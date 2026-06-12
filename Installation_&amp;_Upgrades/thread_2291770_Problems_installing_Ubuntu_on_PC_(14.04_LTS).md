---
title: "Problems installing Ubuntu on PC (14.04 LTS)"
date: 2015-08-22
forum: Installation &amp; Upgrades
---

### Post by shockwave2 on 2015-08-22
Hey guys,

So I've tried to install Ubuntu on my PC but ran into a problem, when it tried to install it, it goes into a black screen and basically tells me:

Could not find the installation files /ubuntu/install/custom-installation ... And it recommends booting into windows and entering chkdsk /r into the console and it should fix, but I have and it did not. Basically I've extracted the iso onto a memory stick and installed from there, and I picked the "help me boot from CD". Did I do anything wrong?

Oh and at the top of the screen it has:

[      4.828355] ACPI PCC probe failed.

Don't know if that will help any diagnosis.

---

### Post by yancek on 2015-08-22
> Did I do anything wrong?

Yes, what you did wrong was:  "I've extracted the iso onto a memory stick".  That won't work. You need to use software specifically designed to create a bootable system.  There is a lot of software of this type but the most common are unetbootin and pendrivelinux.  Just google either term and you should be taken to their site.  It would be a good idea to read some basic info on the site before downloading and beginning.  You will also need to set the usb drive to first boot priority in the BIOS after you have created the bootable usb and before you try booting.  Your computer must be capable of booting from a usb.  You don't mention anything about your hardware, how old it is or which version of windows you have?

---

### Post by shockwave2 on 2015-08-23
Oh that's weird, when I installed 13.04 on my laptop a while back it installed perfectly despite not getting any of the software you mentioned. I'll give it a shot though regardless. My PC is a bit dated, the only thing I've upgraded lately was the GPU, but looking at a bigger overhaul this time as I need to replace the motherboard and, by default, the CPU (The pins are too old or something). Here's my specs:

Windows 8.1
Intel Core 2 Quad 2.5GHz
4GB DDR2
1TB Hard Disk drive
Nvidia GTX 650 1.5GB
550W Power Supply

Thanks for the help

EDIT: The reason why I'm still not using it on my laptop is I had to reinstall it and thanks to UEFI secure boot I couldn't install it after it uninstalled -_-

---

### Post by yancek on 2015-08-23
Reading through your initial post again, the message below is surprising coming from your Ubuntu medium:

> And it recommends booting into windows and entering chkdsk /r into the console and it should fix

Since you have now indicated that you have windows 8 installed and since it uses hibernation by default to make it appear to boot faster, it might be part of the problem.  Turn it off.

---

