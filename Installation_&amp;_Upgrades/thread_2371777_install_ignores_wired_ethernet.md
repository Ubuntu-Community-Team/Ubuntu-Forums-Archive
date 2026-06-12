---
title: "install ignores wired ethernet"
date: 2017-09-18
forum: Installation &amp; Upgrades
---

### Post by yonnie on 2017-09-18
Easier than ever install!  Just did one (OEM) using 16.04.3.  Really impressed!  Put it on an ASUS vivo.
Had a working RJ45 ethernet cable plugged in and the install ignored it, not even an option to choose it.  Install wanted to use only the wifi instead and still did not do the updates.  After install the package manager wouldn't work either.  Had to use the command line to download and install Synaptic.  

So just be aware about what you may need to have handy for post install.

---

### Post by TheFu on 2017-09-19
If you'd like help getting the ethernet working, please post the cmd and output from **sudo lshw -C network**.
Please use "code tags" - Adv Reply (#) to make the output readable.

---

### Post by yonnie on 2017-09-19
thanks, the post was more of a "this is what happened".  I ran into another issue with user account.  I could not get the user account to switch to a different one and there was no mechanism to handle groups.  Switch asked for a password and then would not function when the password was entered.  Just kept indicating the password was invalid.

I gave up and re-installed with the corrected user name.  Apparently, additional users and groups doesn't function the way it should.  Hopefully this will get resolved soon?

---

