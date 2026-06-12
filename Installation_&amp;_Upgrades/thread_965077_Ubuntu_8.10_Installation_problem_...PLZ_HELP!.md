---
title: "Ubuntu 8.10 Installation problem ...PLZ HELP!"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by 4uvak91 on 2008-10-31
Hello,

I just made dualboot on my new computer. I have Win Xp and i installed ubuntu in a same HDD but on new partition. the problem is that the boot menu won't appear...and i didn't find any settings in my BIOS everything looks like OK... ( i have ASUS P5Q PRO motherboard). So what I need to do??

PS. I have installed ubuntu befero and never get any that kind problems.

---

### Post by 4uvak91 on 2008-10-31
answer plz!

---

### Post by LegoAddict on 2008-10-31
Check and make sure the partition is turned to boot?

To do this, boot up via the Ubuntu Live CD and go to the Partition Editor.  I don't have it in front of me so I couldn't tell you exactly what to do but it's under some right-click menus or something.

Sorry not to be of much help.

---

### Post by 4uvak91 on 2008-10-31
well i made ext2 partition i chose /...do ineed to chose /boot??

---

### Post by rbanavara on 2008-10-31
Seems like GRUB boot loader was not installed.

A fast & easy (but may not be elegant) solution would be to install GRUB again on your first HDD.

google search returned this thread:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by 4uvak91 on 2008-10-31
i put the boot mark on Ubuntu it didn't boot...somekind system error...

---

### Post by Dumdideldum on 2008-10-31
Looks like a missed grub install. If possible, reinstall Ubuntu over the last installation and be sure to install grub into the mbr - maybe the repair function of the CD could help you too.

---

