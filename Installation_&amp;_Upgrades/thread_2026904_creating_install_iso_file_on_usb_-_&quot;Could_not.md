---
title: "creating install iso file on usb - &quot;Could not read from...&quot;"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by haplorrhine on 2012-07-15
I'm trying to use StartUp Disk Creator to put the ubuntu iso install file onto a flash drive, but the program always stops in the middle and gives me this error message.  :P

"Could not read from /tmp/tmpbMF_wu"

](*,)

I looked at that folder, it has the lock symbol on it.  It tells me "You are not the owner, so you cannot change the permissions."  :o  I tried "sudo chown me.me -R /tmp/tmpbMF_wu"  The command was followed by a lot of text about it changing the ownership of all the files in that folder, but the folder still tells me the same thing in its permissions tab.  :mad:

:frown:

I could give the other usb-creator program a shot, but it has a lower rating and says "kde" instead of "gtk," whatever that means.  [-o<

This is the help page concerning what I am trying to do.
[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/):-k

\\:D/

---

### Post by nothingspecial on 2012-07-17
*Thread moved to **Installation & Upgrades**.*

---

### Post by haplorrhine on 2012-07-17
I gave the flash drive to my brother and he could do it without problems.

The problem isn't really solved, but I got around it.

---

