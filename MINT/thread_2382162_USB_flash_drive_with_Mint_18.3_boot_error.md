---
title: "USB flash drive with Mint 18.3 boot error"
date: 2018-01-09
forum: MINT
---

### Post by james2b on 2018-01-09
I have a new 32 GB USB stick with Linux Mint 18.3 on it with a persistence partition. So when I hit the key F8 to select the boot device and try to boot it, it just goes to a screen with "boot error". So is there some script file or other fix to make this bootable.? My system is a store built PC from 2009 and it is the MBR type with the old style BIOS, (not the UEFI). I just got it online from the OSDisk.com pre-installed, and it has not yet booted up at all. Okay thanks.

---

### Post by sudodus on 2018-01-10
It helps us help you, if you answer the following questions, and tell us more details about your computer:

1. Is your 'OSDisk.com pre-installed' a DVD disk or a USB pendrive?

2. Can your 'store built PC from 2009' boot from the 'OSDisk.com pre-installed', or are you booting another computer from it?

3. Can you boot another computer from the USB stick with Linux Mint 18.3?

4. Please specify your computer

- Brand name and model (of the motherboard)
- CPU
- RAM (size)
- internal drive (size)
- graphics chip/card
- wifi chip/card

---

### Post by james2b on 2018-01-10
Yes it is like I said, a USB stick, Samsung 32 GB, and I can boot other CDs, DVDs, and my other bootable USB flash drives with this 2009 computer. No I have not got it to boot to another computer yet either. 
Tech Support Guy System Info Utility version 1.0.0.2
OS Version: Microsoft Windows 7 Home Premium, Service Pack 1, 64 bit
Processor: Intel(R) Core(TM)2 Duo CPU E7400 @ 2.80GHz, Intel64 Family 6 Model 23 Stepping 10
Processor Count: 2
RAM: 8191 Mb
Graphics Card: NVIDIA GeForce 9600 GT, 1024 Mb
Hard Drives: C: Total - 76801 MB, Free - 20896 MB; D: Total - 66560 MB, Free - 27778 MB; E: Total - 30721 MB, Free - 15061 MB; H: Total - 20479 MB, Free - 20388 MB; I: Total - 114470 MB, Free - 114376 MB; K: Total - 218880 MB, Free - 218781 MB;
Motherboard: ASUSTeK Computer INC., P5QL PRO
Antivirus: Norton Security, Updated and Enabled

---

### Post by sudodus on 2018-01-11
There might be a problem with this particular USB stick or with the model, that it is not a good booter, or that it does not work well with your particular computer's hardware.

There might also be a problem with the Linux Mint version.

So you can

1. **try to boot some other computers** from the USB stick as it is now

2. **install another live operating system into the USB stick** and try again in this computer and in other computers.

[hr][/hr]
3. There might be problems with the graphics card, that might be fixed temporarily with the boot option **nomodeset**, and after installation, you should probably install an **nvidia proprietary driver**.

---

