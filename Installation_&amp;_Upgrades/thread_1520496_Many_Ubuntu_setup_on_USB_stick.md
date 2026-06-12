---
title: "Many Ubuntu setup on USB stick?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by xerces8 on 2010-06-29
Hi!

Can Ubuntu 10.4 Live be "installed" in a separate directory on an USB stick, so I could have both 32 and 64 bit versions?

I mean to have the equivalent of the CD on the stick, that is the live env, where one can optionally install the system.

Current methods copy the CD root folder to the root folder of the USB stick, so they overlap when more than one Ubuntu is copied.

Ideally all files would under one folder, like ubuntu1004_32/... and then ubuntu1004_64/ for the 64 bit version and ubuntu910_32/ for the older version...

Did anyone do this successfully?

Regards,
David

---

### Post by darkod on 2010-06-29
I'm not sure it can work with just separate folders. I did it by splitting the stick to different fat32 partitions.
I made the partitions 750MB (the ISOs are approx 700MB), then unpacked the ISOs to the separate partitions.
For booting at that time it was easier to use GRUB4DOS and do it from windows (I had little experience with grub). Grub1 also can use the UUID of the partitions, so my entries in menu.lst are like:

title Name
uuid xxxxxx
kernel
initrd

That works fine. I have Lucid 64bit and 32bit like that, plus CloneZilla and System Rescue CD. I also have another partition for the development version but still haven't put Maverick there.

---

### Post by alterpinguin on 2010-06-29
you should search for:

multiboot usb

one link (only one.)
> [http://www.boiselug.org/node/66](http://www.boiselug.org/node/66)

has links to using iso-boot-files like those from ubuntu-10.04
(and others too) to build a grub2-usb-booting setup
from here
> [http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)

you only need to do the grub-install to the usb and
copy the iso to the usb... and create the right grub.cfg
there to enable the booting of it.

-- there are more links, if you search, with decent step-by-step
explanation how to partition, format, install-grub, create the grub.cfg file ...

---

### Post by darkod on 2010-06-29
Maybe I just didn't have good guides, but booting from ISO won't work unless you have lots of spare space. At least it didn't work for me.
The ISO needs to be unpacked during the boot, and maybe even emulated (don't know for sure), so it will just report an error instead of boot.

The method I described with unpacked files, can work even if the stick is 100% full because the files are already unpacked.

With a 2GB stick I was able to boot directly from one ISO, but because I also wanted both the 64bit and 32bit version to be available, once I copied both ISOs to the stick they took 1.4GB. When trying to boot either there was some error about insufficient space or similar (don't remember it exactly any more).

But you can try either way and see what works best for you.

---

### Post by snowpine on 2010-06-29
Ubuntu 32-bit will run on both 32- and 64-bit hardware. Multibooting is not necessary in this case.

---

### Post by C.S.Cameron on 2010-06-29
Great script and instructions for Multi Boot USB:

[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

---

