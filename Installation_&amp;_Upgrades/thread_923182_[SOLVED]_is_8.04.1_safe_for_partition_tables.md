---
title: "[SOLVED] is 8.04.1 safe for partition tables ?"
date: 2008-09-18
forum: Installation &amp; Upgrades
---

### Post by james2b on 2008-09-18
I had found out that when Ubuntu 8.04 first released, that when it installs it deletes the partition table, instead of updating it. So does anyone know about that as a bug fix yet, since some people had dual boot with XP systems become un-bootable due to that 8.04?

---

### Post by Sef on 2008-09-18
> I had found out that when Ubuntu 8.04 first released, that when it installs it deletes the partition table, instead of updating it. So does anyone know about that as a bug fix yet, since some people had dual boot with XP systems become un-bootable due to that 8.04?

If you manually partition you will not have that problem.  Some people click on use the entire disk.  That will erase the XP partition.  

There are more problems with updating to the next version than with installing by cd.

---

### Post by james2b on 2008-09-18
It is not from the Ubuntu partitioning, as I did select the option for custom or manual partitions. What is the real cause is the GRUB boot loader installation onto the master boot record, which writes the boot code over top of the windows code, and clears the data in the partition table. What is should do is just update the partition information there, which is what the older Ubuntu versions did, ( 7.04 and 7.10 ) I had found a forum post from back on 6-4-08 from a Apple Mac user in Ubuntu archives. So a search of the Linux forums should find this issue.

---

### Post by NoWayBill on 2008-09-18
I have done many installs on single, dual and multi-boot systems and have never had a problem.

---

### Post by Herman on 2008-09-18
> It is not from the Ubuntu partitioning, as I did select the option for custom or manual partitions. What is the real cause is the GRUB boot loader installation onto the master boot record, which writes the boot code over top of the windows code, and clears the data in the partition table. What is should do is just update the partition information there, which is what the older Ubuntu versions did, ( 7.04 and 7.10 ) I had found a forum post from back on 6-4-08 from a Apple Mac user in Ubuntu archives. So a search of the Linux forums should find this issue.:) Of course GRUB is safe for partition tables!

That is, if you have an IBM  PC.

Apple computers are quite a lot different from the IBM PCs that almost all of us use, and which you would install GRUB to MBR in. I don't know very much about Apple Mac computers, but I believe they have an 'EFI' instead of a MBR, and you need something called 'boot camp' if you want to set up a dual boot in one.

Apple users have their own special section in Ubuntu Web Forums here it is, [Apple Users]("http://ubuntuforums.org/forumdisplay.php?f=328").
Here is the first sticky in that forum,  [Apple Intel Users FAQ]("http://ubuntuforums.org/showthread.php?t=493393") and if you read [post #2]("http://ubuntuforums.org/showpost.php?p=3668918&postcount=2"), you'll find the bug you're probably referring to.
> After installing Ubuntu Hardy 8.04, you may get a 'no bootable devices' error **after choosing Ubuntu with rEFIt**., or no other operating systems show up at all when holding the Option key on startup. There is a bug in the installer that wipes out information about your partitions in the MBR.** This data is required in order to boot what Apple calls "legacy" operating systems** (meaning linux, windows).:) This bug only applies to Macs, not to the regular kind of computers that most people here would be using.

Are you thinking of installing Ubuntu in a Mac? 

Or is your computer a PC?

Regards, Herman :)

---

### Post by james2b on 2008-10-05
I have now installed the new version of Ubuntu on a PC multi-boot with XP, SUSE, and Fedora, and it seems to be fine, thanks for the help. The default grub install does not include any splash image, so the grub boot screen was plain, but now I did add this too.

---

### Post by Herman on 2008-10-05
:D 
Certainly, you can have a lot of fun with GRUB and add a nice splashimage, here's the link, [splashimage]("http://users.bigpond.net.au/hermanzone/p15.htm#splash").

That link explains how to install one and gives you further links where you can download one, either one I made or one from other web sites. There's a collection of links there you can look through.
It also shows you how you can make your own if you have a little time and patience.
You can use any image file, it can be a photo or digital art.

Enjoy!

Regards, Herman :D

EDIT:
> I have now installed the new version of Ubuntu on a PC multi-boot with XP, SUSE, and Fedora, and it seems to be fine,Congratulations and well done! :)

---

