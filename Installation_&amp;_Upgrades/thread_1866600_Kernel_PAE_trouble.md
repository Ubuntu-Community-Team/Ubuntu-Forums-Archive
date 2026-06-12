---
title: "Kernel PAE trouble"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by stef4001 on 2011-10-21
Hi all,
I installed ubuntu 11.10 on my machine for testing and seeing wath is new;
Now e lot is dissepeart and harder to configurate like groups ans theme's and the al so importing synaptic is not there by default.
But oke i managed to get it the way i wont it to be.

NOW I wand to upgrate my kernel to PAE version to be able to use my 4Gb ram.
I ren sudo apt-get install linux-generic-pae

then sudo update-grube

result: 
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-3.0.0-12-generic-pae
Found kernel: /boot/vmlinuz-3.0.0-12-generic
Found GRUB 2: /boot/grub/core.img
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

So far so good. 

I rebooted and my new PAE kernel was not showing in GRUB   

Google e bit and installed startup manager 

then: gksu startupmanager
result: I only see the kernel not PAE it is in fact not the menu.lst that i created with  update-grube see scrrenshot.

Ok it's clear that i have to different grubs of some type.   

HELP HELP me boot in the PAE kernel.     

I also found script to analyse the boot events with result.txt of my machine.

---

