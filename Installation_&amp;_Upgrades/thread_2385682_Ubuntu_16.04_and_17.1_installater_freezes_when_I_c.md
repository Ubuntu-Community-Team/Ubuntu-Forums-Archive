---
title: "Ubuntu 16.04 and 17.1 installater freezes when I click “Continue”"
date: 2018-02-23
forum: Installation &amp; Upgrades
---

### Post by mntolia on 2018-02-23
I am trying to install Ubuntu on dual-boot on my Desktop but the installation keeps getting stuck at this stage: 

[https://preview.ibb.co/iv5Qfx/IMG_20180223_013507.jpg](https://preview.ibb.co/iv5Qfx/IMG_20180223_013507.jpg)


This is what I tried so far: 
- I tried installing via pendrive & DVD 
- I tried using UEFI & Legacy BIOS mode 
- I tried both partition schemes on Rufus
- I clicked "Try Ubuntu", then clicked "Install" 
- I unticked "Install 3rd party software" and then clicked "Continue" 
- I turned off secureboot for Ubuntu 16.4



Each time I get stuck at the above step(picture).
I waited for an hour but the installer doesn't go further.
I am able quit the installer and shutdown/restart the PC. 

These are my PC specs: 
- Asus M97M-E Motherboard 
- Intel i7 - 7700 
- Nvidia GTX 1060

---

### Post by rouvenster on 2018-02-24
On my PC it always freeze on that part but not that long. Maybe try to skip the "connect to the internet" part ? I guess it may be a network issue. Also check if all HDD are connected normally and unmounted (use umount)

---

### Post by mntolia on 2018-03-11
How do I unmount on the installer?

Thanks for the reply. I have been using virtual machine as an alternative but I still prefer to run the OS directly.

---

### Post by anspectrum on 2018-03-11
I had similar kind of issue. I had an SSD and a HDD but one of the HDD partition (created earlier) had warning related to some physical boundary mismatch. You can confirm this by using Ubuntu Live and then trying "sudo parted" command without giving any disk as argument. If it crashed parted then that for sure its the same case. Then use "sudo fdisk -l " to see which partition has that kinda warning. After that, copy all your data from that partition (better from whole disk), remove partitions (you can use Windows installer for that purpose) and then reinstall Ubuntu.

Hope that helped.

---

### Post by mntolia on 2018-05-01
I still haven't resolved this issue. My VM is becoming slow so I want to install on dual-boot but I am still facing this issue.

I tried "sudo parted" but it showed no errors.

I executed dh -f. This is what I got:
[IMG]https://i.imgur.com/ns2nj20.jpg[/IMG]

It doesn't appear like any of the hard disks are mounted.

---

### Post by mntolia on 2018-12-23
I solved this issue. For people who are having this problem this is what I did:
- Converted all partitions to GPT(Including Windows)
- Disconnected all hard disks except for the one I am installing Ubuntu to.(The application was getting stuck before the partition manager, so I assumed the hard disks was the issue)
- Created a 50 MB EFI partition.
- Installed Ubuntu and then reconnected the hard disks.
- Used boot repair on Ubuntu to get back the grub menu

---

### Post by vidtek on 2018-12-23
> **mntolia said:**
> I solved this issue. For people who are having this problem this is what I did:
- Converted all partitions to GPT(Including Windows)
- Disconnected all hard disks except for the one I am installing Ubuntu to.(The application was getting stuck before the partition manager, so I assumed the hard disks was the issue)
- Created a 50 MB EFI partition.
- Installed Ubuntu and then reconnected the hard disks.
- Used boot repair on Ubuntu to get back the grub menu

mntolia- Please mark your thread as solved, this will help with others looking for solutions.

Your efi partition is very small at 50mb.  Even Microsoft recommend at least 100mb. With multi-boot options, you will find this will quickly fill up and cause major problems.  I always have a 500mb efi partition to be on the safe side.  Check with oldfred, he is the guru, I follow his partitioning format and have zero issues.
His recommendations are (roughly from memory):
/dev/sda1   EFI=250mb  fat32
/dev/sda2   msreserved partition=100mb fat32 or unformatted
/dev/sda3  if dual-booting with windows this is where windows partition goes I use 100gb  ntfs
/dev/sda4  Microsoft rescue partition ntfs
/dev/sda5  / root=at least 50gb ext2~4 or btrfs
/dev/sda6  ~/home= whatever is left!!  ext2~4 or btfrs

Best regards, Tony

---

