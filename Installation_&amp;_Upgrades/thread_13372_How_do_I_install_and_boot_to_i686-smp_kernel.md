---
title: "How do I install and boot to i686-smp kernel"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by carlc on 2005-01-31
I want to install and add to my bootloader the i686-smp kernel. My linux IQ is still well below par. I have searched for how to do this but still do not know what to do. Any advice or helpful link would be appreciated.

---

### Post by J. S. Jackson on 2005-01-31
Open a terminal (Applications>System Tools>Terminal) and enter:
sudo apt-get install linux-686-smp
Then enter your **user** password when prompted, etc.

This will install everything you need, and automatically add a new option to the top of Grub's boot menu.

I haven't used that kernel before, since I have a single AMD proc.  But the k7 kernel install went without a hitch.

Have a look [here](http://www.ubuntuforums.org/showthread.php?t=3713) (look at number 9) and [here](http://ubuntuguide.org/).  You should find some very usefull info at both of those links.  :)

---

### Post by carlc on 2005-01-31
It worked!
Thanks for the info and the links!

---

