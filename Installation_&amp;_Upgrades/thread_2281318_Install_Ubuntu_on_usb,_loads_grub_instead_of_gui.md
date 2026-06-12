---
title: "Install Ubuntu on usb, loads grub instead of gui"
date: 2015-06-06
forum: Installation &amp; Upgrades
---

### Post by terra2 on 2015-06-06
Hi everyone, I have been out of the ubuntu world for quite some time and now I'm a little lost.

So I installed ubuntu 15.04 onto a usb flash drive via unetbootin using iso.

Everything went well and I booted up the flash drive just fine. However once the boot began it took me to the grub command line.

I attempted typing boot but all I got was that the kernal must be loaded first.


I am using a friends computer with windows 8.1 but I can not make changes to it, So I was attempting a usb version of ubuntu.


Any ideas on whats going on and how I can get the GUI to actually load?

Thanks for any help. 

-Terra

---

### Post by ajgreeny on 2015-06-06
Do you actually mean an installed OS of ubuntu on the USB or it a live system?

It is possible that you will not be able to run it on a machine that has Win 8 as the machine will be most likely running in UEFI mode and you will have to boot the USB in that same mode.  Give us more info about what you see when you boot the machine with the USB attached.

---

### Post by oldfred on 2015-06-06
Do not run Boot-Repair, just the summary report:

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by terra2 on 2015-06-07
Thanks for your help but I managed to figure it out.

Using universal usb installer I made a install usb drive on a 4GB flash drive, then in bios I disabled the harddrive so that when I installed ubuntu (targeting a 16gb flash drive) it had to install grub to the usb, then reenabled the hdd with windows.

I now have a bootable linux full os including grub on my usb drive. 

-Terra

---

