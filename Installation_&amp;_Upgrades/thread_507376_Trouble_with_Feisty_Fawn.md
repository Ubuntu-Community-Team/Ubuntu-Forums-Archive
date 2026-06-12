---
title: "Trouble with Feisty Fawn"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by Tootiecat on 2007-07-22
I can't boot from the Ubuntu 7.04 disk, but I can veiw it in XP.  I was trying setting the cd drive as the only boot device and it can't boot from it; the computer asks for a "System Disk".  I unloaded the image file and put all of those files and folders in it onto an other cd to try it.:confused:

---

### Post by brownknight on 2007-07-22
Hi. So you have now configured your PC to booth from the CD drive? Did you burn the Ubuntu CD as ISO or you just copied the files to your CD?

---

### Post by Tootiecat on 2007-07-23
I've tryed both ways, but I burned it as a data disk.  Should I try burning the disk as an image disk?

---

### Post by Seisen on 2007-07-23
> **Tootiecat said:**
> I've tryed both ways, but I burned it as a data disk.  Should I try burning the disk as an image disk?

Yes that is what you need to do.E]sudo

---

### Post by Tootiecat on 2007-07-23
I burned it as an image disk with irfanrecorder, so now I can boot with it now.  But when it shows the boot screen for Ubuntu i can't do anything because whenever I try anything on the menu Boot Loader says "Can not find kernel:"

---

### Post by Pumalite on 2007-07-23
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Or follow these guide lines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by confused57 on 2007-07-23
> **Tootiecat said:**
> I burned it as an image disk with irfanrecorder, so now I can boot with it now.  But when it shows the boot screen for Ubuntu i can't do anything because whenever I try anything on the menu Boot Loader says "Can not find kernel:"

If I understand correctly, you're not able to boot the desktop live cd.  If this is the case, here is an excellent guide:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Key points:  Make sure to do a md5sum of the downloaded iso, burn it as an image(which you've already learned), and burn at a slow speed(8x or less).  I think there is an option on the initial boot screen to check the cd for errors, you might also want to do this.

---

### Post by Tootiecat on 2007-07-25
Problem Solved.

---

