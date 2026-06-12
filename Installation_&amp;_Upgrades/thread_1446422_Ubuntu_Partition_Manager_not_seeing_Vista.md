---
title: "Ubuntu Partition Manager not seeing Vista"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by zippyzappy74 on 2010-04-04
Hi there,

Ok to make a long story short I have Vista Ultimate 32 Bit installed on my single Maxtor 250GB SATA I HDD.  What I would like to do is put Ubuntu Ultimate 2.4 64 Bit in a dual boot config.  However, following the advice in the forums and elsewhere where I was told to first shrink my Vista volume, shut computer down and then run Ubuntu CD hasn't been working.  The Live CD will boot however it won't recognize the space I've freed for Ubuntu.  Also I do NOT have Bitlocker enabled nor does my motherboard support that function without using a thumb drive etc.  

I am running a Pentium Dual Core CPU (E6300) 2.8GHZ, 2GB PC2 6400 DDR2, on a Gigabyte GA-G41M-ES2H Rev 1 w/ F1 BIOS, Maxtor SATA I 250GB HDD, and Samsung Toshiba 22X DVDRW (IDE).

Any advice would be appreciated..

---

### Post by sikander3786 on 2010-04-04
Just a thought.

Did you partition your freed space in Vista? If so leave the free space unpartitioned and Ubuntu should see it.

---

### Post by mikewhatever on 2010-04-04
> The Live CD will boot however it won't recognize the space I've freed for Ubuntu.

What do you mean by that? Can you open Applications->Accessories->Terminial and post the output of the following:

sudo fdisk -l

---

### Post by zippyzappy74 on 2010-05-04
Ok sorry for the delay in responding.  I finally fixed the problem of Ubuntu's partiton manager not seeing the unallocated space I had created in Vista Ult.  It turns out upon further reading that it does actually have something to do with Vista Ultimate's file structure.  So I decided to reformat my system using my Vista DVD and created unallocated space within the Vista partitioning ultility and left that space unformatted.  Bang it worked!!  I rebooted with my Ubuntu DVD and it (Ubuntu partition manager) saw the unallocated space and I was able to install Ubuntu.

Thank you for the ideas..

---

