---
title: "Kernel.org Patch 2.6.38"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by carolinabranden on 2011-03-18
This is my first time patching Linux. I'd really like to have patch 2.6.38 that was just released from kernel.org. Managed to get some information off the internet how to, but I am not entirely sure what I am doing. I haven't applied the patch yet. Did I skip or do something wrong? #-o

<code>
su
apt-get update
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
cd /usr/src
wget [http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.38.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.38.bz2)
bzip2 -dc /usr/src/patch-2.6.38.bz2 | patch -p1 --dry-run
</code>

<code>
patching file .gitignore
Hunk #1 FAILED at 28.
1 out of 1 hunk FAILED -- saving rejects to file .gitignore.rej
patching file .mailmap
Hunk #1 FAILED at 23.
Hunk #2 FAILED at 105.
2 out of 2 hunks FAILED -- saving rejects to file .mailmap.rej
patching file CREDITS
Hunk #1 FAILED at 2365.
Hunk #2 FAILED at 2813.
2 out of 2 hunks FAILED -- saving rejects to file CREDITS.rej
patching file Documentation/ABI/stable/thermal-notification
patching file Documentation/ABI/testing/sysfs-class-led
Hunk #1 FAILED at 26.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/ABI/testing/sysfs-class-led.rej
patching file Documentation/ABI/testing/sysfs-class-net-batman-adv
patching file Documentation/ABI/testing/sysfs-class-net-mesh
patching file Documentation/ABI/testing/sysfs-driver-hid-roccat-kone
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 17.
Hunk #3 FAILED at 33.
Hunk #4 FAILED at 48.
Hunk #5 FAILED at 58.
Hunk #6 FAILED at 67.
Hunk #7 FAILED at 78.
7 out of 7 hunks FAILED -- saving rejects to file Documentation/ABI/testing/sysfs-driver-hid-roccat-kone.rej
patching file Documentation/ABI/testing/sysfs-driver-hid-roccat-koneplus
patching file Documentation/ABI/testing/sysfs-driver-hid-roccat-pyra
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 14.
Hunk #3 FAILED at 31.
Hunk #4 FAILED at 45.
Hunk #5 FAILED at 56.
Hunk #6 FAILED at 69.
Hunk #7 FAILED at 79.
Hunk #8 FAILED at 87.
8 out of 8 hunks FAILED -- saving rejects to file Documentation/ABI/testing/sysfs-driver-hid-roccat-pyra.rej
patching file Documentation/ABI/testing/sysfs-platform-at91
patching file Documentation/ABI/testing/sysfs-platform-ideapad-laptop
patching file Documentation/ABI/testing/sysfs-tty
patching file Documentation/DocBook/80211.tmpl
Hunk #1 FAILED at 146.
Hunk #2 FAILED at 267.
Hunk #3 FAILED at 332.
Hunk #4 FAILED at 346.
Hunk #5 FAILED at 354.
Hunk #6 FAILED at 367.
Hunk #7 FAILED at 374.
Hunk #8 FAILED at 417.
Hunk #9 FAILED at 424.
Hunk #10 FAILED at 435.
Hunk #11 FAILED at 485.
11 out of 11 hunks FAILED -- saving rejects to file Documentation/DocBook/80211.tmpl.rej
patching file Documentation/DocBook/device-drivers.tmpl
Hunk #1 FAILED at 217.
Hunk #2 FAILED at 304.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/device-drivers.tmpl.rej
patching file Documentation/DocBook/drm.tmpl
Hunk #1 FAILED at 73.
Hunk #2 FAILED at 84.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/drm.tmpl.rej
patching file Documentation/DocBook/dvb/dvbapi.xml
Hunk #1 FAILED at 28.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/dvb/dvbapi.xml.rej
patching file Documentation/DocBook/filesystems.tmpl
Hunk #1 FAILED at 82.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/filesystems.tmpl.rej
patching file Documentation/DocBook/media.tmpl
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 86.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/media.tmpl.rej
patching file Documentation/DocBook/mtdnand.tmpl
Hunk #1 FAILED at 250.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/mtdnand.tmpl.rej
patching file Documentation/DocBook/v4l/dev-rds.xml
Hunk #1 FAILED at 75.
Hunk #2 FAILED at 129.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/v4l/dev-rds.xml.rej
patching file Documentation/DocBook/v4l/func-ioctl.xml
Hunk #1 FAILED at 34.
Hunk #2 FAILED at 57.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/v4l/func-ioctl.xml.rej
patching file Documentation/DocBook/v4l/pixfmt.xml
Hunk #1 FAILED at 142.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/DocBook/v4l/pixfmt.xml.rej
patching file Documentation/DocBook/v4l/v4l2.xml
Hunk #1 FAILED at 100.
Hunk #2 FAILED at 381.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/DocBook/v4l/v4l2.xml.rej
patching file Documentation/IPMI.txt
Hunk #1 FAILED at 533.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/IPMI.txt.rej
patching file Documentation/Makefile
Hunk #1 FAILED at 1.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/Makefile.rej
patching file Documentation/RCU/trace.txt
Hunk #1 FAILED at 1.
Hunk #2 FAILED at 130.
Hunk #3 FAILED at 168.
Hunk #4 FAILED at 212.
Hunk #5 FAILED at 326.
5 out of 5 hunks FAILED -- saving rejects to file Documentation/RCU/trace.txt.rej
patching file Documentation/acpi/apei/output_format.txt
patching file Documentation/arm/00-INDEX
Hunk #1 FAILED at 34.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/arm/00-INDEX.rej
patching file Documentation/arm/OMAP/omap_pm
Hunk #1 FAILED at 127.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/arm/OMAP/omap_pm.rej
patching file Documentation/arm/swp_emulation
patching file Documentation/cgroups/blkio-controller.txt
Hunk #1 FAILED at 89.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/cgroups/blkio-controller.txt.rej
patching file Documentation/cgroups/cgroup_event_listener.c
Hunk #1 FAILED at 91.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/cgroups/cgroup_event_listener.c.rej
patching file Documentation/cgroups/cgroups.txt
Hunk #1 FAILED at 355.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/cgroups/cgroups.txt.rej
patching file Documentation/cgroups/memcg_test.txt
Hunk #1 FAILED at 398.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/cgroups/memcg_test.txt.rej
patching file Documentation/coccinelle.txt
Hunk #1 FAILED at 36.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/coccinelle.txt.rej
patching file Documentation/device-mapper/dm-crypt.txt
Hunk #1 FAILED at 8.
Hunk #2 FAILED at 20.
2 out of 2 hunks FAILED -- saving rejects to file Documentation/device-mapper/dm-crypt.txt.rej
patching file Documentation/device-mapper/dm-raid.txt
patching file Documentation/devicetree/bindings/ata/fsl-sata.txt
patching file Documentation/devicetree/bindings/eeprom.txt
patching file Documentation/devicetree/bindings/gpio/8xxx_gpio.txt
patching file Documentation/devicetree/bindings/gpio/gpio.txt
patching file Documentation/devicetree/bindings/gpio/led.txt
patching file Documentation/devicetree/bindings/i2c/fsl-i2c.txt
patching file Documentation/devicetree/bindings/marvell.txt
patching file Documentation/devicetree/bindings/mmc/fsl-esdhc.txt
patching file Documentation/devicetree/bindings/mmc/mmc-spi-slot.txt
patching file Documentation/devicetree/bindings/mtd/fsl-upm-nand.txt
patching file Documentation/devicetree/bindings/mtd/mtd-physmap.txt
patching file Documentation/devicetree/bindings/net/can/mpc5xxx-mscan.txt
patching file Documentation/devicetree/bindings/net/can/sja1000.txt
patching file Documentation/devicetree/bindings/net/fsl-tsec-phy.txt
patching file Documentation/devicetree/bindings/net/mdio-gpio.txt
patching file Documentation/devicetree/bindings/net/phy.txt
patching file Documentation/devicetree/bindings/pci/83xx-512x-pci.txt
patching file Documentation/devicetree/bindings/powerpc/4xx/cpm.txt
patching file Documentation/devicetree/bindings/powerpc/4xx/emac.txt
patching file Documentation/devicetree/bindings/powerpc/4xx/ndfc.txt
patching file Documentation/devicetree/bindings/powerpc/4xx/ppc440spe-adma.txt
patching file Documentation/devicetree/bindings/powerpc/4xx/reboot.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/board.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/cpm.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/cpm/brg.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/cpm/i2c.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/cpm/pic.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/cpm/usb.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/gpio.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/network.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe/firmware.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe/par_io.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe/pincfg.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe/ucc.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/qe/usb.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/cpm_qe/serial.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/diu.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/dma.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/ecm.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/gtm.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/guts.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/lbc.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/mcm.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/mcu-mpc8349emitx.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/mpc5121-psc.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/mpc5200.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/mpic.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/msi-pic.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/pmc.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/sec.txt
patching file Documentation/devicetree/bindings/powerpc/fsl/ssi.txt
patching file Documentation/devicetree/bindings/powerpc/nintendo/gamecube.txt
patching file Documentation/devicetree/bindings/powerpc/nintendo/wii.txt
patching file Documentation/devicetree/bindings/spi/fsl-spi.txt
patching file Documentation/devicetree/bindings/spi/spi-bus.txt
patching file Documentation/devicetree/bindings/usb/fsl-usb.txt
patching file Documentation/devicetree/bindings/usb/usb-ehci.txt
patching file Documentation/devicetree/bindings/xilinx.txt
patching file Documentation/devicetree/booting-without-of.txt
patching file Documentation/dontdiff
Hunk #1 FAILED at 62.
Hunk #2 FAILED at 76.
Hunk #3 FAILED at 94.
Hunk #4 FAILED at 108.
Hunk #5 FAILED at 140.
Hunk #6 FAILED at 153.
Hunk #7 FAILED at 169.
Hunk #8 FAILED at 190.
Hunk #9 FAILED at 200.
9 out of 9 hunks FAILED -- saving rejects to file Documentation/dontdiff.rej
patching file Documentation/dvb/lmedm04.txt
Hunk #1 FAILED at 46.
1 out of 1 hunk FAILED -- saving rejects to file Documentation/dvb/lmedm04.txt.rej
patching file Documentation/email-clients.txt
Hunk #1 FAILED at 104.
Hunk #2 FAILED at 179.
Hunk #3 FAILED at 208.
3 out of 3 hunks FAILED -- saving rejects to file Documentation/email-clients.txt.rej
patching file Documentation/fb/udlfb.txt
patching file Documentation/feature-removal-schedule.txt
Hunk #1 FAILED at 97.
Hunk #2 FAILED at 191.
Hunk #3 FAILED at 232.
Hunk #4 FAILED at 330.
Hunk #5 FAILED at 564.
5 out of 5 hunks FAILED -- saving rejects to file Documentation/feature-removal-schedule.txt.rej
patching file Documentation/filesystems/Locking
Hunk #1 FAILED at 9.
Hunk #2 FAILED at 44.
Hunk #3 FAILED at 53.
Hunk #4 FAILED at 73.
Hunk #5 FAILED at 81.
Hunk #6 FAILED at 340.
Hunk #7 FAILED at 350.
Hunk #8 FAILED at 432.
8 out of 8 hunks FAILED -- saving rejects to file Documentation/filesystems/Locking.rej
The next patch would delete the file Documentation/filesystems/dentry-locking.txt,
which does not exist!  Assume -R? [n] 
</code>

Something doesn't look right. lol

---

### Post by Rolie on 2011-03-18
The patch you try to apply is created against another version of the kernel source code than you want to apply it to.

If you want to run 2.6.38, have a look at [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild). Or do it the easy way and have a look at [http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa).

---

### Post by carolinabranden on 2011-03-18
Bingo! [[color="#B22222"]Install latest kernel 2.6.37 & 2.6.38 in Ubuntu 10.04 from PPA[/color]](http://ubuntuguide.net/install-latest-kernel-2-6-37-2-6-38-in-ubuntu-10-04-from-ppa) filled the gaps. :D

---

