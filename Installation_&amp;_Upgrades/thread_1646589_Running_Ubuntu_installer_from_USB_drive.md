---
title: "Running Ubuntu installer from USB drive"
date: 2010-12-16
forum: Installation &amp; Upgrades
---

### Post by Ploink on 2010-12-16
I've been having some problems getting the Ubuntu (9.10 ?) installer to start on my desktop computer. I have created a bootable USB stick using usb-creator (from my laptop), and am able to boot from it on my laptop. However, I get a "Boot error" message on my desktop when I tell BIOS to boot from the USB stick.
I'm not sure this is related, but I tried to boot the Ubuntu install CD from my external USB CD Drive, but nothing happened - it just proceeded to boot from my primary hard drive.
I have enabled USB boot in the BIOS, but it doesn't list the USB stick as removable media. It lists as a hard disk drive instead. I can't find the external CD Drive on any of those lists.

Can anyone help with this?

(Also, the laptop is dual-booting and has grub installed. The desktop has a single OS - WinXP (and hence doesn't have grub installed).. I don't know how this should affect the USB boot though)

(I don't think this is a problem with only the Ubuntu installer, but I'd like a confirmation on this)

---

### Post by C.S.Cameron on 2010-12-16
Have you tried setting the usb drive as your first hard drive in Bios?
That is what I do.
Sometimes hitting F10, etc, will give you a choice which drive to boot.

---

### Post by Ploink on 2010-12-16
Yes, I've selected the USB as the first hard drive in BIOS. The "boot error" shows up only after trying to boot from USB. Hitting return on the screen with the boot error causes the system to boot from the second choice hard drive (which in this case is my main hard disk drive). 

And no, although I've seen the F10 key to choose boot device on my laptop, I don't think that option's available on this machine.

---

### Post by amsterdamharu on 2010-12-16
First let's check what bios settings you need, download tinycore and unetbootin. I always have good results using unetbootin even on the buggier Linux version.

Unetbootin is easy, you select an iso file (local file) browse to the downloaded tinicore iso and make the usb.

Once you get it booted you can keep the settings and try unetbootin browsing to the downloaded Ubuntu iso. This because the Ubuntu iso is a lot more complicated than tinycore so you can be sure it's not the bios settings that's messing it up.

---

### Post by C.S.Cameron on 2010-12-16
Plop boot manager might be worth a try if nothing  else works.

---

