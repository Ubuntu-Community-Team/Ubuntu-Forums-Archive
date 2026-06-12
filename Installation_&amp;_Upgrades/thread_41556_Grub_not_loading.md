---
title: "Grub not loading"
date: 2005-06-13
forum: Installation &amp; Upgrades
---

### Post by Schoey on 2005-06-13
I (think) I have loaded Ubuntu 5.04 correctly but  when I try to boot it I get the message  Grub loading Stage 1.5 Grub loading please wait  Error 18 
Hope someone can help.    

 Schoey

---

### Post by alexc on 2005-06-13
I am getting this exact error right now. It means that the BIOS cannot read the complete GRUB loader because it is out of reach on the harddrive. The normal solution is to make a partition at the start of the drive that the bios can load for booting, and some people say that changing their bios settings to a large HD or booting in "Normal" mode works. But I dont have these options. Search google for more info.


My predicament:


I have a windows install for the first 32GB of my 36GB HD and just put Ubuntu at the end. I need files back from windows, and I dont know how to load it again now that Grub replaced the previous boot loader and I dont have a Windows XP Pro CD or even a floppy drive on my laptop. The only IBM option is to restore the factory defaults. But I dont want to loose my stuff.

Anyone have any ideas how I can reload windows, backup my stuff, and then go forward?



PS:  I really like the ubuntu live CD and this is my first real experience with Linux, other than putting it on my iPod which initially got me interested. Please help!

---

### Post by alexc on 2005-06-13
[http://ubuntuforums.org/showthread.php?p=211841#post211841](http://ubuntuforums.org/showthread.php?p=211841#post211841)


SOrry didnt read enough.

hope that helps. fixed my problem on my thinkpad!

---

### Post by mingus on 2005-06-13
The problem with the boot loader location being beyond what can be read happens when either the BIOS cannot support the size of drive installed (but yours is a stock system, right?) or its the infamous 1024 cylinder problem.  Don't remember offhand is there is now an LBA option to use with grub that overcomes this; for sure this option is avail with LILO.

If there is absolutely no way to a obtain Windows bootable CD, and since you have no floppy, you are left with using a Linux live-CD or the Ubuntu install CD in rescue mode.  You can use that to either re-install grub or install LILO instead.

---

