---
title: "Cant find hard drive"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by penguinrusty on 2008-02-02
Hello,
I've had some expeience with ubuntu before but i am by no means a ubuntu power user. I have eeeXubuntu on my eee pc, but thats about it.  I also installed 7.10 on my mom's laptop, and she really likes it.  I recently built my friend a gaming computer, and he wants Ubuntu on his old desktop, just to try it out.  He isnt very tech savvy, so i offered to do it for him.  his old desktop, a Dell Dimension 4400, had some major issues. He was using it with no virus protection, so installed NOD32 and scanned it over 6 times, but so many files were infected, we decided to build a new computer for him and salvage what data we could.  Originally, I was going to reformat it with XP, but during install, if i tried to boot with the XP disk, it said it couldn't find the had drive.  Its an IDE drive, so there were no drivers for me to put on a floppy and boot XP with, so I booted up into his current, virus-overloaded edition of XP and tried to install it from there, but it would get stuck and told me there was an "i/o device error".  I then recommended that we try Ubuntu, because I didnt feel like hassling with it any further, and the computer didnt matter much to him any more.  So, when I install ubuntu, I boot from the 7.10 disk, and it will start to boot, and then the screen will go black, which was a little weird, but when I press the power button, thte ubunto live desktop comes up.  I hit the install icon, and after the first few steps, it asks me to select the partition that i want to install it on, but the problem is, no partitions are listed.  As I mentioned before, its a Dell Dimension 4400, with a 240gb IDE hard drive. Nothing special. Any ideas?

---

### Post by digital_exhaust on 2008-02-02
It's probably a long shot... but if the drive is that infected, there may a boot sector virus there as well. Try wiping the disk entirely using [dBan]("http://dban.sourceforge.net/") or maybe gdisk... that should wipe *everything* and hopefully that will do the trick for you... 

Good luck...

---

### Post by penguinrusty on 2008-02-02
> **digital_exhaust said:**
> It's probably a long shot... but if the drive is that infected, there may a boot sector virus there as well. Try wiping the disk entirely using [dBan]("http://dban.sourceforge.net/") or maybe gdisk... that should wipe *everything* and hopefully that will do the trick for you... 

Good luck...

Thanks
I tried doing fixboot and fixmbr in the recovery console but still no luck. I'll ttry what you suggested (:

---

### Post by Pumalite on 2008-02-02
After DBanning the drive, use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it. Delete everything left in your hard drive, then make a new large partition of your entire hard drive, format it ext3 if you want. Then install Ubuntu.

---

### Post by penguinrusty on 2008-02-02
> **Pumalite said:**
> After DBanning the drive, use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it. Delete everything left in your hard drive, then make a new large partition of your entire hard drive, format it ext3 if you want. Then install Ubuntu.

Thanks! I already have some experience with gparted, and mb I will try to dual boot linux/XP. We'll see. Thanks for all the help, guys! DBan just finished and I will try in just a second.

---

### Post by penguinrusty on 2008-02-02
ok so I used dBan, and now gparted, ubuntu, and XP setup wont see that i have a hard drive ):

---

### Post by Pumalite on 2008-02-03
What motherboard and chipset do you have? What kind of hard drive IDE or SATA? Go into your BIOS and see that is well configured. I would check cables and connections too. OTOH, your drive might have gone south. Try TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download), and/or rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by penguinrusty on 2008-02-03
> **Pumalite said:**
> What motherboard and chipset do you have? What kind of hard drive IDE or SATA? Go into your BIOS and see that is well configured. I would check cables and connections too. OTOH, your drive might have gone south. Try TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download), and/or rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

Yep, you were right. I replaced the cables and everything, then ran testdisk, and the hard drive is just dead. Thans for the help, guys!

---

