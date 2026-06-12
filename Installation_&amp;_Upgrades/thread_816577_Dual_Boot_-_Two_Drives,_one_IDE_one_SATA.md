---
title: "Dual Boot - Two Drives, one IDE one SATA"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by soritong on 2008-06-02
I'm currently thinking about adding Ubuntu as a secondary operating system to my computer.

I currently have one small IDE drive that is housing Vista with a few smaller apps, and a larger SATA drives that holds music, movies, games, and important apps.

If I were to install Ubuntu, how difficult would it be to have it placed on the SATA drive, and have GRUB realize that there is one OS on the IDE, and one on the SATA?

---

### Post by Pumalite on 2008-06-02
How large is your IDE drive and how much space do you have left?

---

### Post by fsmithred on 2008-06-02
I don't think GRUB cares whether you have IDE or SATA. It just looks at which one is first and which is second. Sounds like IDE is first, which is what I'd expect. 

You'll need at least two partitions on the sata drive for linux - one for / and one for swap. Put the grub boot loader in the mbr of the first drive, and it should find all your operating systems and make entries for them in the boot list. If not, it's easy enough to add an entry. 

If you ever pull the IDE drive, you'll need to install the boot loader into the mbr of the sata drive and make a few minor edits in fstab and menu.lst.

---

### Post by Pumalite on 2008-06-02
I don't think the issue is so simple:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)
[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/213639)

In my case I'd prefer to install both OS's in the IDE and leave the SATA for storage. You could have your /home for Ubuntu there.

---

### Post by meierfra. on 2008-06-03
A mix of Sata and IDE can lead to grub problem.   But there are various ways to deal with these problems:

If you don't mind overwriting the MBR of the IDE drive:

1)  Follow pumalite's suggestion and install   Ubuntu on the IDE drive.

or

2) Install Ubuntu on the sata drive with both drives attached.

If you prefer to leave the MBR of the IDE drive intact:

3)  Unplug the IDE drive while installing Ubuntu onto the Sata drive.  You  will have  to manually add  a  Vista item  to the file "menu.lst". 

or 

4)   Install Ubuntu on the sata drive with both drives attached. In step seven of the installation click on "advanced"  and  install the bootloader on the SATA drive.  After  the installation is finished and before you reboot into ubuntu, you need to edit menu.lst.  (changing all (hd1,?) to (hd0,?) and vice versa)


In case 1) and 2) you will be booting of the IDE drive, and you shouldn't  have any Grub problems.

In case 3) and 4) you will be booting of the SATA drive and  a little bit editing "menu.lst" is required to make this work. But it avoids later Grub problems: If  you need to reinstall Vista, you won't  have to fix Grub. And if you delete Ubuntu, you won't have to fix the MBR of the IDE drive.

---

### Post by soritong on 2008-06-03
Thanks everyone for your help.

Looking through some of the posted links I guess I'll just have to cut the fat from my IDE drive and install on there, at least for ease.

---

### Post by meierfra. on 2008-06-03
Method 2 is just as easy as Method 1, and it also avoids the grub problems.

---

