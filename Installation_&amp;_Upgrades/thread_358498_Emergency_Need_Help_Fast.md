---
title: "Emergency Need Help Fast"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by motermouth on 2007-02-10
Alright...I currently have a windows XP Media Center edition (Gateway) computer. It has a200 GB harddrive and I have the XP media center edition duel booted with ubuntu. I decided that I was going to undo the duel booting because I found a program that lets you make a virtual computer and everything so I inserted the Linux live cd (Ubuntu) I opened gparted and deleted the 2 linux partitions and then resized my windows one so that it would take up all of the space other than my windows recovery drive. When I was done I restarted and removed the disk like it said but now it won't load the grub. I can't load windows. Does anyone know how I could re install a grub file or what ever windows uses and make it so that it automaticly runs windows with out me pushing anything like a factory computer comes? Thanks so much!!!

---

### Post by Bil-E-daKid on 2007-02-10
Hi there,

Unfortunately, in removing the linux partitions, you've removed essential parts of the grub bootloader.

GRUB is a linux thing, not a windows thing.

What you now need to do is install the windows boot loader back into the boot sector of your hard disk (the bit of the disk where parts of GRUB are started from).

To do this, it's likely easiest to boot from your XP CD and find your way into the recovery console of windows XP.  From there, you should be able to run a command like 'fdisk /mbr' which will write the Windows boot loader code back onto the hard disk.

Other options are to use some kind of recovery CD (like the ultimate boot cd - ([http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")) to re-write the windows boot loader code.

HTH
Bil-E-daKid

PS For something completely out of the box, you could just wipe windows, install linux on your whole drive and install Windows into a virtual machine inside linux rather than linux in a virtual machine inside windows.  In my experience, windows on linux works better than linux on windows.  :-)

---

### Post by housam on 2007-02-11
Fix the MBR using windows installing CD >> recovery console.

---

### Post by motermouth on 2007-02-11
Thanks although i forgot to post that I've already done that so I fixed my computer

---

