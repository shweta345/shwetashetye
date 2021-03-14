+++
title = "Hypothesis - Web annotator in your Browser"
author = "Shweta"
date = "2021-03-14"
tags = ["emoji"]
categories = ["Technical Writing Tools"]
[[images]]
  src = "img/2019/03/pic02.jpg"
  alt = "Desert Scene"
  stretch = "stretchH"
+++

Reviewing documentation is a crucial step for any writing process. You can review your own work and reflect, or sometimes 
reach out to someone who can make this process easier. With an integration of MS office and Adobe Acrobat, you can churn out a decent enough document to send out to the world, but the assumption here would be that everyone has a similar setup. 
If your reviewers are connected to the internet and the documents are available for a review online, Hypothesis can actually make
the process of reviewing and aggregating comments a lot easier. 

Hypothesis is described as follows on the site:
>"Hypothesis is a new effort to implement an old idea: A conversation layer over the entire web that works everywhere, without >needing implementation by any underlying site."

It is mostly marketed for a learning environment and as a collaboration tool. From a technical writing perspective, we do review and engage collaboratively with diverse set of stakeholders. Though the scope isn't specifically learning or it is (maybe), the scope definitely is to transparently review, engage, and collaborate. 

Reading through the features, I thought of testing it out on two setups. 

- Firstly, using the Chrome extension
- Secondly, integrating it as part of the Hugo site setup

## Installing Hyphothesis on Chrome as an extension

Installing the Chrome extension is pretty basic and similar to the process of adding any extension from the browser. Before you go ahead and install the extension, create an account with [Hypothesis](https://web.hypothes.is/). Open the link to download [Hypothesis](https://chrome.google.com/webstore/detail/hypothesis-web-pdf-annota/bjfhmglciegochdpefhhlphglcehbmek). Click **Add to Chrome**, and then click **Add Extension**. 

## Installing Hyphothesis on Hugo site setup

This website is build using Hugo with a repo in GitHub and CI managed by Netlify. The setup is basic and minimal to get the job done. That the site is created with Hugo, has nothing to do with installing Hyphothesis on this setup. I wanted to test integration of Hypothesis on any server and the steps I followed are from the [Hypothesis](https://h.readthedocs.io/projects/client/en/latest/publishers/) documentation.

Since I am using Hugo, my content pages use the `theme/layout/_default/single.html` template. I wanted to include the annotator on the right hand side of my page whenever someone lands on any blog article. 

**To enable the extension:**

1. Identify the template that your content pages use. In my case, the template was `theme/layout/_default/single.html`.
2. Edit the file to add the following code at the bottom of the template file, inside the `main` block.
   ```
   <script type="application/json" class="js-hypothesis-config">
        {
          "openSidebar": true
        }
   </script>
   <script async src="https://hypothes.is/embed.js"></script>
   ```
3. Save the file.
4. Commit your changes and redeploy the site.

---
**Note:** The Hyphothesis documentation provides more information about changing properties of how the extension must appear when used.

---

In both the install cases, the Hypothesis extension (sidebar) appears as follows:

![hypothesis](/img/main/hypothesis.png)

After you add a comment, you do have an option to again share it with someone or just keep it to yourself. Let us add a test comment and see where it takes us. 

![hypothesis editing](/img/main/hypothesis1.png)

Assuming the entire review cycle is complete, let us see the Hypothesis dashboard and what we can do using it.

![hypothesis working](/img/main/hypothesis2.png)

It does give me a view of the comments alongwith the specific page where the comment was made. It also, again, lets you share the comments with multiple users. 

To sum up, for collaboration I find Hypothesis useful, as long as the content is out in the public space. I am yet to research how offline systems can integrate Hypothesis, and maybe that can be part 2. If you want to make a decision, take a look at the pros and cons.

Pros:

- Hypothesis is truly collaborative way to edit with minimal integration steps
- Lets not forget - it's Free!
- Highly scores on shareability and ease of use
- Free version lets you create private groups too

Cons:

- Option to export to an offline file from the UI is missing. There is a [prototype tool](https://jonudell.info/h/facet/?max=50) that offers export through Hypothesis API. 

Making a decision to use Hypothesis might require a more collaborative play and trial. Let me know how was your experience using Hypothesis!



