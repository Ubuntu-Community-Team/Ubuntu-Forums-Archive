---
title: "tilda and picard in natty unity"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by johnrunsubntlnx on 2011-05-02
I recently updated my Ubuntu 10.10 to Natty and I'm experiencing some problems getting Tilda and Picard to work/install properly.

I did a clean install and only things I kept a backup of are my personal files.  All other applications and drivers are reinstalled on the fresh Natty installation.



Tilda Problem:

Tilda was easily installed and configured.  It works fine on first show (first time F12 is pressed) but any other calls after that would only show a grey box on the spot where Tilda is supposed to be.  Best way to describe I think is Tilda looks like it's showing up with compositing disabled, kinda like how AWN or other transparent apps would show if compositing is disabled.   This was then my first guess as to what might have caused the problem, but compositing is indeed enabled.  My nvidia gpu is installed and configured correctly and no other applications are having compositing problems.



Picard problem:

I tried installing it through "sudo apt-get install picard" but I'm getting a missing dependency error.  Same error when using Synaptic or Software Center.  Missing dependency is called "python-qt4" and installing it manually would also give me this same error.  I did check for broken dependencies and updated my apt cache and stuff but they don't seem to help.  I also installed numerous other applications after this so I'm guessing my apt is not messed up.  I'm wondering if the picard package (or one of its dependencies is broken in the repo)




Any one else experience these?  Thanks guys

---

### Post by subzero2000 on 2011-05-10
With regards to your tilda issue, it sounds like you are getting bitten by this bug - [https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175) . The most reliable fix I've found is to disable the Animated Pulldown on the Appearances Preferences tab. I'm running Natty 64 bit, and just confirmed it is still an issue.

---

### Post by johnrunsubntlnx on 2011-05-15
> **subzero2000 said:**
> With regards to your tilda issue, it sounds like you are getting bitten by this bug - [https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/144175) . The most reliable fix I've found is to disable the Animated Pulldown on the Appearances Preferences tab. I'm running Natty 64 bit, and just confirmed it is still an issue.

that sounds like the one I'm having.  thanks I'll give that a try

---

