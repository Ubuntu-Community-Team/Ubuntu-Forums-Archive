---
title: "meaning of all_generic_ide"
date: 2008-06-09
forum: Installation &amp; Upgrades
---

### Post by g320907aa on 2008-06-09
After weeks of trying to boot from SATA DVD, I found all_generic_ide options makes the live cd to boot. Before, I was constantly having problem where the live cd takes it to initramfs. After that I googled all over for the meaning of this switch but nowhere it says anything about it other than just using it. 
I wonder what the meaning of this switch for?

---

### Post by g320907aa on 2008-06-10
No one knows it?

---

### Post by Dave2k6 on 2008-06-10
I would guess that it forces the linux kernel to see the STA controller as a Generic IDE controller.

I also had to use that boot parameter (along with floppy=off & irqpoll, to get the installer to recognise my laptop's internal SATA harddrive correctly.

---

### Post by dstew on 2008-06-10
I think what is happening is that the Live CD kernel runs a hardware autodetect program that tries to figure out what kind of disk controller you have, and then loads the appropriate driver. It seems that some disk drive and controller combinations are not happy with this driver. So, the kernel parameter tells the kernel not to bother with using the "better" driver, but just use a generic IDE driver.

People who study these things write all kinds of interesting posts on the Lauchpad site, getting into the code. I think they know exactly what the problem is, so the next kernel version will have drivers that work correctly, we hope. Until then, the work-around is used.

---

### Post by g320907aa on 2008-06-11
i wonder if looking into linux source code will help.

---

### Post by dstew on 2008-06-11
If you want to, go ahead. Please post back if you can figure out the correct answer.

---

### Post by g320907aa on 2008-06-13
> **dstew said:**
> If you want to, go ahead. Please post back if you can figure out the correct answer.

Well i copied the casper/initrd.gz into my hard drive. I presume it is a kernel file (correct me if I am wrong). Unzipped and there was a single 19MB file of binary. I searched for this string inside the file and found several instances. One of them has some kind of comments that says 'claim all unidentified IDE controller'. That is as far as I went.

---

