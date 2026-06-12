---
title: "Live USB drive no longer boots to installer after installing 12.04"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by kiryu3000 on 2012-10-08
Hello,

I have managed to install Ubuntu 12.04 LTS and it's great so far! All I need to do now is to resize some partitions on my hard drive (namely, my boot drive). In order to do that, I need to boot into the installer, go to "Try Ubuntu", then use Gparted to resize my boot partition. However, when I tried to do this using the same live USB stick that I used to install Ubuntu 12.04 in the first place, I am not prompted to the installer screen; my machine simply loads GRUB. Are there any configurations that I need to do?

Thanks.

---

### Post by oldfred on 2012-10-08
Welcome to the forums.

Did your grub2 boot loader also get installed to the MBR of the USB flash drive?

From your install post the link to BootInfo report. Just want to see what boot loader is in the MBR of the flash drive, so have it plugged in also.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

