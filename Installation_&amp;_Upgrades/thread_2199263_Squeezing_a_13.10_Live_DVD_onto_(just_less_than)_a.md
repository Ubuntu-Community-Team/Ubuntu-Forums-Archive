---
title: "Squeezing a 13.10 Live DVD onto (just less than) a 4G USB flash drive"
date: 2014-01-13
forum: Installation &amp; Upgrades
---

### Post by TBerk on 2014-01-13
(SPECIFICALLY, it's Kubuntu 13.10 but it's not [hopefully] limited to just that ver...)

I have a USB Flash Drive thats labeled 4G but formats out to 3.7G. <-- thats a whole 'nother thread...

I've tried to use Startup Disk Creator & 'kubuntu-13.10-desktop-i386.iso'. The ISO is a Gig in size but wants to unfold onto a DVD sized partition; 4.7G or so.

My searches so far keep getting bogged down in "will it run in 4G RAM?" and/or older versions of xxxUbuntu that _would_ fit onto a 700M CD, let alone a multi Gig disk.

I'm currently scheaming up installing an old version such as an 8.x or 9.x and overwriting the contents of the burned (or at least mounted) ISO image onto the prep'd USB drive. 

PS- I've succesfully burned the image to a DVD, and it boots OK, but I'd like to be able to see if I can get that Live CD/DVD image onto a less than 4G drive.

---

### Post by sandyd on 2014-01-13
Should work - use something like USB Startup disk creator or UnetBootin with the ISO and USB Drive.

---

### Post by Elfy on 2014-01-13
IF you're trying to install to the USB, what minimum space requirements does the kubuntu installer tell you it requires?

Edit - I just installed it in a vm.

After install it's using 3.6Gb , following a apt-get update/upgrade/clean - it's using 3.5Gb

If you are trying to install to a 4GB USB then I'd say you're asking for trouble.

---

### Post by mastablasta on 2014-01-13
if however you want to create a live disk then 4GB (3.7) is more than enough space to create a liveUSB. you will also have plenty space left for persistence.

---

### Post by ubfan1 on 2014-01-13
I use 4G USBs for full installs.  No swap, use ext2, and ignore the warning about not enough space, and the install works.

---

