---
title: "How to overwrite windows vista with windows XP, without harming ubuntu?"
date: 2010-09-10
forum: Installation &amp; Upgrades
---

### Post by Jessi on 2010-09-10
I would like to replace Windows Vista with Windows XP without uninstalling my Ubuntu partition. I use ubuntu 90% of the time, but would like to have XP for games and for my printer. Is there a way to just overwrite Vista and not Ubuntu? I booted my XP disk and it came up with many different partitions, 4. I wasn't sure what my Vista one was named or which one I should overwrite. 

Thanks in advance.

---

### Post by howefield on 2010-09-10
What's the output from the following terminal command ?

```
sudo fdisk -l
```

PS. You will harm your Ubuntu install, in as much as XP will overwrite Grub with it's own bootloader, easy to fix as you can reinstall Grub, but so as you know.

---

### Post by Jessi on 2010-09-10
```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe6345cc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13057   104880321    7  HPFS/NTFS
/dev/sda2           28843       30401    12522667+   7  HPFS/NTFS
/dev/sda3           13058       28842   126793012+   5  Extended
/dev/sda5           13058       28195   121595953+  83  Linux
/dev/sda6           28196       28842     5196996   82  Linux swap / Solaris

Partition table entries are not in disk order

```

Hmm how difficult is it to reinstall grub? I mainly want to keep my software and settings. I did some editing and configuring that I don't want to loose. I'd be ok loosing my files, but things like setting up wine to run certain programs and installing java instead of iced tea to use Jtablet for oekakis took some work. Is there a way to back that up, whipe my computer, install XP, install Ubuntu and recover my ubuntu settings?

---

### Post by oldfred on 2010-09-10
Several versions of instructions to reinstall grub. You just need a liveCD and know which partition is your Ubuntu install - sda5.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)


Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda5 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

