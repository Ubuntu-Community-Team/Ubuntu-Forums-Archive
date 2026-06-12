---
title: "Ubuntu 19.10 on Flash Drive"
date: 2019-12-21
forum: Installation &amp; Upgrades
---

### Post by daniell59 on 2019-12-21
I installed Ubuntu 19.10 using mkusb. I tried to boot into it. All I got was the word Ubuntu with several dots. After about 15 minutes I gave up. Any insight into this problem will be appreciated.

---

### Post by oldfred on 2019-12-21
What brand/model system?
What video card/chip?
UEFI or BIOS install?
Dual booting with Windows that was pre-installed? Then UEFI and you really want Ubuntu in UEFI boot mode.

If nVidia, you need nomodeset boot parameter.

---

### Post by daniell59 on 2019-12-21
Home built
Radeon HD 3410
AMD Athlon 64X2 Dual Core Processor 4400+ 1000MHz
Memory 4GIG
BIOS

---

### Post by yancek on 2019-12-21
Based on the information you posted, you created what you hoped would be a bootable usb of Ubuntu 19.10 and are now trying to boot it and install it on a computer with no current operating system.   During the creation of the usb with mkusb, did you see any warnings or messages that might indicate a problem?  All I can suggest is that you review again the mkusb quick start guide and compare the instructions to your notes made during the attempt to create the bootable usb.

[https://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf](https://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual.pdf)

---

### Post by daniell59 on 2019-12-22
After a complete shutdown, I tried again this morning. After a short pause, it booted without a problem.

---

