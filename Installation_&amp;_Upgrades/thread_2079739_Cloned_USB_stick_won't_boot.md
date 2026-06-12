---
title: "Cloned USB stick won't boot"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by andycivil on 2012-11-02
I made a bootable USB stick, it has /boot, /, and swap partitions. It was becoming unreliable so I cloned it with gparted, and set the 'boot' flag on the boot partition. The new one won't boot. I think it's because I have yet to install grub, so there's no grub in the MBR. Assuming I know the device name of the stick (e.g. /dev/sde) what grub-install command would I use to get this clone working? Thanks.

---

### Post by darkod on 2012-11-02
You will have to use the cd of the same version in live mode, or live usb, and know the exact number of the /boot and / partitions.

Since you have /boot partition too, you have to mount both before running the grub-install. The commands for a usb stick called /dev/sde would be:
```
sudo mount /dev/sdeX /mnt (the / partition)
sudo mount /dev/sdeY /mnt/boot (the /boot partition)
sudo grub-install --root-directory=/mnt /dev/sde
```

That will install it on the MBR of /dev/sde.

---

### Post by andycivil on 2012-11-02
Worked perfectly (in the end!). Tried it from the original USB stick, got a "bus error". Dug out the original install CD and booted from that, second time lucky. Thank you!

---

