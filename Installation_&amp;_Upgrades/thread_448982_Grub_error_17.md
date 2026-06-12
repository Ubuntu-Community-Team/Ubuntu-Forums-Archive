---
title: "Grub error 17"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by cmg45 on 2007-05-19
I'm incredibly new to linux and im trying to dual boot with windows vista but every time i install both operating systems niether of them ever boot up again.

i install windows on one raid 0 hard drive (well 2 but you know that) and ubuntu on my other 500 gig hard drive and always get a grub error 17 message and neither of them boot then i re install windows and start again.


Any one want to tell me how to go about doing this so i can run both systems, im trying to get into this whole linux reveloution but i love my games and just am not willing to make the windows sacrafice yet.

any help would be greatly apreciated.

---

### Post by phidia on 2007-05-19
Are you using the live/desktop cd to do the install? Which version of ubuntu are you using?
You can check the link in my sig for community documentation on setting up grub.
Also there are specifics here [https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed](https://help.ubuntu.com/community/Installation#head-86a18ab57715d9bb5f0dfaba497a928e67cd73ed) for installing to raid.

---

### Post by vtel57 on 2007-05-19
We'll need a little info from you...

You have two drives on RAID 0, right? With Windows installing there? And you have another drive (IDE, I'm assuming) and trying to install Ubuntu there. Right, so far?

Install your Windows on your RAID array first. Boot to it. Make sure all is well.

Now, install your Ubuntu on your IDE drive, making **SURE** that the GRUB bootloader is written to the master boot record of the **SAME** drive where you are installing Ubuntu.

Set your BIOS settings so that the IDE (Ubuntu) drive is the primary bootable drive. Reboot. GRUB will automatically add an entry for your Windows installation in the menu. You can either boot Ubuntu or, by moving down the menu with the down arrow key, boot Windows.

It will look something like this:

[img]http://tinypic.com/iyoj7s.gif[/img]

---

### Post by Ub1476 on 2007-05-19
Follow this guide: [Linky]("http://www.apcstart.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first") 
Good luck:)

---

