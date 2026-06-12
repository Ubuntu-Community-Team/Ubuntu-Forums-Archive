---
title: "Partitioning problems on a thinkpad"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by mlinchits on 2008-08-06
I am having difficulty getting Ubuntu to recognize my windows partition. Ubuntu stopped recognizing it after I deleted the hidden IBM "Rescue and Recovery" partition to free up space. I still have a working 10 Gig Windows partition and the rest is free space. How can I set up a dual boot in this situation?

This is how the disk is read by GParted:

/dev/sda1 - ntfs - IBM_PRELOAD - 10 Gig
/dev/sda2 - extended - (no label) - 46 Gig
  braches out into: 
       /dev/sda5 - unknown - (no label) - 44.78 Gig
       /dev/sda6 - unknown - (no label) - 1.44 Gig
 
I can delete the whole sda2 partiton, but that doesn't help. So how can I manually patition the disk to dual boot properly?

Thanks a lot,
Max

---

### Post by tech9 on 2008-08-06
> **mlinchits said:**
> I am having difficulty getting Ubuntu to recognize my windows partition. Ubuntu stopped recognizing it after I deleted the hidden IBM "Rescue and Recovery" partition to free up space. I still have a working 10 Gig Windows partition and the rest is free space. How can I set up a dual boot in this situation?

This is how the disk is read by GParted:

/dev/sda1 - ntfs - IBM_PRELOAD - 10 Gig
/dev/sda2 - extended - (no label) - 46 Gig
  braches out into: 
       /dev/sda5 - unknown - (no label) - 44.78 Gig
       /dev/sda6 - unknown - (no label) - 1.44 Gig
 
I can delete the whole sda2 partiton, but that doesn't help. So how can I manually patition the disk to dual boot properly?

Thanks a lot,
Max


you can use gparted - under System>Administration>Partition Editor

---

### Post by tamoneya on 2008-08-06
removing that partition may have messed up the numbering.  Can you post the contents of /boot/grub/menu.lst

---

### Post by mlinchits on 2008-08-06
"Can you post the contents of /boot/grub/menu.lst?"

I haven't installed anything besides windows yet and my live session does not provide a  "/boot/grub/menu.lst" file. 

I have GParted open in my live session, but I don't know how to use it to set up a working dual boot system (in the past I've relied on the installer to do it for me).

---

### Post by spiderbatdad on 2008-08-06
> **mlinchits said:**
> I am having difficulty getting Ubuntu to recognize my windows partition. Ubuntu stopped recognizing it after I deleted the hidden IBM "Rescue and Recovery" partition to free up space. I still have a working 10 Gig Windows partition and the rest is free space. How can I set up a dual boot in this situation?

This is how the disk is read by GParted:

/dev/sda1 - ntfs - IBM_PRELOAD - 10 Gig
/dev/sda2 - extended - (no label) - 46 Gig
  braches out into: 
       /dev/sda5 - unknown - (no label) - 44.78 Gig
       /dev/sda6 - unknown - (no label) - 1.44 Gig
 
I can delete the whole sda2 partiton, but that doesn't help. So how can I manually patition the disk to dual boot properly?

Thanks a lot,
Max

sda2 is an extended partition. It doesn't actually take up space. It allows you to have more than the standard 4 partitions on a single hdd. You can google extended partitions for more info...basically leave it be.
You can use sda5 for you root partition and sda6 for your swap partition. Also the live cd will guide you through the process. You can use all the unused space or manually partition.
There is a screencast here worth watching, regarding creating a separate /home partition as well. [http://screencasts.ubuntu.com/taxonomy/term/54](http://screencasts.ubuntu.com/taxonomy/term/54)

Removing the windows recovery partition wont bother unless you ever delete windows and need to recover. You will have to contact lenovo and order a new disk. They used to provide online recovery, but no longer afaik.

---

### Post by mlinchits on 2008-08-06
Thanks for the link. Just one more question: Do I need to set up a /home partition or will a single root (/) partition do? Which way does Ubuntu do it by default?

---

### Post by spiderbatdad on 2008-08-06
by default ubuntu will create a / and a swap. separate home is not necessary, nor is it offered in guided install. it is totally optional and done through manual partitioning.

---

