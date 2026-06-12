---
title: "Bootingissue after upgrading to 10.10"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by srinathduraisamy on 2010-10-22
Hi, I was using ubuntu 10.04 installed under windows, so it was using windows boot loader.

Now I upgraded my ubuntu to 10.10 it asked for some grub installation and i did something now my either windows boot loader or neither grub is working.

How can I restore both the windows as well as my ubuntu.

Will the normal grub recovery procedure will work.

Any suggestions will be realy helpful.

---

### Post by sikander3786 on 2010-10-22
You can reinstall Grub as mentioned here.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

However, it would be better to post the output of bootinfoscript and then let us guide you there.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Please wrap the output with proper code tags #.

---

### Post by srinathduraisamy on 2010-10-22
Thanks I solved the problem.

I used a live cd and booted into it.

Then I installed lilo
 sudo apt-get install lilo
 sudo lilo /dev/sda mbr

It works fine. thanks.

---

