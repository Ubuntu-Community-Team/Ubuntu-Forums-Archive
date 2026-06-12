---
title: "Fresh install: no ubuntu option in grub menu"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by cse on 2012-11-23
hi,
just moved to ubuntu 12.10.
my problem is that i have no option in grub menu for ubuntu, only two memtest and win7.
i'm in live cd. i installed ubuntu from hard disk using unetbootin.
i have tried all steps in this page: [http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/](http://howtoubuntu.org/how-to-repairrestorereinstall-grub-2-with-a-ubuntu-live-cd/) 
when  tried update-grub:
```
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Cannot find list of partitions!  (Try mounting /sys.)
done

```so i tried mounting /sys:
```
root@ubuntu:/# mount /sys
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
root@ubuntu:/# grub-install --recheck /dev/sda
Installation finished. No error reported.
root@ubuntu:/# update-grub
Generating grub.cfg ...
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
```still ubuntu not found.
fdisk -l result is this:
```
root@ubuntu:/# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x1707a8a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102402047    51097600    7  HPFS/NTFS/exFAT
/dev/sda3       102402048   921602047   409600000    6  FAT16
/dev/sda4       921604094   976771071    27583489    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       921604096   941602815     9999360   83  Linux
/dev/sda6       941604864   951367679     4881408   82  Linux swap / Solaris
/dev/sda7       951369728   976771071    12700672   83  Linux

Disk /dev/sdc: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            8192     7744511     3868160    b  W95 FAT32

```
[EDIT]```
ubuntu@ubuntu:~$ sudo os-prober
/dev/sda1:Windows 7 (loader):Windows:chain
/dev/sda5:Ubuntu 12.10 (12.10):Ubuntu:linux

```
but when tried:
```
ubuntu@ubuntu:~$ sudo update-grub2
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.

```[/EDIT]
i have installed linux many times before without such cases. no idea what went wrong this time.
help will be highly appreciated.
thanks in advanced!!!
Regards

---

### Post by oldfred on 2012-11-24
You cannot run sudo update-grub from liveCD. It is trying to update the grub on the CD which cannot be updated.

Often better to use Boot-Repair. 

       Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by cse on 2012-11-24
I got following result after good 10 mins processing.
Going to reboot, let me see what goes on?
```

Boot successfully repaired.

Please write on a paper the following URL:
http://paste.ubuntu.com/1382427/

```

Thanks for the help

---

### Post by darkod on 2012-11-24
You say you have the live cd but you still decided to install from hard disk using unetbootin? Even if you didn't have the cd at that time, it's better to create it instead of trying to install from hdd to the same hdd. It's not impossible, but things can go wrong and you are looking for trouble.

Let us know how it went after the reboot since the bootinfo looks OK to me at first glance.

---

### Post by oldfred on 2012-11-24
Boot-Repair made lots of fixes.

I still see this in your Window partition which is a grub file that should not be there.

/boot/grub/grub.cfg

Your Windows boot has these which may be from EasyBCD?

/grldr

---

### Post by cse on 2012-11-27
it was fixed after reboot :-)
How can i mark it solved?

> **oldfred said:**
> Boot-Repair made lots of fixes.

I still see this in your Window partition which is a grub file that should not be there.

/boot/grub/grub.cfg

Your Windows boot has these which may be from EasyBCD?

/grldr
i have no idea how you see this, may be you see 
```
/dev/sda1:Windows 7 (loader):Windows:chain
```
i tried using EasyBCD once i found no ubuntu menu, but during its installation i got another idea that my grub was installed on MBR, so it was not going to help me as per my knowledge...correct me.

> You say you have the live cd but you still decided to install from hard  disk using unetbootin? Even if you didn't have the cd at that time, it's  better to create it instead of trying to install from hdd to the same  hdd. It's not impossible, but things can go wrong and you are looking  for trouble.

Let us know how it went after the reboot since the bootinfo looks OK to me at first glance. 	
i have done this many times before, i mean installing from HD, without any problem excepting few occasions when i forgot to change location for grub, but not this time. so bootrepair fixed it correctly.

Thanks oldfred and darkod for the help.

---

### Post by oldfred on 2012-11-27
Glad it is working.

The BootInfo script shows files that may be hidden in Windows. Either in Windows you have to unhide or from Ubuntu edit to remove extraneous files. If it works then it may not be an issue to worry about.

To post as solved see my signature. :)

---

