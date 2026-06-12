---
title: "Error Loading Operating System--Linux Ubuntu--Help"
date: 2008-03-14
forum: Installation &amp; Upgrades
---

### Post by jadehe on 2008-03-14
I am very new to Linux, heard it was pretty good from a friend. So I downloaded Linux Ubuntu and burned it to a CD and installed it. Now everytime I turn on my computer I get "Error loading operating system". I can boot from the Ubuntu CD, but I cant boot to my old disk drive. I try installing Ubuntu again and I get the error "The test of the file system with type ext3 i partition #1 of SCS13(0,0,0)(sda) found uncorrected errors. I was running windows XP before trying to install Ubuntu. My labtop is a Sony VAIO VGN-FE660G. I didn't get any start up CD's with my labtop because the files are supposed to be located on my hard drive. So if I ever needed to I could press F10 when loading to reinstall Windows. But now I can't even get there! So I guess I just need some help on what I should do. Thanks in advance!

---

### Post by gtdaqua on 2008-03-14
what do u exactly want? a fresh ubuntu on your laptop with no other OS or ubuntu alongside XP?
how many partitions did u have? 

In most cases, if you format that partition containing errors (during install) that message will go away. But formatting that partition will obviously mean losing data. But you say its a fresh install and its linux ext3. So there shud be no prob formatting it.

---

### Post by jadehe on 2008-03-14
I have 3 partitions.  One being the ext3, the second is the exteded and third is the linux swap. I would love to still have windows XP.  I don't care if I lose any information that I had previously, I have all my software discs anyways.

---

### Post by jadehe on 2008-03-14
I was told to run 'sudo fdisk -l' and this is what I got.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa17fead9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11787    94679046   83  Linux
/dev/sda2           11788       12161     3004155    5  Extended
/dev/sda5           11788       12161     3004123+  82  Linux swap / Solaris

---

### Post by jadehe on 2008-03-14
I also read to find '/boot/grub/menu.lst' but all I got were 6 files in the /boot folder named

abi-2.6.22-14-generic
config-2.6.22-14-generic
initrd.img-2.6.22-14-generic.bak
memtest86+.bin
System.map-2.6.22-14-generic
vmlinuz-2.6.22-14-generic

So then I ran the following code in the terminal 'sudo vim/boot/grub/menu.lst' and all I got were a bunch of '~' and at the end "/boot/grub/menu.lst" [New DIRECTORY].

Hope this can help in some way! Thank you again

---

### Post by jadehe on 2008-03-14
Would downloading and using a Windows XP Emergency Boot CD help at all?

---

### Post by jadehe on 2008-03-14
Well I finally got Ubuntu running! After the 10th or so time trying to fully install it somehow worked.  Weired!

---

