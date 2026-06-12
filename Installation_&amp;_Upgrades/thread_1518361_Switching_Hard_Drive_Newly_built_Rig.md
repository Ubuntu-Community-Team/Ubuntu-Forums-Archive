---
title: "Switching Hard Drive Newly built Rig"
date: 2010-06-26
forum: Installation &amp; Upgrades
---

### Post by deba on 2010-06-26
Hi,

I have just built a new machine and want to transfer my hard drive over to it, can i just plug it in and power up?, will ubuntu 10.04 detect the new hardware and reconfigure. if not whats the best way to backup the data and re-install.

Old Rig details:

AMD Athlon 64 3200+ cpu
1gb ram
Nvidia 5200
ASrock VM800 Systemboard

1 x IDE 80gb (Boot/home)
2 x Sata 32gb in Raid0 (Data Drive but currently empty)


NEW Rig Details:

Asus M4A77TD Pro Systemboard
AMD Athlon II X2 2.9ghz dual core cpu + Fan
ATI Radeon HD 5450
1 x 2GB Ballistix DDR3 PC3-10600 Ram
Mid Tower Case & 500W PSU


Any help appreciated

---

### Post by dabl on 2010-06-26
Probably, if you set the BIOS correctly (boot the right drive first), it will boot and load the kernel, but with different video cards and the different motherboard there are liable to be multiple glitches.  It will take considerable time googling and tweaking to work your way through installing a different video driver, resolving any power management issues, never mind motherboard sensors and stuff like that.  If it were me, I'd figure out a way to back my data up on some other device, then make a new OS installation on the new drive in the new hardware.  That way you'll take advantage of the hardware detection capabilities and a lot of the configuration will be done automagically.  I think you'll save time doing it that way.

With a Parted Magic Live CD, with which to do your partitioning on the new drive first, and then a *buntu Alternate Install CD, with which to install your OS on your chosen partition, I think you can be up and running productively in about 45 minutes. Going down the other path, it's a poker game when you resolve the last glitchy issue.

That's my two cents' worth.  :lolflag:

---

### Post by dandnsmith on 2010-06-26
On the other hand, you might have my experience when I did the same operation - the linux OSs just adjusted themselves without any significant tweaking.
I agree that some graphics cards can be suffucuently different to cause problems.

---

### Post by cascade9 on 2010-06-26
If you remove the nVidia drivers, it should start fine. When I've changed cards without removing the binary driver, I dont get X working. 

RAID could complicate matters as well. 

I'd probably just do what dabl suggests, and reinstall on the fresh drive.

Edit- I've got no idea why you use a parted magic live CD to do the partitioning dabl. Is there some logic behind this that I'm missing?

---

### Post by deba on 2010-06-26
Thanks guys,

I just installed the boot drive into the new system and it detected the new gfx card all ok so all is well.

now i want to clone an image from the 80gb ide to a 320gb sata drive so i can get rid if the ide drive from the system totally. I will try and use g4u for this now.

---

