---
title: "A simple installation question"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by andyj1 on 2006-07-25
Hi there.

This is my very first posting on a Ubuntu forum, so please be gentle with me. :) 

I have an ancient PC (Pentium MMX) running Windows 98 and RedHat 8.  I am finally in a position to get a new machine.  I am planning on getting an AMD64 machine, perhaps with a dual core CPU (socket 939 Athlon 64).  I will have 2 SATA disks and a half of the first one will be taken by Windows XP.  I was thinking about installing Linux on the 2nd disk but putting the /usr partition on the rest of the first.

I have the following simple questions about installation:
1. I understand that I run the Live CD and once Ubuntu boots and finds my essential hardware, I just click on the installaction icon on the desktop.  Is this correct?
2. Will the installer see my Windows partition and set up multiboot automatically?
3. Will the installer give me boot choices of the Linux kernel automatically (between 32bit, 64bit and SMP, if I get a dual core chip)?
4.  Do I still need to make a /boot partition at the beginning of the second disk so GRUB will see everything.

Thanks in advance.  All additional comments are welcome.

Andy

---

### Post by altonbr on 2006-07-25
1. Yes (for the most part... there are always exceptions)... ATI graphic cards and SOME printers are usually the main problems

---

2. GRUB will locate Windows, but for your partitioning, you need to do it manually and set up a 'ext3' partition (this is the main installation format) and 'linux-swap' (should be the size of your RAM or double ... ie: 512MB or 1024MB)... and if you want to share files between Windows and Linux, make a data partiton that is FAT32 (this would then probably be bigger then your 'ext3' partition if you hard drive is large enough)

---

3. I'm not sure, I've never had a 64-bit chip... I know that is GRUB will detect your other OSs (if they have a boot flag) like I said above

---

4. I don't THINK so.



I am quite the amateur as you can tell, so maybe a more advanced user will come by and give you more specifics. But, nonetheless, I hope I helped a bit.

---

### Post by bukwirm on 2006-07-25
3. I don't know if they will be installed automatically, but it is really easy to install new kernels - just find the package in Synaptic and install!

---

