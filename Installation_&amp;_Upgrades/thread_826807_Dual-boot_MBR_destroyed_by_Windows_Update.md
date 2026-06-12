---
title: "Dual-boot MBR destroyed by Windows Update?"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by starfailure on 2008-06-12
I dual boot XP and Kubuntu, with GRUB.

I woke up this morning to find my PC on a lovely "Non-system disk or disk error" message. 
I emptied floppy and cd drives and rebooted to get the same thing.

Later found out my wife said she ran "Windows update: install updates and shut down" the night before.

Can anyone explain why/how a Windows update might cause this?

What steps do I need to take to fix my MBR and get the GRUB boot loader functional?

Thanks much.

---

### Post by dstew on 2008-06-12
It is a little odd, because if Windows puts its own boot loader into the MBR, usually at least Windows will boot.

If you have an Ubuntu Live CD, boot it. Open a terminal window (Applications --> Accessories --> Terminal) and type```
sudo fdisk -l
```That should get you a list of the partitions you have. If it looks like all your partitions are OK, then try to re-install grub (see below). If you have doubts about your partitions, post the fdisk output to the forum.

To re-install grub, start the grub shell program by entering grub on the terminal command line. That gets you the grub command line, with the **grub>** prompt. At the grub prompt, enter this command:```
find /boot/grub/stage2
```It should return a partition name, in grub-speak, like (hd0,1). Your exact number may be different. Whatever it returns use as the argument for a root command:```
root (hd0,1)
```Then, setup grub in the MBR of the first hard drive:```
setup (hd0)
quit
```Shut down the Live CD system, remove the CD, and reboot. Hopefully you will see your grub menu.

---

### Post by starfailure on 2008-06-12
Thanks for the great response.  I'll try to do this when I get home or later tonight.

---

### Post by starfailure on 2008-06-12
Okay, when I use "grub> find /boot/grub/stage2" from the Live CD, I get File Not Found.

---

### Post by dstew on 2008-06-12
Quit grub. Post the output of the command```
sudo fdisk -l
```

---

### Post by starfailure on 2008-06-12
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1081     8683101    7  HPFS/NTFS
/dev/sda2            1082       30401   235512900    f  W95 Ext'd (LBA)
/dev/sda5            1082        8730    61440561    b  W95 FAT32
/dev/sda6            8731       16379    61440561    b  W95 FAT32
/dev/sda7           16380       17653    10233373+   b  W95 FAT32
/dev/sda8           17654       20203    20482843+   b  W95 FAT32
/dev/sda9           20204       25302    40957686    b  W95 FAT32
/dev/sda10          25303       27852    20482843+   b  W95 FAT32
/dev/sda11          27853       30401    20474811    7  HPFS/NTFS

Disk /dev/hda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2198    17655403+   7  HPFS/NTFS
/dev/hda2            2199       12906    86012010    f  W95 Ext'd (LBA)
/dev/hda3           12907       14946    16386300   83  Linux
/dev/hda5            2199        7425    41985846    b  W95 FAT32
/dev/hda6            7426       12651    41977813+   b  W95 FAT32
/dev/hda7           12652       12906     2048256   82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by starfailure on 2008-06-12
Honestly, I can't remember which drive has the XP boot part. on it.
I think it's on the IDE.

---

### Post by louieb on 2008-06-12
When you ran grub from the terminal you need to start grub by using
```
sudo grub
```
otherwise  the find command doesn't work.

destews  advise should work then.

BTW. I have heard that XP SP3 does cause trouble for those of us that Dual Boot. Just wondering if thats what the wife updated to.

---

### Post by starfailure on 2008-06-12
I don't know if that's what the update was or not... Could you elaborate on this "trouble"?  :\

---

### Post by dstew on 2008-06-12
The partitions look OK. Perhaps the boot disk got changed in BIOS. Check to see if it is booting the proper disk. It seems that the smaller, 122.9 GB disk is the one to boot.

I think grub will work without sudo on the Live CD, since you are root, but try it anyway.

---

### Post by meierfra. on 2008-06-12
>  since you are root

No, one is logged in as "ubuntu", not as "root":

> ubuntu@ubuntu:~$

 The "sudo" is necessary.

---

### Post by starfailure on 2008-06-13
Well, that was it... 

I did :-$sudo grub, followed dstew's directions to reset GRUB and all is normal.  
Stupid Microsoft.

Thanks for all your help.

---

