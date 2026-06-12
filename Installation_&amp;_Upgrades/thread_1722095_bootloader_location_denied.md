---
title: "bootloader location denied"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by holborn77 on 2011-04-05
hey all

So, I'm trying a triple boot and I have a problem
with ubuntu 10.04.2 desktop i386 lts (live usb)when it comes to choosing the location of the bootloader.

The partitions of the hard drive are:

/dev/sda/
free space - [0 MB]
/dev/sda1 - hfs+ [209 MB (mac efi partition)]
/dev/sda2 - hfs+ [35 GB (Mac os)]
free space - [134 MB]
/dev/sda3 - ntfs (win7)
/dev/sda4 - fat32 [25 GB (partition to install ubuntu)]
free space - [0 MB]

So anyway, I choose /dev/sda4 > delete > add 3 partitions:
sda4 > 2gb swap
sda5 > 12gb ext4 / 
sda6 > 11gb ext4 /home 

I go on and when it comes to the point when hitting advanced
I can choose the location of the bootloader it doesn't let
me proceed (OK button is grey) with /dev/sda5 selected(where / is).

What's the deal? I need the bootloader there and not at /dev/sda
cause it'll mess the triple boot. I had tried this with ubuntu 10.10 desktop before and there was no problem.any ideas?

:confused:

---

