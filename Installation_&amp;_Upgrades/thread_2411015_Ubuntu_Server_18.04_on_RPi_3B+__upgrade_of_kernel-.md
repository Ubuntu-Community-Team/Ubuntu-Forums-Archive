---
title: "Ubuntu Server 18.04 on RPi 3B+  upgrade of kernel- error."
date: 2019-01-23
forum: Installation &amp; Upgrades
---

### Post by B99 on 2019-01-23
Hi.

I don't know if my error is general enough for this forum or is better addressed on the Raspberry forums. Please let me know.

I am running the official Ubuntu image for Raspberry Pi 2 found [here]("https://wiki.ubuntu.com/ARM/RaspberryPi") with a boot partition modified for the RPi 3B+.  The first time I ran apt upgrade I got an error attempting to install 

linux-firmware/bionic-updates 1.173.3 all [upgradable from: 1.173.1]

Below is the error I receive when I try and upgrade now.

Two questions:

Is this fixable?

Is it a problem to leave it unfixed?

TIA

```
Fetched 2307 kB in 4s (583 kB/s)Reading package lists... Done
Building dependency tree
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/65.3 MB of archives.
After this operation, 3281 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 135768 files and directories currently installed.)
Preparing to unpack .../linux-firmware_1.173.3_all.deb ...
Unpacking linux-firmware (1.173.3) over (1.173.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-firmware_1.173.3_all.deb (--unpack):
 trying to overwrite '/lib/firmware/brcm/brcmfmac43455-sdio.bin', which is the diverted version of '/tmp/brcmfmac43455-sdio.bin'
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
update-initramfs: Generating /boot/initrd.img-4.15.0-1030-raspi2
Using DTB: bcm2710-rpi-3-b-plus.dtb
Installing /lib/firmware/4.15.0-1030-raspi2/device-tree/bcm2710-rpi-3-b-plus.dtb into /boot/dtbs/4.15.0-1030-raspi2/bcm2710-rpi-3-b-plus.dtb
Taking backup of bcm2710-rpi-3-b-plus.dtb.
Installing new bcm2710-rpi-3-b-plus.dtb.
Installing /lib/firmware/4.15.0-1030-raspi2/device-tree/bcm2710-rpi-3-b-plus.dtb into /boot/dtbs/4.15.0-1030-raspi2/bcm2710-rpi-3-b-plus.dtb
Taking backup of bcm2710-rpi-3-b-plus.dtb.
Installing new bcm2710-rpi-3-b-plus.dtb.
flash-kernel: deferring update (trigger activated)
update-initramfs: Generating /boot/initrd.img-4.15.0-1022-raspi2
Using DTB: bcm2710-rpi-3-b-plus.dtb
Installing /lib/firmware/4.15.0-1022-raspi2/device-tree/bcm2710-rpi-3-b-plus.dtb into /boot/dtbs/4.15.0-1022-raspi2/bcm2710-rpi-3-b-plus.dtb
Taking backup of bcm2710-rpi-3-b-plus.dtb.
Installing new bcm2710-rpi-3-b-plus.dtb.
Ignoring old or unknown version 4.15.0-1022-raspi2 (latest is 4.15.0-1030-raspi2)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-firmware_1.173.3_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

