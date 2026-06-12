---
title: "Ubuntu will not boot with USB drive inserted"
date: 2013-11-07
forum: Installation &amp; Upgrades
---

### Post by ac4rb on 2013-11-07
Hi,
  I don't know if this has been addressed before or if it is a bug. However, I have noticed if I have a USB flash drive inserted in either of the USB ports, and power goes down or I forget and reboot the desktop, it will not boot. the grub goes to a blinking line and never boots. If I turn the desktop off, remove the flash drive, then it will reboot OK. This doesn't seem to happen with my USB printer or other USB devices. Just with a USB flash-pocket drive. It doesn't seem to matter if the drive has pictures or data it still will not boot. I am a little older than most of you so I tend to forget having the drive inserted. When I realize this then I can boot just fine. Is there a reason for this that I am not aware of? BTW, I am running Kubuntu 12.04 on an older 2ghz machine:p

Thanks and God bless 
AC4RB

---

### Post by Johan De Cauwer on 2013-11-07
You *could* change the boot order in bios so that the hard disk always goes first and that solves the problem but why a usb key hangs the system puzzles me also, unless there was an earlier OS on it, now deleted and replaced with pictures or data. What would be expected is a delay, nothing more. Anyhow, if your PC searches for a hard disk first...

---

### Post by erasmusp on 2013-11-08
Hi AC4RB, This is actually "normal" for today's PCs that if your boot device before the hard drive is a USB device in the BIOS settings and you have a non bootable USB plugged in the PC will not boot. We have the same issue here at my work with our Window PCs where the Lenovo PCs are set as USB as the first boot device and if someone forgets their music flash drive in their PC it will not boot and a call gets logged with our IT department... :(

I would give the same suggestion to you that Johan did: Go into the PC's BIOS settings and change the boot up sequence so the the first item is not a USB device...

---

### Post by ac4rb on 2013-11-14
Thanks folks, 
 I will look at the bios, but if I am not mistaken, the bios in my computer doesn't seem to have the option of booting from a USB. I will check and let you know. I hope you are right. I have been backing up some of my photos and sometime forget the flash drive. I hope I can change the bios so this don't happen.

---

### Post by ac4rb on 2013-11-23
Hi Folks,
   I checked and the BIOS doesn't have a boot from USB listed, however, I can press F12 for a boot menu which doesn't mention a USB boot. You would think that even if it did have a USB boot option, if the USB drive inserted did not have a boot or MBR record on it, grub would just ignore the USB drive altogether instead of just stopping. It could be that this is a problem with the BIOS and not the Kubuntu grub. If this is the case, there may be a flash update. which I will be looking for. With the USB pocket drive in, when it tries to boot, it just comes up with a blinking curser and stays there.

---

