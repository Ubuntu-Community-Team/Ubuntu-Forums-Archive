---
title: "Installing Windows 7 beside Ubuntu 11.10"
date: 2011-10-27
forum: Installation &amp; Upgrades
---

### Post by aryandelhi on 2011-10-27
I have Ubuntu installed on my laptop. Now I also want to install Windows 7 beside Ubuntu.

How can I do that?

Virtualization in not an answer for me because I want to install Unity 3d which consumes a lot of system resource.

Thanks!

---

### Post by vicshrike on 2011-10-27
I have always found it much easier to install Windows first, and then Linux, because the Windows installer does not recognize any other os than Windows. But it is doable, Google can probably be of help here.

---

### Post by ahso4271 on 2011-10-27
[http://www.youtube.com/watch?v=GhnLk3gviWY&feature=related](http://www.youtube.com/watch?v=GhnLk3gviWY&feature=related)

---

### Post by Snader on 2011-10-27
You will need to think carefully about the partitions on your harddisk (partition size and partition type: primary vs. extended) and you will need to restore GRUB after installing Windows. This information might be of help to you:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Note: Please make sure that you have a back-up of your data before you start an attempt.

---

### Post by aryandelhi on 2011-10-27
> **Snader said:**
> You will need to think carefully about the partitions on your harddisk (partition size and partition type: primary vs. extended) and you will need to restore GRUB after installing Windows. This information might be of help to you:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Note: Please make sure that you have a back-up of your data before you start an attempt.

Is there any video tutorial on it?

---

### Post by Snader on 2011-10-27
Without a doubt, you will be able to find numerous video tutorials on the installation of a dual boot system. However, I cannot recommend a particular video since I have no experience with video tutorials. My advice would be to read the above presented page since it is maintained by Ubuntu and both nice and comprehensive. If you have any questions regarding this page, please do not hesitate to post them on the forums.

---

### Post by Mark Phelps on 2011-10-27
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

### Post by aryandelhi on 2011-10-28
I think it is better to Install Windows first and then re-install Ubuntu.

Thanks for your reply!

---

