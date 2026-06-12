---
title: "Unable to boot Ubuntu Studio 18.04"
date: 2018-07-10
forum: Installation &amp; Upgrades
---

### Post by tedthetrumpet on 2018-07-10
Had ubuntu studio working ok on dell laptop, but decided on a clean install of 18.04. Managed to install I think, but can't get it to boot. Tried boot-repair, which shows an error:

paste.ubuntu.com/p/4ZVGMyZGmr/

I installed this under a 'legacy' option rather and UEFI, as I can't seem to get the machine to boot from the usb disk under UEFI. Last time around I had similar problems, but did eventually get it booting under efi, not sure how.

When I try to boot I get 'no boot device found'. Booting from the usb drive, I can see in gparted that I have only one main partition, no boot partition at all. There are no other operating systems on the machine, and I don't need any.

Suggestions?

Thanks!

---

### Post by tedthetrumpet on 2018-07-11
I can't see how to mark this as solved, but it is, sort of. More of a work around. I can't give a full account of the steps: tired and confused, been at it for hours! Broadly outline:

* booted from an install disk on an sd card rather than usb: not sure if that really made any difference
* used legacy boot to wipe disk and install system
* would not boot
* used gparted from install disk to add an EFI System Partition (ESP)
* reinstalled from legacy
* used advanced settings in boot-repair to change the grub location to the ESP
* finally now machine would boot UEFI into either the SD card, or, more importantly, the new system!


Reference pages I used:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by #&amp;thj^% on 2018-07-11
Thanks for sharing your method, very helpful to others.
And you can mark this Solved by going to your first post#1 under "Thread Tools" and select Solved. :)

---

