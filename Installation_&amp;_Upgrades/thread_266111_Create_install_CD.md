---
title: "Create install CD"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by rob2002 on 2006-09-26
I have got a DVD with Ubuntu 6.06. My desktop only has CD drive. How can I burn a bootable CD from the files inside the DVD? I have copied the entire DVD to a folder in the USB hard disk but I could not boot from this as my system does not allow boot from USB.

My system is currently on XP PRO. I tried to use instlux and booted using that but even that looks for a CD-ROM and not the USB drive where all my files are! I also tried the files given in netboot but that looks for a download http site!

Ideally I would like to avoid burning CD, just copy the install files somewhere on the HDD (NTFS) and boot from there and install, is that possible?

Thanks in advance..sorry if already answered.

---

### Post by jharr on 2006-09-26
Booting from a hard drive/usb drive, and booting from cd-roms are completely different. You'll need to burn the DVD ISO image to a DVD-R (alternatively, if you just have a CD burner, download the CD image and burn to a CD-R).

There is no way to take the Live CD copy the data to a partition and have it boot. Bootstrapping on PCs doesn't work that way. If you want to learn about how a PC boots, here is an introduction [http://oldfield.wattle.id.au/luv/boot.html]("http://oldfield.wattle.id.au/luv/boot.html")

Keep in mind that linux can read NTFS, but can't write to NTFS. You'll probably want to resize your partition and give linux 5G or more to use itself.

Sorry this isn't the answer you wanted, but good luck getting ubuntu installed :)

---

