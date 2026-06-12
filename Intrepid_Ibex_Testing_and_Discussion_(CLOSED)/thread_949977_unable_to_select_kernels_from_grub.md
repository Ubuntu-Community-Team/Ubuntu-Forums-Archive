---
title: "unable to select kernels from grub"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Richard-g8jvm on 2008-10-16
Hi

since upgrading to 8.10 from 8.04 I'm unable to select any of the downloaded kernels .this is applicable to 2.6.26 & 2.6.27.

I'm still using  2.6.24-21-rt , the restricted modules for 2.6.26 RT dont seem to be available as they are greyed out on the upgrade manager.

I need the RT kernel for the audio apps I run, but I'd like to use the later kernels in case the module for my 1GB NIC has been fixed.


On selecting one of the later kernels from the grub splash it returns error 15 cant find file.
Yet update-grub shows:-
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-7-server
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /vmlinuz-2.6.26-1-rt
Found kernel: /vmlinuz-2.6.24-21-rt
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done



What have I missed


This machine is an AMD 64 dual core +4400, 8 GB of RAM


TIA


Richard

TIA

---

