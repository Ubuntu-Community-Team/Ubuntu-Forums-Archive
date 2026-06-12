---
title: "Ubuntu 21.04 Won't Boot After Installation"
date: 2021-07-29
forum: Installation &amp; Upgrades
---

### Post by yasirrwebdesigner on 2021-07-29
okay, So I had Manjaro 21.1.0 (EFI) installed on my laptop and it was  running fine until my dumbass decided to install Ubuntu because Among Us  wasn't working on Manjaro for some reason I saw a couple of reviews on  ProtonDB and the issue seemed with Manjaro only and I decided to install  Ubuntu as it had good reviews.

 Instead of doing some research I decided  let's go back to Ubuntu downloaded the 21.04 because I didn't had time  to do research and find out what's wrong with Manjaro, plus I had  separate partitions so I was good at least that's what I thought.

Now  before the installation I deleted and recreated the EFI partition in  gparted FAT32 flagged ESP/BOOT and formatted the root rest I didn't  touch and proceed with installation selected the partition of efi, root,  and home the installation went fine but it didn't boot I don't know  what's going on but it keeps rebooting on HP splash screen over and over  unless I go to boot menu and  manually choose the efi/grub file from  there. 

No one touched the BIOS Manjaro was also on EFI not on legacy the  Disks Utility shows the partition mounted as /boot/efi. but it doesn't  boot on its own ctrl+alt+f4 doesn't work as it still is on HP splash  screen and boot process never starts. 

I even did a complete reinstall  multiple times at this point thinking that I might be doing something  wrong I even went with the auto partitioning and still didn't boot now  in 3rd try I even create a 5mbs partition for something like Reverse  bios grub i don't remember what it was called but it was suggested by  the installer. Now what do I do? So that boots on its own I wouldn't  have to go to boot menu every time.

```
zero@Phoenix:~$ sudo fdisk -l 
[sudo] password for zero:  
Disk /dev/loop0: 32.27 MiB, 33841152 bytes, 66096 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop1: 51.04 MiB, 53522432 bytes, 104536 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop2: 218.99 MiB, 229629952 bytes, 448496 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop3: 55.45 MiB, 58142720 bytes, 113560 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop4: 64.77 MiB, 67915776 bytes, 132648 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop5: 68.75 MiB, 72093696 bytes, 140808 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/loop6: 164.76 MiB, 172761088 bytes, 337424 sectors 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
 
 
Disk /dev/sda: 465.76 GiB, 500107862016 bytes, 976773168 sectors 
Disk model: HGST HCC545050A7 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 4096 bytes 
I/O size (minimum/optimal): 4096 bytes / 4096 bytes 
Disklabel type: gpt 
Disk identifier: 90A3A38A-B1D9-4814-85D5-57B9EA3569E8 
 
Device         Start       End   Sectors  Size Type 
/dev/sda1    1591296  74991615  73400320   35G Linux filesystem 
/dev/sda2       2048   1581055   1579008  771M EFI System 
/dev/sda3   74991616 221792255 146800640   70G Linux filesystem 
/dev/sda4  221792256 242763775  20971520   10G Linux swap 
/dev/sda5  242763776 976773119 734009344  350G Linux filesystem 
/dev/sda6    1581056   1591295     10240    5M BIOS boot 


```

```

zero@Phoenix:~$ lspci -k | grep -EA3 'VGA|3D|Display' 
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) 
    DeviceName: 64 
    Subsystem: Hewlett-Packard Company 3rd Gen Core processor Graphics Controller 
    Kernel driver in use: i915 

```


EDIT: btw if I choose my hard disk instead of choosing the efi file it still wont' boot.

---

### Post by tea for one on 2021-07-29
> **yasirrwebdesigner said:**
>   unless I go to boot menu and  manually choose the efi/grub file from  there. 

Your post is difficult to follow i.e. Wall of text without paragraphs and punctuation.

Anyway, as you have an HP device, you can successfully boot Ubuntu via the UEFI boot menu using F9 - is that correct?

---

### Post by yasirrwebdesigner on 2021-07-29
> **tea for one said:**
> Your post is difficult to follow i.e. Wall of text without paragraphs and punctuation.
Sorry about that,
> **tea for one said:**
> Anyway, as you have an HP device, you can successfully boot Ubuntu via the UEFI boot menu using F9 - is that correct?
Yes

---

### Post by oldfred on 2021-07-29
Many with HP, update UEFI and then change UEFI boot order with HP's UEFI setup menu (not boot menu).
HP, for whatever reason does not seem to retain boot order changes using efibootmgr which we suggest to correct boot order and also is used by grub to make a new install first in boot order.
see this for typical commands, but some do not work with HP:
man efibootmgr
To see boot order:
sudo efibootmgr -v

HP - escape + F9 for boot menu, F10 for UEFI/bios setup

---

