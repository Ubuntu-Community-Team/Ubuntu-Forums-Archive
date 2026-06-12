---
title: "Cannot boot after clean install of 1Ubuntu 12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by Najand on 2012-05-24
Ok, I have been using Linux for 7-8 years now and have been with ubuntu since Breezy Badger (5.10). Last month, I bought a new desktop "Acer AM3470G-UW10P Desktop PC with AMD Quad-Core A6-3620 Accelerated Processor, 4GB Memory, 500GB Hard Drive" to replace my old Pentium 4 computer which was as old as Breezy.

Then I made a USB live disk to install Ubuntu as directed in the website. During booting the USB I saw that it has been booted using EFI. It booted smoothly and I saw the unity environment of Ubuntu (Something I could not use using with my previous computer). 

So, I tried to install Ubuntu. The plan was to install Ubuntu on a separate SATA (Hitachi Global Storage Technologies) with 320GB space and put the boot wizard on that (/dev/sdb). Installation wizard started smoothly and everything finished successfully.

Then I booted the system and I removed the USB. I selected the Hitachi HDD to boot from it and it showed me a blank screen with a blinking cursor. I tried every possible button on my keyboard to reach the Grub menu but it was not showing anything. (It looks to me that the Grub is not loaded)

So I tried the live USB again and tried to fix the boot using boot-repair from repositories. It said EFI feature has been detected and I need a 200MB+ FAT32 partition for EFI at the beginning of the HDD. I didn't have (and still don't have) any idea EFI works. So I created the FAT32 partition using Gnu Parted and ran boot-repair again. It said that it has been fixed. So I rebooted my computer and I got "ERROR: No bootable device was detected". I searched around and found I have to check if I have GPT enabled using gparted. I did it on live Ubuntu and then made a EFI system partition (EF00) using it. Then I tried boot-repair, installing grub-efi with "chroot"ing and installing fresh ubuntu over and over and I was getting different error. The last error is "Error: Operating System is missing" after checking the EFI setting using efibootmgr and I think everything looks good on that. I have been struggling with this for 5 days now and still not able to boot. 

Please help me to fix this problem. Thanks.

---

### Post by wilee-nilee on 2012-05-24
Could you make some paragraphs with that first post, for me it is unreadable as a wall of text, might be for others as well. :)

Use this tool and run the create a boot summary only and post that summary as well.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

