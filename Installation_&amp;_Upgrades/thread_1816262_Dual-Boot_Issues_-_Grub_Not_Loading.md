---
title: "Dual-Boot Issues - Grub Not Loading"
date: 2011-08-01
forum: Installation &amp; Upgrades
---

### Post by gg4gg4 on 2011-08-01
I have been using Ubuntu for a while now on a netbook and even installed it on another pc, but I never tried dual-booting before...
 
-
 
I just recently built a pc (my first custom build), and I'm having major difficulties getting a dual-boot running with Win 7 and Ubuntu 11.04.
 
I'm trying to install these on one hdd.
 
I don't know if it's a hardware issue or not, but the bios doesn't seem to like grub... I installed Win 7 first, and before installing Ubuntu on a separate partition, Win 7 would boot up fine. (Although, sometimes the bios would ignore my key presses for entering the bios menu or the boot-menu... When I only had Windows installed.)
When I turn on the pc, I mostly get a blinking cursor, with no messages at all. Nothing would boot at all, grub doesn't seem to load, and no OS would load by default. This would even happen sometimes after I set CD-ROM as the first item on the boot order list, trying to boot from the Ubuntu liveCD since there was no way for me to reach either of my installs on my HDD. 
 
I tried several suggestions I found online, and nothing seems to help.
I even tried both grub 1.99 and grub 0.97, but still not much luck, (Although, grub legacy seems to load slightly more often...)
I don't really want to have to resort to using Ubuntu through a VM, but it looks like this is the only option left...
Is there some way I can dual boot with something other than grub?
 
-
 
Here's something I noticed after trying Ubuntu a few times. I'm not sure how relevant this is to my issue but, at times, on booting from a liveCD, I see several lines appearing that say something like "over-current change on port 2" should I be worried about this? Is something wrong with my mobo or psu?
 
Another thing and this was before installing Ubuntu, when I boot up the pc, my keyboard is sometimes disabled until it's re-plugged in to a usb port. Maybe this has something to do with over-current charge? I'm just trying to figure out if anything needs to be replaced... I got sick of having to replugin the keyboard since I was constantly restarting the pc, so I started using a less fancy keyboard and it seems to be recognized most of the time (sometimes the bios would still ignore my boot-menu key press attempts).
 
Any help here would be greatly appreciated! Thanks!

---

### Post by zero244 on 2011-08-01
That is common for a usb keyboard to be delayed at certain points in the boot process. 
If you have PS/2 ports and a usb adapter you could plug into those and have keyboard control almost immediately

As far as not finding the grub2 loader, there is a program called Super Grub2 Disk you can download.
Do a google search to easily find the web page.
It is a small iso file that is bootable.
You need to burn this iso to a cd, to boot from.
After you boot from the cd you tell this program to look for any grub2.cfg files.
It will find them and load the grub loader.
This program wont actually install your grub2 boot loader but that is simple to do once you've booted up.
After you boot into Ubuntu you can then install the grub2 loader into the boot partition probably sda.

There is a iso for standard grub and grub2, make sure you use the correct one.

---

### Post by oldfred on 2011-08-01
I would review BIOS settings. You should at least have a setting for USB keyboard & mouse. My system would work without the setting except in grub. Windows & Ubuntu seemed to ignore BIOS??

Not sure if there may be other BIOS settings that can change things, but I would review those also.

---

