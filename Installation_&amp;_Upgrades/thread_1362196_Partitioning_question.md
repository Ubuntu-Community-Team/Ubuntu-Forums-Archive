---
title: "Partitioning question"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by Drjim on 2009-12-22
I'm thinking about installing remix on my samsung netbook. I'd like to set up separate partitions for ubuntu and windows. I know the usb drive I've prepared can do this. 

I have 8.04 on my laptop as a wubi installation. I can access my windows files from ubuntu. If I set up remix as a separate partition, will I still be able to access my windows files (via openoffice or other cross-platform programs) from ubuntu? 

Second question: if I change my mind later, can I undo the partitioning without :confused:screwing up the windows 7 starter os?


Thanks,

Jim

---

### Post by x33a on 2009-12-22
you can access windows files (fat32/ntfs) from a non wubi installation also.

if you intend to remove ubuntu later on, you'll have to restore windows 7's bootloader, as grub (ubuntu bootloader) will be removed.

---

### Post by Drjim on 2009-12-24
Thanks

---

### Post by Mark Phelps on 2009-12-24
> **Drjim said:**
> Second question: if I change my mind later, can I undo the partitioning without :confused:screwing up the windows 7 starter os?

I'm going to break from the pack here and say -- probably NOT.

Why?

Because I believe that your netbook does not have (1) an optical drive or (2) ability to boot from an optical drive.

If these are both true -- you are asking for major problems if you go traditional dual-boot because you will not later be able to boot from CD/DVD to restore the Win7 MBR.

Also, when you shrink the Win7 OS partition to make room for Ubuntu, if you use the Ubuntu installer to do that, and you encounter Win7 OS bootloader corruption as a result, without the ability to boot from a Win7 recovery CD, you will have no way to restore the Win7 boot loader.

More typically, this does not pose such problems because Win7 provides the builtin feature to create and burn a Win7 recovery CD, and folks can later boot from that to do any needed repairs.  But even if you did burn this CD, if you have no way to boot from it, you're hosed should some boot problem arise.

---

### Post by Drjim on 2009-12-24
[QUOTE=Mark Phelps;8553766]I'm going to break from the pack here and say -- probably NOT.

Why?

Because I believe that your netbook does not have (1) an optical drive or (2) ability to boot from an optical drive.

Can I make a restore disc on a usb drive or an SD card?

Jim

---

