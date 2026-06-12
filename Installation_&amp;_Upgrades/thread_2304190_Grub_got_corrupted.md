---
title: "Grub got corrupted"
date: 2015-11-24
forum: Installation &amp; Upgrades
---

### Post by charif2 on 2015-11-24
Hi, I am new to this forum so please bear with me. 
I was try to do some upgrades and somehow I think Grub got corrupted. I no longer can boot into my Ubuntu Partition. 
I tried to follow the link in here
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

but the recommended action seems to go onto an endless loop.

Here is a link to the Bootinfo summary of boot-repair.
[http://paste.ubuntu.com/13490592/](http://paste.ubuntu.com/13490592/)

I would really appreciate any help.

---

### Post by yancek on 2015-11-24
You're using UEFI and you seem to have the correct files for both Ubuntu and windows on sda2.  Odd thing is you also have an EFI partition on sda3 which certainly isn't standard.  Also, if you look at the grub.cfg file there is no menuentry for Ubuntu.  That's pretty bizarre!  Have you tried the recommendations listed at the bottom of the boot repair output?

---

### Post by oldfred on 2015-11-24
If you go into the UEFI or use one time boot key like f10 or f12 can you boot Ubuntu?
Not sure if grub issue or UEFI settings? You show 0016 as first boot option which looks like an external drive?  
Boot0016* USB HDD: GOODDRIVEFR    

Your link to repair instructions is mostly for older BIOS, but Boot-Repair works for both BIOS and UEFI if booted in correct mode which you did do.

Boot-Repair also has an advanced mode where you can totally uninstall grub2 and reinstall it. Sometimes that fixes grub issues.

---

### Post by charif2 on 2015-11-29
@oldfred, yes, that was a usb drive that I run Ubuntu Live from it (GOODDRIVER), cause ubuntu stops booting, so I had to boot from a usb drive. I will try your recommendations, but when I use recommended repair it just takes very long time to repair.
@yancek, the recommendations has something like: "[COLOR=#000000]reinstall the grub-efi-amd64-signed of sda8", do you have any idea how to do that? thanks. [/COLOR]

---

### Post by oldfred on 2015-11-29
In Boot-Repair you just accept the auto fix. That may or may  not be enough.
Often you have to go into advanced options and choose the full un-install/reinstall of grub. Make sure Internet is working as it needs to download a new copy of grub.
Be sure you have booted in UEFI boot mode to install the correct version of grub. If you boot flash drive in BIOS mode it will install a BIOS boot version of grub.
In UEFI boot menu you should have two boot options for GOODDRIVER or flash drive. 
One usually is clearly UEFI:Gooddriver and the other is just Gooddriver (which then is the BIOS boot mode).

---

