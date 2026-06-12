---
title: "initramfs-tools broken (update-initramfs stuck)"
date: 2011-02-04
forum: Installation &amp; Upgrades
---

### Post by Unas on 2011-02-04
A while ago I upgraded Lucid from 2.6.32-23-generic to 2.6.32-24-generic. I have been unable to boot into 2.6.32-24 because of a missing initrd, so I've been using 2.6.32-23 ever since.

Today I upgraded my RAM from 8GB to 16GB, and I changed my NVidia GTS250 for an ATI 5450. In 2.6.32-23 I tried to install FGLRX via Hardware Drivers, and it got to 99% until it got stuck at:

**update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic**

I presume that this has never bother me before, because I never installed a driver after trying to upgrade to 2.6.32-24. Now however, it is a problem, because FGLRX is not working correctly. I think it is because the necessary changes have not been integrated with initramfs-tools.

I have tried to remove and reinstall initramfs-tools, but it keeps wanting to run update-initramfs before dpkg can do anything. I have run the following to prevent it:

**sudo nano /etc/initramfs-tools/update-initramfs.conf**

However, in an attempt to fix things, I again upgraded linux, this time to 2.6.32-28.55. So turning off update for initramfs in the config file doesn't help, as update-initramfs does need to be run either way to complete the upgrade.

I have also moved the initrd files in /boot, in an attempt for update-initramfs to perhaps work better, to no avail.

The moment update-initramfs starts, the ram does a weird thing, the ram usage keeps stepping up in flat steps, and then falls down again, with about 1 core of CPU engaged the whole time:
```
                           |---------| 10GB                |---------|
                   |-------|         |             |-------|         |
         |---------|                  |   |--------|                  |
_________|                             |__|                            |__|
```

My real problem is that I can't successfully resume after Suspend-to-RAM, which I believe is due to FGLRX not being correctly installed. I know it's not correctly installed, because the graphics is very very laggy, even though I can access the control panel. I need initramfs to work for me to fix FGLRX.

I have run out of options. How do I fix initramfs-tools?

---

### Post by Unas on 2011-02-04
Installed a fresh lucid, and FGLRX successfully. I can confirm that suspend to RAM is now working correctly.

Though, the problem with initramfs-tools still remain on my other linux, so if anyone could give some advice I'd appreciate it, thx.

---

