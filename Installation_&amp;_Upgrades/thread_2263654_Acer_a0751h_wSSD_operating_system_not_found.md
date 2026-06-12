---
title: "Acer a0751h w/SSD: operating system not found"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by alexndr-frolov on 2015-02-02
Hi folks!

I have downloaded Ubuntu 12.04.4 (32-bit) and installed it on my netbook (Acer Aspire One a0751h) with Intel SSD DC S3500 disk. 
Unfortunately, BIOS does not see grub and nothing which I have tried helped to mend this problem.

I tried to do the following:

1. Booting with live USB, mounting sda1 and running 

[FONT=courier new]sudo grub-install --boot-directory=/mnt/boot /dev/sda[/FONT]

2. I thought that it can be caused to be related to the configuration of the SATA controller (which is set to IDE by default) but after updating BIOS to most recent version 32.12 I still could not find there more options than in the previous BIOS version.

The results of bootinfoscript are attached. I have tried 14.04.1 and 14.10 releases with the same effect.

Any help will be much appreciated!  :-) I am almost at the wit's end :-(

Best, 
   Alex

---

### Post by oldfred on 2015-02-02
If you hold shift key as BIOS boots until grub menu should appear, do you get grub menu?
With only Ubuntu you do not normally get grub menu.

It looks like you only have 1GB of RAM. Lubuntu or Xubuntu may work a lot better. Also your graphics chip just may not have enough power to run full Ubuntu with Unity. My old laptop with dual core but Intel video and 1.5GB RAM is too slow for Unity, but I can install fallback as a lighter weight gui.

If you have a AHCI mode you need to use that, not IDE. Otherwise you will have issues with SSD as trim will not work.

---

### Post by alexndr-frolov on 2015-02-02
Holding shift keys does not help (why should otherwise?)

I have 2GB of DRAM and not going to use heavy window managers such as KDE or GNOME. I used FC19 on the same netbook and it worked fine (with HDD).

I am not able to set AHCI because this option is not provided in my BIOS (it is very limited actually). There is a version 3310 for Acer A110/A150 models but I am afraid to try it for my A0751H.

---

### Post by oldfred on 2015-02-02
BIOS should not have to see grub, just see drive and BIOS boot will load grub. Does BIOS correctly show SSD?
But with one install you will not see grub load, but it will continue to boot system. 
Then issue can be some driver not loading or other issues later in boot process.
You should be able to hold shift key as BIOS starts and get grub menu.

I think in IDE mode SSD will fill up and become very slow (may still be a bit faster than a hard drive) as it then has to erase before it can write, if trim does not work.

---

### Post by alexndr-frolov on 2015-02-02
In the boot tab its only marked as IDE HDD... No other mention about ssd

---

### Post by oldfred on 2015-02-02
Most BIOS show model of drive, may not say SSD, but should show it under the HDD settings.

If not seen double check all connections.

---

### Post by alexndr-frolov on 2015-02-03
I think the problem is in BIOS. I tried to insert this Intel SSD into another (desktop) computer and it has been visible in BIOS and Ubuntu booted successfully. Also I have found another SSD disk (Transcend SATA-2) it has also been visible in my A0751h BIOS. I would assume about backward compatibility (netbook has SATA) but the specification proves it to be compatible with SATA ([http://www.intel.com/content/dam/www/public/us/en/documents/product-specifications/ssd-dc-s3500-spec.pdf](http://www.intel.com/content/dam/www/public/us/en/documents/product-specifications/ssd-dc-s3500-spec.pdf)) and it can be mounted. 

Any other clues?

---

### Post by oldfred on 2015-02-03
If BIOS does not support SSD, then there is nothing we can do. 
BIOS has to report to operating system what hardware system has.

---

### Post by alexndr-frolov on 2015-02-03
It's strange that BIOS does not support this SSD but anyway I could install Ubuntu on it and can mount it, that is SSD is correctly working as SATA device.
I think to try it with more BIOS versions.

---

### Post by oldfred on 2015-02-03
If you can mount it, then I do not understand that you should not be able to boot from it. Or is it now in an USB external mount?

---

### Post by alexndr-frolov on 2015-02-04
No, it is attached to on board SATA connector.

I think of a work around to place /boot on USB and everything else leave on SSD.. Is it possible?

---

### Post by oldfred on 2015-02-04
Just about anything is possible.

And some have laptops with  a DVD caddy that can be replaced with a hard drive, but is not bootable. So they have done as you intend by putting /boot only on the hard drive and the rest of the install on the drive in the DVD slot.

---

### Post by alexndr-frolov on 2015-02-04
I did exactly this (installed grub on usb stick with vmlinuz and initird) and ... 
.. I have Ubuntu running beatifully  on my Acer Aspire One 751h with Intel SSD S3500 with usb flash drive sticking from it :-)

Many thanks!

ps. I think to use sdcard instead of usb stick for grub :-)

---

