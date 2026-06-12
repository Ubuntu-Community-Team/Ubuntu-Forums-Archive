---
title: "installing on iPod - where to put /boot"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by themoebius on 2006-10-03
I want to install ubuntu as my secondary OS on my old iPod, which I'll be using as an external hard drive for my laptop. The thing is, I don't want it to touch my windows partition because I want the computer to be able to function just fine without the iPod plugged in. Which means I can't install grub to the /boot partition on the iPod because then the computer wouldn't be able to boot without it.

I'm thinking I might be able to create a small /boot ext3 partition at the end of my windows drive which would contain grub and have everything else on the iPod? That way grub could still function and windows could still boot even if the iPod wasn't connected. Would I need to make it big enough to hold the kernel, etc as well or could it just contain grub? And how would it go about booting using two separate physical drives? What are your recommendations?

---

### Post by Ocxic on 2006-10-03
if your bios allows booting from a usb device, then you can put the /boot partition on the ipod i believe.

---

### Post by themoebius on 2006-10-03
Alas, it does not support booting from USB device.

---

### Post by Ocxic on 2006-10-03
boot from floppy or cd to a USB device is possible I think.

---

