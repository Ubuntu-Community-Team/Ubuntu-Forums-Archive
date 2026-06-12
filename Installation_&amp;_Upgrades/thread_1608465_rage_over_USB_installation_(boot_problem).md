---
title: "rage over USB installation (boot problem)"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by tml240 on 2010-10-29
I've been struggling with it for about 7-8 hours so I turn here.

I got a HP Mini 1150nr netbook and want to get the full 10.10 instsalled (not the netbook remix). So I've been trying to create the USB Install key (I have a 1GB one)

At first, I tried using my desktop and laptop's Startup Disk Creator (usb-creator-gtk). It starts erroring it up when I tried erasing data. So I use GParted to get FAT32. But then when I go back to USB-Creator-gtk to create a startup key, it errors up at 99% saying cannot install bootloader.

Also in Gparted, I tried adding 'boot' flag to get the key to boot when selected at BIOS. No luck.

So I turned to Windows and tried using UNetbootin and Universal USB Program. I create the USB keys in FAT32 (default) but then it doesn't seem to have any bootloader although the Windows programs do not show any error about it.

So for three computers I tried my USB stick, it's skipping through the USB Key.

I'm thinking about adding Windows' "boot.ini" but I'm not sure what to change there.

Any suggestions? Solutions?

Thanks so much!

---

### Post by wilee-nilee on 2010-10-29
Have you checked the Md5SUM of the ISO.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Do you have another thumb?

---

### Post by tml240 on 2010-10-29
Hash's are fine for ISOs... I'm thinking it might be the USB thumb now. Don't have another one, but would it be possible to install from an external hard drive without formatting the drive? I've only seen threads with booting up Ubuntu from the drive, which is not what I want.

---

### Post by wilee-nilee on 2010-10-29
> **tml240 said:**
> Hash's are fine for ISOs... I'm thinking it might be the USB thumb now. Don't have another one, but would it be possible to install from an external hard drive without formatting the drive? I've only seen threads with booting up Ubuntu from the drive, which is not what I want.

There is a loop that can be done from a partition I believe to install, I don't know the process though I will look around.

---

### Post by tml240 on 2010-10-29
well the good news is i decided to create a new partition on my external hdd to get the live installer working. the bad news is that the netbook just goes blank on the usb bootup

---

