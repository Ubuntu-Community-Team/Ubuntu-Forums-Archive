---
title: "Dual boot system - Upgraded to Win 8 Pro - Ubuntu boots fine - Win 8 will not boot"
date: 2013-01-28
forum: Installation &amp; Upgrades
---

### Post by lerasch on 2013-01-28
I have a Windows 7 / Ubuntu 12.04 64 bit dual boot system on a ZT Affinity desktop with an Asus motherboard.  I had Windows 7 Home Premium on the primary hard drive and Ubuntu 12.04 on the second internal hard drive.  System had no problems for the past 7 months.  I took advantage of the $14.99 upgrade to Windows 8 Pro.  I upgraded but now I can not boot into Windows 8 Pro.  I can boot fine into Ubuntu 12.04.  I did not uninstall Ubuntu before doing the upgrade.  I just did the online download of Windows 8 Pro and then ran the upgrade program.  The program ran, installed Windows 8 Pro, rebooted itself a couple of times but now can not boot.  When I start up the computer I get choices for booting into the current version of Ubuntu, an older version of Ubuntu, the Memory tests and Windows 7.  I no longer have Windows 7, since I performed the upgrade, but its my only choice for booting a Windows program.  I select it but only get an error message from Windows Boot Manager that says Windows failed to start.  I'm not all that experienced with computers.  Do I need to modify the Grub or do I need to start over with the upgrade?

---

### Post by furything on 2013-01-28
Try regenerating grub menu from linux install to be safe
```
sudo update-grub
```or```
sudo update-grub2
```Makes no difference as one is symbolic link to the other. 

If still does not boot then you can try using win 7 repair to do a console recovery.
In the console recovery```
FixMBR
```This will overwrite grub but let you see if the issue is with windows installation or if windows 8 does not like a non MS master boot record. Have not tried 8 yet so do not know if an issue exists.

If you overwrite MBR then you could reinstall windows making sure it works.

Once windows is working ok then restore grub boot loader to get at linux - use the live cd and the grub repair mechanism see
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Just seen another post and they have done exactly what you have been trying to do by the sounds of it with grub loader.

Looks like something went wrong with your windows upgrade

---

### Post by Mark Phelps on 2013-01-28
First thing to do is disconnect the Ubuntu drive from your PC.  

Then, see if you can boot from only the Win8 drive. IF it works, that means there's a problem with GRUB and the update-grub may fix that.

If it does not boot, you will have to fix the Win8 boot. Unfortunately, without disk media, I know of no convenient way to do that.

---

### Post by oldfred on 2013-01-28
Beans: 10,000
Congradulations to Mark Phelps. :popcorn:

You may be able to get into a Windows repair console. Easier if booting Windows directly, but some say it works from grub but is very fast, or you have to hit f8 (?) at almost the same time.

---

### Post by lerasch on 2013-01-29
Thank you all for the responses. I disconnected the drive with Ubuntu on it and rebooted the computer.  Same windows error message came up and Win 8 Pro would not boot up.  I will try to reload Win 8.

---

### Post by Mark Phelps on 2013-01-30
> **lerasch said:**
> Thank you all for the responses. I disconnected the drive with Ubuntu on it and rebooted the computer.  Same windows error message came up and Win 8 Pro would not boot up.  I will try to reload Win 8.

BEFORE you go to all that trouble, I suggest you go to the Win8 forums (eightforums.com) and look through their installation tutorials.  There may be a way to do a clean reinstall without losing anything.

---

### Post by lerasch on 2013-02-23
Problem Resolved - I received Win 8 disk media, used it to correct the Win 8 Pro install problem, connected the 2nd internal HDD back up, ran boot-repair, and now everything works fine.  I think if I was not in such a rush and had just temporarily disconnected the HDD with Ubuntu there would not have been any problem installing Win 8.  Thank you all for your time and advice on what to do once I got Win 8 installed properly.

---

