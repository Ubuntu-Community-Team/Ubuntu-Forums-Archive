---
title: "Window boot missing"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by anirudha on 2011-11-16
Hi All
I have installed Ubuntu 9.10 on my PC which already has windows XP on it. But, while installing Ubuntu, I disconnected HDD having windows XP OS.

Now, when I reconnected the HDD that has XP, it does not show boot option for XP - Ubuntu is booted automatically. Can anyone please help me to recover the windows boot to allow dual boot option.

---

### Post by darkod on 2011-11-16
Because the disk was disconnected during install, ubuntu did not discover it to include it in the boot menu.

Boot ubuntu, open the terminal and run:

sudo update-grub

That will sort it out.

---

### Post by anirudha on 2011-11-17
Thanks for help!

I tried the update-grub command and but following error ...

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sdb2
grub-probe: error: Cannot find a GRUB drive for /dev/sdb2.  Check your device.map.

done

Is there some way to fix this? I would appreciate any help.

---

### Post by darkod on 2011-11-17
This is why it's better not to disconnect other disks while installing so that they can be properly discovered.

First run a command to generate new device map and then to update grub:

sudo grub-mkdevicemap
sudo update-grub

---

