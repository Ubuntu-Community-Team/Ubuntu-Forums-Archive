---
title: "[SOLVED] Install with XP boot first"
date: 2007-12-06
forum: Installation &amp; Upgrades
---

### Post by gasport on 2007-12-06
I am sure this has been asked before, but search is not getting me the answer I need.

I installed Ubuntu on a separate drive and naturally, the boot loader listed Ubuntu first and XP last.   I would like to install with XP first in the list.

Is there an easy way to install Ubuntu and have it configured so that XP boots first?   I know there are ways to do this through manipulation of the boot file, but I would prefer a simpler way, such as a choice when the program installs.

I had to reformat that drive as I had some problems with XP and did a reinstall.  So, I am basically starting from scratch with the installation going on a second hard drive.

Thanks.

---

### Post by Pumalite on 2007-12-06
You can edit  /boot/grub/menu.lst when you finished your installation. Ideally one installs XP first and Ubuntu last.

---

### Post by MQMike on 2007-12-06
Yes:

How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
---  HOW To:  Change the Default Operating System (Also:  Changing the timeout, boot menu, and other tips)  Reply #1

---

### Post by gasport on 2007-12-06
Thanks Pumalite

I did install XP first.  I would install Ubuntu second.  I have not used Ubuntu before so how does one edit the menu.lst

Is this a command line statement or is there an edit option somewhere in the actual program?

---

### Post by MQMike on 2007-12-06
The How-To I gave you explains it, and more.   :)

---

### Post by Pumalite on 2007-12-06
Backup first.
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.back
gksudo gedit /boot/grub/menu.lst
Post your menu.lst if you need help when you are ready.

---

### Post by gasport on 2007-12-07
Thanks everyone.   

I should be able to master this.  If not it is time to quit....


I will mark the post as resolved.

---

