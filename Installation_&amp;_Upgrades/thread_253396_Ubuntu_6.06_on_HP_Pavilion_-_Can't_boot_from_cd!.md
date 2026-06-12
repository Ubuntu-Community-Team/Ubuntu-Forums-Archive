---
title: "Ubuntu 6.06 on HP Pavilion - Can't boot from cd!"
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by Henke on 2006-09-08
Hi!

I'm helping a friend with his HP-Laptop, and now we are in some serious troubles... At first, when the machine was new, we installed Ubuntu 6.06, and it installed, and worked just perfect. After that, he wanted to install Windows XP and do a second Ubuntu-install after that, so he could dual-boot. But something went seriously wrong with the XP-thing. The XP-installer was (is) unable to copy all the files in a proper way. And now, when I'm trying to get Ubuntu back on the machine, I can't even boot from the cd. The machine says Ok booting the kernel, but then I get:

PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(1,0)

](*,) 

How do I give this machine its life back? There isn't anything on the drive that we want to keep. If there is a way to reset the whole thing I would appreciate your help with that very much... But that You have already understand, I think! ;) 

Regards
Henke

---

### Post by andlinux21 on 2006-09-08
I am sure you checked the Bios to make sure the settings were correct is there anyway you can do a recovery.  Most of the new laptops have a seperate partition with recovery info on it. :confused:

---

### Post by wpshooter on 2006-09-08
Use this program to wipe the drive clean and then install XP first and then install Ubuntu.  But my preference would be to have either XP on the machine or Ubuntu on the machine and not both.  IMO, having both on the same machine is just asking for problems.

[http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by Henke on 2006-09-08
> **wpshooter said:**
> IMO, having both on the same machine is just asking for problems.

[http://www.killdisk.com/](http://www.killdisk.com/)

Thanx for that tip! I'm running it now, and it seems like the program is doing a great job. 23% progress for the moment... 
Then its up to my friend to decide what system he should use. I will try to convince him to install Ubuntu again. I love Linux - and the whole OpenSource thing! Microsoft is just embarrassing... :cool: 

Henke

---

### Post by Henke on 2006-09-08
Now I've killed the disk, but ther's no difference in the computers behaviour... However, when Killdisk starts it says:

-InitDiskillegal partition table - drive 00 sector 0
illegal partition table - drive 00 sector 0
illegal partition table - drive 00 sector 0
illegal partition table - drive 00 sector 0

And when I enter the programs main window I can see the Hard Disk Drive (80h) with a total size of 55.8 Gb, and a Virtual Drive (00h) named "MATSHITAUJ-840D" version 1.02 with a total size of 1023 Mb (I tried to kill that one too, but it failed). There must be some GigaBytes lost here I think... The drives total size is (was) 80 Gb...

Any suggestions?
Henke

---

### Post by wpshooter on 2006-09-08
If your drive is 80gb just put it on the line that says 80gb, I think it will probably be the first listing in the tree.

When you get thru with WIPE and you esc out of the program and back to the DOS prompt just take the CD and any floppies out of your drive and then reboot and it should NOT reboot because it will not be able to find a valid O/S.

Then put what ever O/S (Ubuntu) CD in the drive you want and it should boot to it.  Make sure you run the CD integrity verification on your Ubuntu CD.

Good luck.

---

