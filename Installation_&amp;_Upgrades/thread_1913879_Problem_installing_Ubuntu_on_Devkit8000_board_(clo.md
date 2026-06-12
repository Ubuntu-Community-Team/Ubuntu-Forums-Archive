---
title: "Problem installing Ubuntu on Devkit8000 board (clone of BeagleBoard)"
date: 2012-01-23
forum: Installation &amp; Upgrades
---

### Post by Kitinz on 2012-01-23
Hello everyone.


Im trying to install a ubuntu into a Devkit8000 board, which is a BeagleBoard clone. It's ARM architecture with a OMAP3530 processor.

I followed the instalation instructions on [https://wiki.ubuntu.com/ARM/OmapNetbook](https://wiki.ubuntu.com/ARM/OmapNetbook), but when i turn on the board with the sdcard this is what i got:

```
Texas Instruments X-Loader 1.41
Starting OS Bootloader...


U-Boot 1.3.3 (Dec 21 2010 - 16:13:44)

OMAP3530-GP rev 2, CPU-OPP2 L3-165MHz
OMAP3 DevKit8000 Board + LPDDR/NAND
DRAM:  256 MB
NAND:  256 MiB
In:    serial
Out:   serial
Err:   serial
Hit any key to stop autoboot:  0 
reading uImage

3605220 bytes read
## Booting kernel from Legacy Image at 80300000 ...
   Image Name:   Linux
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    3605156 Bytes =  3.4 MB
   Load Address: 80008000
   Entry Point:  80008000
   Verifying Checksum ... OK
   Loading Kernel Image ... OK
OK

Starting kernel ...


```

And nothing else happens. Just for your information, im connecting to he board using the serial port through minicom.

Dont know what else can i try, so im looking for some help.


Thank you all in advance :D

---

### Post by Kitinz on 2012-01-26
BUMP to find someone who can help me :D

---

### Post by bimodh on 2012-04-07
I think you haven't changed the environments to the mmcblk0p2.

---

