---
title: "Bootpartitiontype of Xubuntu16.04 USB stick"
date: 2017-02-20
forum: Installation &amp; Upgrades
---

### Post by hvn2 on 2017-02-20
Hi,

I'm trying to make a bootable USB stick from a verified image and find that it won't boot. So after burning with "sudo dd if=<omitted> of=/dev/sdc", I check with "fdisk -l" and find its boot partition is "hidden HPFS/NTFS". This seems not correct since it's not booting. Did I do something wrong?

Thanks,

hvn

Sorry for multiple posting..forum gave an error the first time.

---

### Post by oldfred on 2017-02-20
I am a bit surprised fdisk even sees it, they must have updated it to include the hybrid configuration.

One of the issues of the hybrid flash drive was you then could not use standard partition tools to reuse it until you erased the partition table with dd. But that may now be fixed?

 The daily ISOs for the Ubuntu Oneiric 11.10 development cycle (and all official Ubuntu CD releases going forward)
for i386 and x86_64 platforms will be now spun as hybrid ISOs. Or you can use dd.
[http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid](http://ubuntuforums.org/showthread.php?t=1783752&highlight=Hybrid)
dd creates hybrid which does not have standard partition table, you need to delete with dd beginning of flash drive to restore it to full size.
iso9660 file system

---

### Post by hvn2 on 2017-02-20
Thank you for your response. Some comments:
- I was surprised about the "fdisk -l" as well, but it clearly showed the hidden boot-marked partition.
- I've tried to boot the image on 3 different pc, which all have been installed before via USB. On none of these, this image booted or was even recognized (auto-mounted) which never happened to me before.
- the USB bootable stick is not intended for a UEFI but for a few years old BIOS pc. Should I prepare the USB stick in a different way then?
- Yes, I found earlier I had to use gdisk to completely erase a UEFI USB stick, but since this one wasn't recognized at all, I thought something was wrong with the image.

hvn

---

### Post by ajgreeny on 2017-02-20
I've been using **[mkusb]("https://help.ubuntu.com/community/mkusb")** to create bootable USBs now for a while and so far it has been faultless in making a USB that works on any computer I have tried it on.

Give that a try and come back again if you still have no luck.

---

### Post by hvn2 on 2017-02-20
I've installed and tried mkusb, which also uses dd. After writing the USB stick, the file manager clearly shows that the USB stick is a bootable Xubuntu 32bits disk (which was an improvement over my previous attempts). However, after unmounting/re-inserting it, the pc doesn't recognize it again. Same with the other pc's: no recognition except with "fdisk -l" and no boot. Any more suggestions?

---

### Post by oldfred on 2017-02-20
Is system so old that it does not boot from USB port?

Or are you looking for USB device to boot and it really is another hard drive?
My old desktop from 2006 had many USB boot options. And I knew flash drive worked as laptop would boot it. 
But then one day with flash drive plugged in and rebooting I got to hard drive boot menu and flash drive was there. I had almost given up.

---

### Post by hvn2 on 2017-02-20
The 3 systems that I try are: very old BIOS Pentium-M installed via USB, a BIOS Pentium B960 from 2012 installed via USB and 1 brand-new UEFI Pentium Core i7, also installed via USB. All three systems work great. I just use them to test this USB stick which is intended for a system on a different location. And if these systems won't boot from the USB stick, the target system won't either.
Given the latest attempt, I have no clue what the cause is. I consider to remove everything manually using gdisk and try dd again. I recall that installing the Core i7 gave problems due to some UEFI boot stuff on the USB stick which I could only resolve via gdisk.

---

### Post by oldfred on 2017-02-20
No guarantees on system boot, flash drive & flash drive configuration.
We see many posts where user could not use one installer but another worked, or could not use one flash drive but another worked.
Not sure if downloaded ISO, how user actually installed it or actual flash drive issue.

Standard Ubuntu ISO is configured for both BIOS & UEFI boot.
Very old system, may only boot with 32 bit version or 32 bit Lubuntu BIOS boot.
Very new system will require 64 bit version for UEFI boot, but may boot with 32 bit Ubuntu in BIOS, but not sure why anyone would want to do that.

 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
USB flash drives Pendrive lifetime sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297](http://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297)

---

