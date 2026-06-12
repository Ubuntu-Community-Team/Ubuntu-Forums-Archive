---
title: "only have wireless conection"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by Xbehave on 2008-01-31
i live in a flat the landlord only offers wireless, Ive messed up my gutsy install and need to reinstall my system with an alternate CD

    * i have a wired connection at uni but its quite hard to get running as i need to install cisco VPN to get out bound access, which is to say the least a pain. (tried connecting wirelessly today and it just wasnt working . )
    * i have ndiswrapper and bcm43xx working with no problems
    * ive got patched drivers but if its too hard to copy them over then it doesn't matter

what files should i save on a memory pen to be able to get my system working?

---

### Post by linuxmagick on 2008-02-10
Since you're familiar with setting up ndiswrapper, I would just make sure to have the wireless drivers available after the reinstall.  For my Broadcom wireless card the files are bcmwl5a.inf and bcmwl5.sys (may be different names for you).  The Ubuntu CD should have ndiswrapper-utils on it, you'll just need to make sure that Synaptic is setup to check the CD in addition to any other repos, which it is by default, I believe.  Once you have that up and running you should be able to connect to the ol' Interweb to install any programs and updates that you need.

---

