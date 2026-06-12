---
title: "missing operating system"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by omnomnom1 on 2010-12-19
I've followed each and every single step to make a bootable usb drive, but when I try to boot from it, it says "missing operating system".


I'm using a 1008HA eee pc with win 7 starter and I'm trying to install ( by booting from a usb device ) ubuntu-10.10-netbook-i386, but unfortunately, even after correctly adjusting the boot priority in the bios to ensure the usb flash drive is 1st and even by pressing "Esc" to select my usb flash drive to boot from, I get the "missing operating system" error, then it boots win 7 from the hdd.


the problem isn't my netbook since it doesn't boot either on my pc. As for the usb flash drive, I used the suggested software "Universal USB Installer" to make it bootable.


If I forgot any type of crucial information, let me know, I'll happily add them.



Bear in mind that I'm a linux noob.

Thanks.

-Dan

---

### Post by dabl on 2010-12-19
Although it is not precisely responsive to your question, if you give this guide a review, especially the "dd" part, I think you can raise your knowledge level up to where you might be able to beat that USB stick into submission: [http://kubuntuforums.net/forums/index.php?topic=3107512.0](http://kubuntuforums.net/forums/index.php?topic=3107512.0)

Also don't underestimate the importance of the BIOS in that netbook -- you have to enable "boot from USB", you have to include the USB stick in the list of "hard drives", you have to set the USB stick first in the "boot sequence", etc. etc.

---

### Post by omnomnom1 on 2010-12-19
thanks for the advice, Ive done what you mentioned without success so Im going to simply install it inside windows. It might not be as good but itll have to do.

---

### Post by jamesbarnhill on 2011-01-06
Anybody have a solution for this?  I've installed Ubuntu more times than I can count on everything from desktops to netbooks to VMs using USB and CD, but I don't understand why the new (-ish) netbook remix won't boot at all.  I've tried UNetBootIn, the included USB-Creator and the Universal USB installer; on both of my netbooks it ends up with "operating system not found."  It's not the ISO as I can run it just fine in a VM, and I've also md5'ed it.  Sorry, I don't have any logs as it won't even boot. ;)
I've tried it on a Dell Mini 9 and 10v.
Thanks, 
~James

EDIT: Forgot to say that I've also tried the dd method using Snow Leopard on my Macbook Pro. Same thing happens.

---

### Post by djluvsgod on 2012-06-02
I'm bumping this thread because I'm having the same problem. I've tried booting both Ubuntu 12.04 and Fedora from usb sticks on my laptop. I have done this before with this same usb stick and laptop. So I'm really baffled as to what is going wrong.

---

### Post by Rex Bouwense on 2012-06-02
My ASUS EeePC 1000h recognizes the flash drive as another hard drive so the BIOS must be set to boot from the USB flash drive "hard drive" ahead of the computer hard drive.  Merely setting it to boot from a removable USB device will not cut it some times.  You have to look closer at the hard drive components.

---

