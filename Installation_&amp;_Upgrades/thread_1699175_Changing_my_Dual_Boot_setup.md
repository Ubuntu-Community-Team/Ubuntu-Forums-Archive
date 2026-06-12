---
title: "Changing my Dual Boot setup"
date: 2011-03-03
forum: Installation &amp; Upgrades
---

### Post by Notac on 2011-03-03
I currently have xp installed on the 1st partition and Ubuntu installed on the 2nd.
Both partitions are on the same drive.(Being the 1st drive)

I have just purchased a new case and some other components and wish to take the opportunity to change my current setup so that xp is on the 1st drive (alone) and Ubuntu on the 2nd drive (alone)

Can anyone let me know if the following will work

Using clonezilla, I take a backup of each partition separately.
I then copy back the xp partition to the 1st disk.
I then copy back the Ubuntu partition to the 2nd disk.

I gather at his point i run the live Ubuntu cd, open a terminal and run sudo update-grub.

Is there anything else I need to do as I am still quite new to linux.

All help is appreciated

---

### Post by Quackers on 2011-03-03
I believe that this would not be enough. Grub is presumably installed to sda at the moment and looking for boot files on sda, whereas after doing the above, the boot files would be on sdb.
If you do it as above I would recommend that you run fixmbr from the Windows repair disc and make Windows bootable on the first drive. When Windows is booting ok you can change the bios to boot from the second hard drive before the first hard drive, then boot from the Ubuntu live cd.
I would suggest that you then purge/re-install grub to sdb (not sda) using the "Why chroot" section of the guide below (after identifying the Ubuntu root partition, and confirming the drive designation).

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Notac on 2011-03-03
Thanks for the reply Quackers :)

Will have a crack following the thread you mentioned or do you know of an easy way of changing a single disk dual boot to a 2 disk dual boot?

Thanks again Quackers

---

