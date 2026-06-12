---
title: "Installing XP from Ubuntu, backing up Ubuntu help"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by timepanda on 2008-05-16
Hello everyone,

I currently have Hardy 8.04 installed on my laptop and I want to install XP in a seperate partition. I have set a dual boot system before, but only when XP was the initial OS. Can anyone give me any tips/threads/warnings on how to do this correctly? Specifically:

-how to correctly install XP from Ubuntu Hardy.
-how to make a backup of my current Ubuntu setup incase anything goes wrong with the XP installation.
-how to use that backup if needed.

Thank you so much for your time, and verbose explanations are appreciated, but I'll take anything I can get! Thanks!

---

### Post by dmj99 on 2008-05-16
A few thoughts.  I would recommend creating a grub boot floppy first.  It may come in handy.  You can find a number of sites that explain how to do this.  You will install XP on the partition of your choice by booting from the XP CD.  The installation of windows XP will, in all likelihood, overwrite the MBR of your hard drive.  This will mean that you will need to reinstall grub on your hard drive for a dual boot.

---

### Post by timepanda on 2008-05-16
> **dmj99 said:**
> A few thoughts.  I would recommend creating a grub boot floppy first.  It may come in handy.  You can find a number of sites that explain how to do this.  You will install XP on the partition of your choice by booting from the XP CD.  The installation of windows XP will, in all likelihood, overwrite the MBR of your hard drive.  This will mean that you will need to reinstall grub on your hard drive for a dual boot.


Forgive me, I'm still learning about how linux works. Please correct me if Im wrong. If I install XP correctly to a partition, then reboot, the system will probably recognize the XP in the master boot record, rather than Ubuntu. Having a grub boot floppy will help me reset the mbr to Ubuntu. Then I would go into Ubuntu and do what to add XP to the boot options...Am I following this correctly or am I way off? Thanks for your time, it's greatly appreciated! :)

---

### Post by zvacet on 2008-05-16
> Then I would go into Ubuntu and do what to add XP to the boot options

You will type in terminal 

```
sudo fdisk -l
```

to find out on which partition is XP.Then 

```
gksudo gedit /boot/grub/menu.lst
```

and find this line 

### END DEBIAN AUTOMAGIC KERNELS LIST

below that line add 

title       Windows XP
rootnoverify (hd?,?)
chainloader +1

**(hd?,?)** = correct partition on which XP is.You will see that from **fdisk -l** command.For example if after runing **sudo fdisk -l ** you see your XP partition as hda2 then (hd?,?)= (hd0,1)

---

### Post by timepanda on 2008-05-16
Wonderful, thank you all for the posts so far!

Now, are there any reccomendations for the best way to actually go about partitioning and installing XP? And making a backup of Ubuntu in case of emergency?


Thanks again.

---

### Post by zvacet on 2008-05-16
If you don´t have free space or you don´t have it enough shrink your Ubuntu partition with [Gparted live CD]("http://gparted.sourceforge.net/") and make new partition and format it as NTFS.On that partition you will install windows.For backup look [here.]("https://help.ubuntu.com/community/BackupYourSystem")

---

