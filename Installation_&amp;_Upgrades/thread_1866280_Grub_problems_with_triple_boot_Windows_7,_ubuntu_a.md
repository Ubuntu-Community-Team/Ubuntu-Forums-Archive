---
title: "Grub problems with triple boot Windows 7, ubuntu and sabayon"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by ubukool on 2011-10-21
Hi friends,

I'm stuck trying to triple boot Windows 7, Ubuntu 11.10 and Sabayon.  These are my partitions:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43a42cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    27265023    13631488   27  Hidden NTFS WinRE
/dev/sda2   *    27265024    27469823      102400    7  HPFS/NTFS/exFAT
/dev/sda3        27469824   261844823   117187500    7  HPFS/NTFS/exFAT
/dev/sda4       261844990   580339711   159247361    5  Extended
/dev/sda5       261844992   262348799      251904   83  Linux
/dev/sda6       262350848   266254335     1951744   82  Linux swap / Solaris
/dev/sda7       266256384   295550975    14647296   83  Linux
/dev/sda8       295553024   324847615    14647296   83  Linux
/dev/sda9       324849664   520159231    97654784    7  HPFS/NTFS/exFAT
/dev/sda10      520161280   580339711    30089216   83  Linux

sda1,2 and 3 are Windows 7.  The actual Windows installation is on sda3.
sda4 is an extended partition.
sda5 is /boot
sda6 is swap
sda7 is / for Ubuntu 11.10
sda8 is /home
sda9 is a partition for sharing files between linux and windows
sda10 is / for sabayon 7 GNOME

Everything was fine when I installed Ubuntu, putting grub on /sda5 (I read somewhere that it shouldn't go on the MBR), but then when I installed sabayon and put /boot on sda5 as well, it wiped out all my ubuntu menu options.

I tried to fix this by following a tutorial where I did put grub on /dev/sda and when I booted, all I got was the grub prompt. There's no boot menu and I can't boot into any operating system.  How can I sort out this mess, please?  Thanks in advance for your help! :D

---

### Post by raja.genupula on 2011-10-21
in my signature look at grub recovery that gonna help you.

All The best.

---

### Post by ubukool on 2011-10-21
> **raja.genupula said:**
> in my signature look at grub recovery that gonna help you.

All The best.

Thanks Raja for your help, :) I found this page after I made my request for help and used the Ubuntu 11.10 Live CD to download and run Boot-Repair which is a fantastic piece of software.  I now have a boot menu and can boot into Windows 7 and Sabayon, but Ubuntu 11.10 doesn't show up, unfortunately, which is strange considering I used the Ubuntu live CD to make the changes. Nevermind, at least I can boot into two OSs!

Perhaps my only other option is to reinstall Ubuntu so that grub can 'see' it?  Does anyone have any other suggestions?

---

### Post by raja.genupula on 2011-10-21
> **ubukool said:**
> Thanks Raja for your help, :) I found this page after I made my request for help and used the Ubuntu 11.10 Live CD to download and run Boot-Repair which is a fantastic piece of software.  I now have a boot menu and can boot into Windows 7 and Sabayon, but Ubuntu 11.10 doesn't show up, unfortunately, which is strange considering I used the Ubuntu live CD to make the changes. Nevermind, at least I can boot into two OSs!

Perhaps my only other option is to reinstall Ubuntu so that grub can 'see' it?  Does anyone have any other suggestions?

welcome man, ok you mean There is no Ubuntu Option from the grub menu or anything else ? 
 in my signature boot info script is there , could you please provide me output of that .

---

### Post by oldfred on 2011-10-21
You cannot share a /boot and I do not recommend a separate /boot for most desktops.

You normally do not install grub2's boot loader to the PBR partition boot sector but to the MBR. But you have to decide which boot loader you want to use Ubuntu or Sabayon. I would use the one you boot the most, but I like grub2 and use Ubuntu the most.

You can manually add an entry to Sabayon's menu. Does it use grub legacy or grub2?

Best to see what is installed where. Post the link to boot_info script that you can generate from boot-repair.

---

