---
title: "Duel bootwith windows xp"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by huntintim on 2010-11-19
I installed ubuntu 10.10 in m machine along side win xp. It booted several times. but it did not recognize my wireless network adapter. so we followed the instructions to install and use the windows driver for it.cold not get it to work and decided to reboot. now the machine boots to the dual boot screen and will not go any further. nor will the keyboard work to select which os to boot. the machine just completly hangs up i cant even get in to bios.

---

### Post by huntintim on 2010-11-19
i for got to mention it will boot into the installer on the ubuntu cd. should i try a reinstall or delete that partition and boot back to windows then start again?

---

### Post by dino99 on 2010-11-19
what is your wireless chipset ?

if you reinstall, here is the guide line:

use gparted or partedmagic to create 3 partitions:
- / : root, bootable, ext4, ~ 12 Gb (take note of its name: /dev/sd? , will be asked when installing in manual mode by the "alternate" iso.
- swap : about 2 Gb
- /home : ext3 or ext4 format, unlimited space to store your data and settings

[http://partedmagic.com/](http://partedmagic.com/)

note: mostly never use winblows driver with Linux, they are builtin for the most current

---

### Post by huntintim on 2010-11-19
yes i did do the reinstall. im not sure of the wireless chip-set. the keyboard still dose not work at the dual boot screen but it did boot into ubuntu this time. how do i determine the chip-set of the wireless device. im relay not that worried about the no keyboard issue because if i like ubuntu after about 3 months or so i think im going to do the reinstall and completely wipe windows so i relay want to focus on the driver fr the network adapter.

---

### Post by huntintim on 2010-11-19
ok so did lsusb and came up with the id as 1737:0075. where can i find the drivers for linux if made?

---

### Post by oldfred on 2010-11-19
You may have a setting in BIOS to allow USB keyboards. It seems Windows & Ubuntu ignore BIOS setting but grub uses it.

I do not know about wireless as mine just works. Do you have ethernet plugged in so you can download wireless driver. If so check System, adminstration, Hardware Drivers.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide/Drivers)
Some commands to check
[http://ubuntuforums.org/showthread.php?t=1491899](http://ubuntuforums.org/showthread.php?t=1491899)

---

### Post by huntintim on 2010-11-19
well the keyboard thing was a stupid mistake. i pluge them all in to an pci expansion card that requires a driver to come up. so i put them back in the onboard usb slots and they work fine. as far as the networking issue it seems my time ould be better spent for a known compatable wireless device. i have ound several places with this same piece of hardware and no resolve.

---

### Post by huntintim on 2010-11-21
for those keeping up with this i discontinued tryig to get this thing to work i went and bought a Belkin F7D1101 I did have to use the ndiswraper with the windows driver. but it works like a charm even with wpa2 security to the router. ubuntu is up and everything works except a dvd player but im about to tackle that.

---

