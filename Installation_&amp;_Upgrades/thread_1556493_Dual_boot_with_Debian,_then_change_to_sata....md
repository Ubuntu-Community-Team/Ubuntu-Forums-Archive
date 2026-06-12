---
title: "Dual boot with Debian, then change to sata..."
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by cardinalx on 2010-08-19
Hello,
 
I installed Debian on my PC and then installed Ubuntu. This worked fine and I could dual boot between the two. The PATA disk was /dev/hda on debian and (I think) /dev/sda on Ubuntu.
 
I copied the entire disk to a sata disk using dd from knoppix and put the PATA one to one side.
 
Now the Ubuntu comes up fine but when I boot debian, it complains about references to /dev/hda1, which is present in grub - root=/dev/hda1. Debian now expects sda references rather than hda references.
 
My question is: **How do I persuade Ubuntu to write /dev/sda1 to the bootloader rather than /dev/hda1 using grub-mkconfig?**
 
Thanks for all constructive advice given.
 
Hal.

---

### Post by quixote on 2010-08-21
Just a shot in the dark, but is there a reason why you need to use grub-mkconfig?  Wouldn't update-grub do what you need? (I.e. "sudo update-grub" in a terminal.)

---

