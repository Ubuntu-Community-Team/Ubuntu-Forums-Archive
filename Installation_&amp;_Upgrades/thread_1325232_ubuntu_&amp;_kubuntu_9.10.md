---
title: "ubuntu &amp; kubuntu 9.10"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by orangeworx on 2009-11-13
Hey all,
I posted a couple days back about not being able to boot a fresh install of 9.10. After several attempts at re-installing and getting the same error (error: no such device: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx). It seemed that GRUB wasn't installed properly or something I can't explain as of yet due to my limited *nix knowledge.
Oh yeah, before I forget, I used unetbootin to create the bootable usb key.
So I decided to try something else, started unetbootin and selected the option to download an image rather than load one I had downloaded. I did that for kubuntu 9.10 and it created my usb key after the download.
Booted from the flash disk, installed by choosing to keep previous os (ubuntu 9.10) and have the partition manager do the default (split the drive in two) at the grub screen, chose to install to sda1, it was sda or sda1.

system booted, got the error: no such device: the letter/number series flash for a second and the GRUB menu appeared with the kernel options... after a couple of reboots, I realized, GRUB was only booting ubuntu which wasn't bootable before!!!
I thought I'd just trash everything and fresh install kubuntu on formatted entire drive and guess what? Same error: no such device!!!

Does anyone have any ideas on what the blazes is happening? Could it be an issue with unetbootin?

---

### Post by orangeworx on 2009-11-13
original thread with no responses 
[here]("http://ubuntuforums.org/showthread.php?t=1321882")

---

### Post by caue.rego on 2009-12-07
I'm sorry, I have no idea what your problem might be. Didn't even know what is unetbootin or why you insist on using it. I just didn't want you to go unreplied again, and I hope to hear you got this solved already! :D

If not, well, in your place I would start by not using that thing. Can't you just record a CD? Are you only able to grab Ubuntu from a windows machine without any CD recorder?

I have no experience on creating USB disks with ubuntu from windows, or why you could be having those issues. :(

Granted, I had some problems with grub2, launched on Ubuntu 9.10 karmic... Maybe you should look after that.

Best of luck!

---

### Post by presence1960 on 2009-12-07
did you choose "check disk for errors" at the menu screen prior to trying to install Ubuntu?

---

