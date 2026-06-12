---
title: "GRUB Problems"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by Guerreiro on 2010-08-08
Esteemed (K/X)Ubuntu'ers,

I need some help. I had a Samsung HDD (Internal) that crashed, was a fault of the store that sold it to me and they went bankrupt. I thought I buy an external HDD (Western Digital Elements 1.5TB) and boot Kubuntu from there, so I still use the computer till I buy a super nice one after USB 3.0 hit the streets. 

The problem I keep having by booting of the external HDD is that GRUB keeps saying ```
error: bad filename
```

Can someone here please help me out how to install Kubuntu on a external HDD and make it boot correctly?

Have a nice day. :)

---

### Post by dino99 on 2010-08-08
check it with partedmagic

prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by gordintoronto on 2010-08-08
During installation, specify manual partitioning. There will be a drop-down which shows SDA or HDA, select SDB or HDB instead, which should be your external hard drive.

After installation, set your BIOS to boot from the external hard drive.

---

### Post by Guerreiro on 2010-08-10
If it were that simple gordintoronto I would not ask for help. :) What I did was go and install, specify to use the whole disk of sdb1 (external one) sda1 being the internal one, and choosing advanced install Bootloader /sdb or should it be /sdb1 ?

---

### Post by dougalkerr on 2010-08-10
Guerreiro

I think you need to name it sdb1. I had to give my USB key a number after the letters for it to be recognized. I have not booted from it though. The BIOS must accept booting from external. My laptop BIOS should but, when I set it to do this... it does not. Typical...

Good luck.

---

### Post by Guerreiro on 2010-08-16
haha, yeah Linux is great, but when confronted with these sort of problems I tend to rip my hairs out ;)

---

### Post by Guerreiro on 2010-08-18
This is not solved yet, but what I am going to do is run Katana over at hackfromacave and that works ( I tested it already) :D

---

