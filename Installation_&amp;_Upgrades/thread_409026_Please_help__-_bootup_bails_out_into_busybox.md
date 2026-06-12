---
title: "Please help  - bootup bails out into busybox"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by agger on 2007-04-14
I'm running Xubuntu 6.10 on an old x86.

Until a few days ago, I also had the Gnome desktop installed. However, to save space, I removed Gnome and installed Fluxbox, ensuring afterwards that Xubuntu was intact by doing a 

apt-get install xubuntu-desktop

Upon reboot, though, Ubuntu bails out into a busybox shell. 

The last things in the boot log are "Target filesystem doesn't have sbin/init".

I checked, and the hard disk is absolutely okay with all files intact. But the directory /sbin really doesn't have a file named init.

HEEEELP :-) - what do I do?

Thanks in advance for any response.

---

### Post by agger on 2007-04-14
Hmmm, I may have solved the problem myself.

First of all, I found this old thread on a similar problem:

[http://ubuntuforums.org/showthread.php?t=223773](http://ubuntuforums.org/showthread.php?t=223773)

However, this isn't what I really did - what I did was to copy the /sbin/init from the other Linux distribution on my HD into Ubuntu's /sbin/, and now it worked! The upgrade must have thown away my old one :-| 

Now I'll do a new "apt-get upgrade" to hopefully get an "official " version.

---

