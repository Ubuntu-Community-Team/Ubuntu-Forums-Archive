---
title: "Boot failure"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by sarapoglou on 2015-12-14
Hi,

after an update/upgrade I couldn't boot into Linux. The only way to boot was via a SuperGrub2 disk. I decided to install Linux in a new hard disk. However, the problem remains. I can boot the hard disk only via SuperGrub2 disk (usb stick). I tried to use boot-repair with no success. Here is the summary info [http://paste2.org/VdCgXvLN](http://paste2.org/VdCgXvLN).

If anyone could help me.

Thank you in advance.

---

### Post by yancek on 2015-12-14
You have two 1TB hard drives.  Have you set the boot priority to boot from the first drive, the on which you formerly had windows?

---

### Post by sarapoglou on 2015-12-14
> **yancek said:**
> You have two 1TB hard drives.  Have you set the boot priority to boot from the first drive, the on which you formerly had windows?

Here is the configuration of the Hard Drives

HDD1
   /dev/sda1 fat32           /boot/efi     512.00MB     flag:boot
   /dev/sda2 ext4            /                923.12GB                     
   /dev/sda3 linux-swap                       7.89GB 

HDD2             
   /dev/sdb1 ext4                          931.51GB         

The BIOS boot priority is
  1st USB
  2nd Hard drives

I didn't have Windows. I made a clean Linux installation to HDD1 (using liveCD-USB) and then format to HDD2 (ext4).

---

### Post by matyapiro31 on 2015-12-16
I also have same problem.(;_;)

---

### Post by oldfred on 2015-12-16
What brand/model computer?
Do you have Secure boot on? Try with it off.
Make sure you have UEFI boot on and CSM/Legacy/BIOS boot off. Your install is for UEFI boot.

You show default boot as 0001, which is a BIOS boot. Your want 0000 ubuntu which is the UEFI boot. See lines 959 and up.

---

