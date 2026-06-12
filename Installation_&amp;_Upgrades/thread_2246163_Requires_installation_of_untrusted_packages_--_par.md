---
title: "Requires installation of untrusted packages -- partial solution"
date: 2014-09-28
forum: Installation &amp; Upgrades
---

### Post by hfinger on 2014-09-28
I have posted this message because there are a large number of posts revolving around this alert dialogue. In my case, the Software Updater (14.04) popped up with a large number of updates. But when I tried to apply them the **Requires installation of untrusted packages **alert appeared. The alert directed me to the Ubuntu Software Centre's tab, but how to identify which packages are causing the problem?

If you are not a command-line Terminal geek, try downloading and installing the Synaptic package manager.

[LIST=1]
[*]Launch Synaptic.  Allow it to update the cache of software lists.
[*]Click the **Mark All Upgrades** button.
If there are any dodgy packages, a dialogue will open and list them.
[*]Check the packages; they are probably all quite harmless and may be there because you download a tar package or a .deb archive from outside of a repository.
[/LIST]

If you search on this error message you will find suggestions for solving many of its other causes, such as out-of-date repositories, etc.

---

