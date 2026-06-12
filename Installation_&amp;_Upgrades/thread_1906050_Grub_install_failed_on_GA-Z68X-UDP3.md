---
title: "Grub install failed on GA-Z68X-UDP3"
date: 2012-01-08
forum: Installation &amp; Upgrades
---

### Post by lovelyzoo on 2012-01-08
Brief summary: How do I fix a failed Grub install?

I have just attempted an install of Ubuntu on to a new machine. Having done so I am met with the message "DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER".

The machine is a triple boot Hackintosh, and I have already completed the OSX and Win7 installs successfully. I can boot to either of those two partitions using Chameleon (oreferred bootloader of the Hackintosh community) off of a USB pendrive. Therefore I'm certain of the hardware's integrity. 

Note that the disk is a Hybrid format. I did observe that subsequent to the Ubuntu install a protective MBR was in place. I did have to repair the MBR using gdisk to fix the Win7 install. 

I've booted the machine using the live disk and so believe that it is capable of running Ubuntu. Having done I checked the partitioning using gparted, it looks good to me. Finally, I mounted the EFI System Partition and verified the presence of 'efi/ubuntu/grubx64.efi'

My mother board is a GA-Z68X-UDP3 with the F4 BIOS.

My best guess is that the exotic nature of my system confused the Ubuntu installer and that Grub has not installed properly. Can anyone explain how to do this?

---

### Post by lovelyzoo on 2012-01-11
Bumping, can anyone give me a hint as to how to investigate this?

---

### Post by lovelyzoo on 2012-01-14
I have now successfully booted Ubuntu using the version Super Grub 2 disk on the Ultimate Boot CD.
I took a look at grub.cfg and the conditional statements in the script look like they are talking about my OSX, Windows and Ubuntu partitions. Finally, I executed 'sudo update-grub2' which also completed successfully.

However upon reboot I still get the "DISK BOOT FAILURE" error.

---

### Post by YannBuntu on 2012-01-17
Hi
please follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1821980") and indicate here your BootInfo.

---

### Post by lovelyzoo on 2012-01-19
> **YannBuntu said:**
> Hi
please follow [this tutorial]("http://ubuntuforums.org/showthread.php?t=1821980") and indicate here your BootInfo.

Thanks for your interest but I've decided to install 10 LTS instead which is now working.

---

