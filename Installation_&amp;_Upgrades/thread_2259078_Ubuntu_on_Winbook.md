---
title: "Ubuntu on Winbook"
date: 2015-01-01
forum: Installation &amp; Upgrades
---

### Post by jeff111 on 2015-01-01
Hi I got one of those cheap microcenter winbook tablets and I was wondering if I can install Ubuntu on it? Can I use it on a touch screen and does it have a virtual keyboard?

---

### Post by MAFoElffen on 2015-01-02
I don't see why not-- Intel Atom Processor. Others have installed Linux distro's on them. Test would be if it boots a LiveUSB Image and test how it does, right?.

---

### Post by Eric_M on 2015-01-05
> **jeff111 said:**
> Hi I got one of those cheap microcenter winbook tablets and I was wondering if I can install Ubuntu on it? Can I use it on a touch screen and does it have a virtual keyboard?

It should work, but it uses a 32-bit UEFI, so you will need to drop a custom UEFI bootloader onto the bootable media.

Keep in mind that I don't know if the touchscreen has proper drivers (or might require some hacking).  Also, wifi drivers are hard to get working.

If you still want to take the plunge, make sure you have a keyboard and mouse in the USB port, and a USB stick (with a 32-bit UEFI loader) to boot.

Careful of the "recovery" partition of Windows, as it's needed for Windows to continue booting, if you decide to try dual-boot.  There is also some Grub headaches due to the 32-bit UEFI, although YMMV on that aspect.

---

### Post by MAFoElffen on 2015-01-05
Welcome to the Ubuntu Forums Eric. (Noticed that was your first post...)

---

### Post by Gordonbp531 on 2015-01-06
I have a Toshiba Encore, also Win 8.1. I can't get it to boot from anything other than a Windows 8 recovery USB and there doesn't seem to be any way to get into a conventional BIOS setup screen either....so you may not be able to do anything with it at all.

---

### Post by mtndrgon on 2015-01-08
Ok first post.. BUT. You can get ubuntu on the winbook.. sorta. There is no communications to the efi from the kernel, no processor control or battery monitor. not to mention no wifi or bt as there is no support for the intel wireless adapter or sdio in general.. see previous lack of comm to the motherboard from the kernel. Boot partially id's the dev and leaves a partial port open for bt but then de initializes it due to a power issue. ... i tried for about 60 hours to get it running and tried versions of 7? kernels.. including 3.19 betas all down to 3.13.. no joy. Over heating and almost cooked the processor one core at a time. oops. No touchscreen.. you need the 10inch keyboard or a full hub w/ keyboard and a generic wifi dongle.. even then you will get serious IO errors through the usb bus as you are going to have to run initial boot off your modified liveusb. And thats just the start of the fun. .. so fedlet installs.. worse IO errors post install HOWEVER you get battery data and a fully inverted and reflected touch input single point only.. sometimes. I am 2 weeks into this and well.. crap

---

### Post by mtndrgon on 2015-01-08
side note.. if anyone can help.. Intel will not release any code for the baytrail processor firmware. wifi yes.. though the versions that require the hci com to the sdio are what i am having issues with.

---

