---
title: "boot ubuntu livecd from hard drive?"
date: 2007-08-18
forum: Installation &amp; Upgrades
---

### Post by ./confused on 2007-08-18
Hi,  

I have a fujitsu lifebook b2610, and it has no cdrom drive and no ability to boot from usb. I've tried to install ubuntu on its hard drive from a gateway laptop that I have, and it's been limtedly successful. The touchscreen works, although it needs calibration, the wireless worked, everything worked except for desktop effects (I'm not even sure that its rage mobility can handle it... but...) I played around with video drivers and scripts and it's fubar. 

Anyways my progress so far: I've used my gateway to delete my root partition and I've copied the entire cd to it. /boot is as i was; and grub is installed and working. I know that the kernel and initrd are to be found in /casper, but i'm at a loss as to where direct grub to as for the root and all the other kernel params... can anyone help?


Thanks, 
Brewer

---

### Post by ./confused on 2007-08-18
BUMP

Anyone? I've been tailoring the grub.conf and it's not been successful. So far I have:

root (hd0,6)/casper
kernel /casper/vmlinuz  
initrd /casper/initrd.gz
boot

And, whether or not I specify 'root=/dev/sda7', the booting process stops at this:
[  9.332000] hda: hda1 hda2 hda3 < hda5 hda6 hda7 >

I'm still trying little tweaks, but nothing is working. anyone please?

---

