---
title: "Grub..wtf!"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by ManyBeers on 2008-10-18
I just reinstalled Windowsxp on my computer yesterday
and installed Ubuntu today using the LiveCD in a dual-boot setup.
I did this once before using the Alternate cd and when the time
came to install Grub I was asked whether I wanted grub installed
into the Master Boot Record or not. I was not asked this time
and so Grub was installed into the Master Boot Record. Is that 
the default action of the LiveCD?

---

### Post by cariboo on 2008-10-18
Yes it is as grub needs to be on the mbr of the first hard drive in your system, in order for it to work.

Jim

---

### Post by ManyBeers on 2008-10-18
> **cariboo907 said:**
> Yes it is as grub needs to be on the mbr of the first hard drive in your system, in order for it to work.

Jim
Ok. I didn't know that I wouldn't be able to select where to
install Grub using the LiveCD. I tried to use my AlternateCd
which I used last time but somehow between then and now the cd got corrupted and would not complete the install. So I used
my LiveCD which was successful. The reason for my inquiry here
is because I was planning on letting ntloader handle boot. I 
have the tools to do it,namely--SystemRescueCD.

---

### Post by ManyBeers on 2008-10-18
> **cariboo907 said:**
> Yes it is as grub needs to be on the mbr of the first hard drive in your system, in order for it to work.

Jim
Ok i have blasted Grub from my MBR using Windows Recovery Consle. I now need to install Grub in Ubuntu's root directory. How do I do that? I have both a LiveCD and the SystemRescueCD.
My setup: scsi sda1(windows) sda2(ubuntu) sda3(swap) sda4(fat32share)

---

### Post by ManyBeers on 2008-10-18
> **ManyBeers said:**
> Ok i have blasted Grub from my MBR using Windows Recovery Consle. I now need to install Grub in Ubuntu's root directory. How do I do that? I have both a LiveCD and the SystemRescueCD.
My setup: scsi sda1(windows) sda2(ubuntu) sda3(swap) sda4(fat32share)

Would somebody mind giving me a hand here? I know this is not a difficult problem to fix. I need to get grub's stage1 into Ubuntu's /.

---

