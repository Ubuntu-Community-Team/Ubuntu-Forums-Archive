---
title: "Dual boot Ubuntu/Kubuntu ?"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Wehrmacht on 2008-05-22
I have an upgraded Ubuntu 8.04 install on 20% of my drive, and kubuntu8.04 on the remainer.  The recent install of Kubuntu has taken over grub, and my boot partition for Ubuntu is now gone.  

I do get some lame option in grub each boot whether I want safe mode or Kubuntu... but no choice for Ubuntu-Kubuntu.

:confused:

kind of a recent noob.  Really had my Ubuntu copy fine tuned the way i liked it.. now I can't even figure out how to access it.

---

### Post by abn91c on 2008-05-22
> **Wehrmacht said:**
> I have an upgraded Ubuntu 8.04 install on 20% of my drive, and kubuntu8.04 on the remainer.  The recent install of Kubuntu has taken over grub, and my boot partition for Ubuntu is now gone.  

I do get some lame option in grub each boot whether I want safe mode or Kubuntu... but no choice for Ubuntu-Kubuntu.

:confused:

kind of a recent noob.  Really had my Ubuntu copy fine tuned the way i liked it.. now I can't even figure out how to access it.

ubuntu is not gone, when you logout you will see it if you click on sessions on the log in screen

---

### Post by Wehrmacht on 2008-05-22
Hmmm I see only " Default , KDE4, and shutdown... "  KDE4 is also started when you try default.

I know Ubuntu is still there, I can access my old Home folder and all my old data on a new partition drive.. 

here is my boot list :  All of those options start KDE4
```



title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=587c6025-3557-4d9c-a54f-0372fb9b03af ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=587c6025-3557-4d9c-a54f-0372fb9b03af ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

```

---

### Post by Wehrmacht on 2008-05-22
sudo fdisk -l yields:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00097da4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         115      923706   83  Linux
/dev/sda2             116       30401   243272295    5  Extended
/dev/sda5             116        8776    69569451   83  Linux
/dev/sda6           30267       30401     1084356   82  Linux swap / Solaris
/dev/sda7            8777       29510   166545823+  83  Linux
/dev/sda8           29511       30266     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order
chris@lianli:~$

---

### Post by confused57 on 2008-05-22
You can reinstall Hardy's grub, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

I don't know how your disk was partitioned before you installed Kubuntu, but if you had other partitions mounted in Hardy's /etc/fstab using UUID that were reformatted when you installed Kubuntu, you would receive an error when trying to boot Hardy that the UUID couldn't be found.  This explains a little about fstab & UUID:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

If you do receive the missing UUID error when you boot into Hardy, you can mount your Hardy root partition, using the Ubuntu live cd & comment out(place a # in front of the  line with the mountpoint) the entry for now:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

If you didn't have any other partitions mounted in your Hardy's fstab that were reformatted when you installed Kubuntu, you shouldn't have any problem booting Hardy.

---

### Post by abn91c on 2008-05-23
not sure what happened then but you can do sudo aptitude reinstall ubuntu-desktop, if asked what default GUI you want to start by default select GDM

---

### Post by Wehrmacht on 2008-05-23
Ok... it looks like the "boot" folder in my old Ubuntu install has been wiped out... and now the only thing with any info in it is the boot folder in the new install of Kubuntu.

grub>
      find /boot/grub/stage1
 (hd0,6)

theres the location of kubuntu's grub.

What can I fill the old Ubuntu's 'boot' folder with to make it also bootable, and how do I map it into grub to be given the choice?  

Just tinkering here... like to know how to do these things... I'll eventually make a choice and have just one large partition.

thanks!

Chris

---

### Post by meierfra. on 2008-05-23
It looks like to me that sda1 is a /boot partition.  What's the output of

```
sudo grub
find /grub/stage1
```

If this returns (hd0,0), try

```

root (hd0,0)
setup (hd0)
quit

```

---

