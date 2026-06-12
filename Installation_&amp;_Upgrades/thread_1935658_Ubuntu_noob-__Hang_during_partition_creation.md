---
title: "Ubuntu noob-  Hang during partition creation?"
date: 2012-03-04
forum: Installation &amp; Upgrades
---

### Post by ryoaska1 on 2012-03-04
I'm trying to install Ubuntu 11.10 64-bit side by side with the existing windows 7 installation on my laptop.  It's a Toshiba Satellite P500 with a core i7 q740.

I select 'something else' for install type, and create an ext4 root partition, an ext2 /boot partition, and swap.  I also set the bootloader to the boot partition because I want to use bcdedit to chainload from the windows bootloader.

When I start the install the process seems to just hang (just the install process) indefinitely.  I waited overnight and nothing changed.  When I try to run the installer again it shows an ext4 partition on the drive I selected, but not the correct size or set as the root mount point.  There's no /boot or swap space the rest is still free space.

I'm wondering if this just be a bad burn of the liveCD, or if that hang could indicate some common install mistake.

EDIT:
not sure if there is a problem with the initial way I tried to install, but I did finally read that windows bootloader only loads 2 OSs on the same physical drive, which is not what I wanted.  Instead I only created a root and swap partition and chose the volume of the drive I was installing on for the bootloader instead of creating a /boot partition and using that.  Install went smoothly, and I just let the BIOS choose which drive to boot from.

---

