---
title: "Error 21"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by puner on 2008-04-24
Hey guys, 

Here is my current setup

[[IMG]http://imagenerd.com/thumbnails/th_screenshot--dev-sdb---gpartedZqms.png[/IMG]](http://imagenerd.com/show.php?_img=screenshot--dev-sdb---gpartedZqms.png)

I installed and rebooted. Ended up with Error 21. Like every other time I give another go at linux.

---

### Post by puner on 2008-04-24
bump

---

### Post by Herman on 2008-04-25
Here's a link containing the GNU/GRUB manual's interpretation of it plus some information I've collected on that error message, [Grub error 21]("http://users.bigpond.net.au/hermanzone/p15.htm#21").

If you have IDE and SATA drives together, you might just need to edit your /boot/grub/menu.lst file with the correct hard disk number.
This link should help you access your hard disk installed Ubuntu's vital files from the Ubuntu Live CD, [Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") .

If you have IDE hard disks, make sure they are plugged in an jumpered correctly for the type of IDE cables you use. Even the CD/DVD drive needs to have the jumpers set correctly as well.

If you need specific help, please post a copy of the bottom half of your /boot/grub/menu.lst file.

Regards, Herman :)

---

