---
title: "b43-cutter    12.10    dell"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by s9032g@comcast.net on 2012-10-22
Ok I got b43-cutter
b43-fwcutter version 015

A tool to extract firmware for a Broadcom 43xx device
from a proprietary Broadcom 43xx device driver file.

Usage: b43-fwcutter [OPTION] [proprietary-driver-file]
  --unsupported         Allow working on extractable but unsupported drivers
  -l|--list             List supported driver versions
  -i|--identify         Only identify the driver file (don't extract)
  -w|--target-dir DIR   Extract and write firmware to DIR
  -v|--version          Print b43-fwcutter version
  -h|--help             Print this help

Example: b43-fwcutter -w /lib/firmware wl_apsta.o
         to extract the firmware blobs from wl_apsta.o and store
         the resulting firmware in /lib/firmware

NOW  How do I use it to get drivers for Broadcom BCM4312 low power lpphy device??????????

---

### Post by dino99 on 2012-10-22
i dont know if you're a human, but ubuntu is for human  (joke)

simply install:

sudo apt-get install firmware-b43-lpphy-installer


***
This package installs the firmware needed for usage of the b43 kernel
driver.

Supported chipsets:
 - BCM4312 (with Low-Power aka LP-PHY)
****

---

### Post by s9032g@comcast.net on 2012-10-22
I have done that. Did not work.

I solved all the 12.10 issues by going back to 12.04.

First time in 10 distros that I had to give up.

---

