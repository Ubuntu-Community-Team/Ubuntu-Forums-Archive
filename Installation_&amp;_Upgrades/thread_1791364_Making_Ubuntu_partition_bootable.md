---
title: "Making Ubuntu partition bootable"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by aa4bb on 2011-06-26
Base system is a Dell Inspiron 1525 with Vista.

I installed 9.04 as a dual boot. Ubuntu and swap partitions were in the extended partition. I did an upgrade to 10.04. It booted routinely into 10.04 and my user files were in /home on the 10.04 partition. I still saw a volume that had 9.04 but there was nothing of value there. Using Disk Utility, I deleted that volume to free up space. However, my system would no longer boot.

I downloaded SuperGrub and used it to boot into Vista. I downloaded EasyBCD but it wasn't able to restore booting to Vista. I then downloaded the Vista Recovery Disk and it restored booting into Windows. 

In Vista, I then used EasyBCD to add a second boot option, to boot Ubuntu. I used the option to specify the partition to boot, which it identified as Ubuntu 10.04.

When I boot Vista, all is fine. However, if I choose Ubuntu in the Vista boot manager, the screen goes blank and nothing happens. I suppose there is something missing in my 10.04 partition (GRUB, GRUB2?) that is needed to allow Ubuntu to boot. Is that right? I tried the function to activate a partition in SuperGrub, but that didn't work. There is some reference to starting GRUB and using the command line to make the partition bootable, but I haven't been able to discover how to do it.

---

### Post by nzjethro on 2011-06-26
Can you boot from a Live Ubuntu CD, then mount your Ubuntu partition, chroot in, and reinstall grub?

[This guide]("http://opensource-sidh.blogspot.com/2011/06/recover-grub-live-ubuntu-cd.html") should help.

---

### Post by aa4bb on 2011-06-26
Thanks, nzjethro. I will give this a try.

---

### Post by nzjethro on 2011-06-26
If you have any issues, post back here, and someone will be able to help out.

---

### Post by mörgæs on 2011-06-26
As a side note: If you install 9.04 (including Grub 1) and upgrade to 10.04, you will still have Grub 1, unless you also upgrade Grub. 

A fresh install of 10.04 would have given you Grub 2 automatically.

---

### Post by aa4bb on 2011-06-26
Here's what happened:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    6  FAT16
/dev/sda2   *           6        1280    10240000    7  HPFS/NTFS
/dev/sda3            1280        8228    55805562    7  HPFS/NTFS
/dev/sda4            8229        9729    12056782+   5  Extended
/dev/sda5            8229        9348     8996337   83  Linux
/dev/sda6            9349        9404      449788+  82  Linux swap / Solaris

Disk /dev/sdb: 4051 MB, 4051697152 bytes
125 heads, 62 sectors/track, 1021 cylinders
Units = cylinders of 7750 * 512 = 3968000 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ad0a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1021     3956344    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/boot
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /usr/ /mnt/usr
ubuntu@ubuntu:~$ sudo chroot/mnt
sudo: chroot/mnt: command not found
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# ls
bin    dev   initrd.img      lost+found  opt   sbin    sys  var
boot   etc   initrd.img.old  media     proc  selinux    tmp  vmlinuz
cdrom  home  lib         mnt     root  srv    usr  vmlinuz.old
root@ubuntu:/# cd boot
root@ubuntu:/boot# ls
Boot     grub          Program Files  System Volume Information    Windows
bootmgr  NST          $RECYCLE.BIN   Tools
dell     ProgramData  sources         Users
root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
device.map
root@ubuntu:/boot/grub# cd /
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# cd boot
root@ubuntu:/boot# cd grub
root@ubuntu:/boot/grub# ls
default  device.map  menu.lst
root@ubuntu:/boot/grub# cd /
root@ubuntu:/# grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
root@ubuntu:/# update-grub -h
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
grep: /boot/config*: No such file or directory
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# man update-grub
root@ubuntu:/# update-grub2
The program 'update-grub2' can be found in the following packages:
 * grub-pc
 * grub-coreboot
 * grub-efi-amd64
 * grub-efi-ia32
 * grub-ieee1275
Try: apt-get install <selected package>
root@ubuntu:/# exit
ubuntu@ubuntu:~$ 


So, I got as far as update-grub, but it did not make a .cfg

I went ahead and tried grub-install but it generated an error message.

Not sure where to go from here.

---

### Post by nzjethro on 2011-06-26
Ok from what I can see, /dev/sda2 is your Windows install, while sda5 is your Ubu install. First up, although it is a boot device, don't mount /dev/sda2 as /mnt/boot. This is because /dev/sda2 has all your Widows MBR files but won't know anything to do with Grub. Doing so is what caused this a number of errors.

Try again, without mounting /dev/sda and /mnt/boot (don't mount anything as boot - skip that step).

It may also be a Grub Legacy/Grub2 issue, so if that doesn't work post back, and we can try something else.

---

### Post by YesWeCan on 2011-06-27
Yes, that is right. The chroot should only involve Ubuntu files. I think if the process is repeated correctly it will probably work.

Grub legacy is installed. So once 10.04 boots you ought to upgrade to Grub2. Instructions here: [https://help.ubuntu.com/community/Grub2#ChRoot](https://help.ubuntu.com/community/Grub2#ChRoot)

---

### Post by aa4bb on 2011-06-27
Spot on, nzjethro. It worked like a charm.

I will now try upgrade to Grub2, YesWeCan.

Thank you!!

---

### Post by nzjethro on 2011-06-27
> Spot on, nzjethro. It worked like a charm.

Brilliant - glad we could help. AS always, could you please mark this threas as solved so others know there's a solution here? (Instructions in my signature).

---

