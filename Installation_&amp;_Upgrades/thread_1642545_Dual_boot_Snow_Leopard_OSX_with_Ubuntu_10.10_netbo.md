---
title: "Dual boot Snow Leopard OSX with Ubuntu 10.10 netbook"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by gringoben on 2010-12-10
Hi

Perhaps I should have put this in the apple users section, but I am not an apple user. I am using a MSI WIND U100 running OSX snow leopard retail (GUID/GPT  - boots using Chameleon). 

I've been feeling guilty preaching open source while not currently practising what I preach so finally downloaded ubuntu 10.10 (netbook version) and using unetbootin I made the ISO bootable on an external USB drive.

I already had an empty 40gb partition which I'd intended to dual boot linux on so I went ahead and booted from the external and installed ubuntu. During the install I divided up the 40GB with 3GB for swap and 37GB as ext4 mount point /

Anyway, it installed and rebooted and loaded ubuntu fine using the default option in the auto installed GRUB. However, although the menu show my OSX it does not boot (ARGH!). When selected there is disk activity for a few seconds and then nothing, just blank screen.

I'm praying that I just need to tinker with grub or something to get my OSX back...

please help.

(PS> the insanelywind.org forums have loads of info on dual/triple booting these hackintosh netbooks but mostly involving windows XP or windows 7 rather than ubuntu and also mostly about earlier OSX varieties which booted onto MBR partitions rather that GPT. I've searched the web for half a day without coming up with an answer.)

---

### Post by sent17inel on 2010-12-16
I want to do this also. Please tell me what you find. I'm the other way around though. I'm mostly interested in osx for video editing. My sugestion would be to format over those 40 gig's you had with a gparted live cd or usb, and use a restore cd or whatever osx people use to fix your mbr. I think maybe you NEED chameleon? Anyways that would be my first try if I needed my Mac install back in a flash. Good luck!

---

