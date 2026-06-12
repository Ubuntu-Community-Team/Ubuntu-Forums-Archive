---
title: "Problems booting, trying to install."
date: 2014-05-05
forum: Installation &amp; Upgrades
---

### Post by Marc_Edwards on 2014-05-05
Hi,

Bit of a beginner when it comes to solving technical problems with linux. Currently trying to install linux on a new pc. I have an image created with the pendrive linux tool on an external harddrive. I've done this before with an old laptop so don't think that's the problem. when i boot from the image i get a purple screen with a couple of symbols at the bottom then a black screen that says:
 wn-block (0,0)
[1.327397] cpu: 3 PID: 1 comm: swapper/0 not tainted

then some stuff about the hardware names to be filled by oem and a call trace. pic here 

 [http://s345.photobucket.com/user/alwaysmpe/media/IMG_20140505_163536_zps38a19b4d.jpg.html](http://s345.photobucket.com/user/alwaysmpe/media/IMG_20140505_163536_zps38a19b4d.jpg.html)

I suspect it's a hardware incompatibility but i'm not sure. I've turned off secure boot.

PC spec:
[COLOR=#464445][FONT=Verdana]CPU: AMD FX-4350 Quad Core CPU (4.3/4.2GHZ - 4MB CACHE/AM3+)
MB: [/FONT][/COLOR][COLOR=#464445][FONT=Verdana]ASUS® M5A97 LE R2.0 (DDR3, USB3.0, 6Gb/s)
RAM: [/FONT][/COLOR][COLOR=#464445][FONT=Verdana]8GB KINGSTON DUAL-DDR3 1600MHz (1 x 8GB)
GPU: [/FONT][/COLOR][COLOR=#464445][FONT=Verdana]2GB NVIDIA GEFORCE GTX 750 Ti

[/FONT][/COLOR]Any advice much appreciated, any questions go ahead.

M

---

### Post by ubfan1 on 2014-05-05
Sounds like a video problem. Try adding "nomodeset" to the linux boot line.  You may type "e" at the grub menu screen, (directions on screen) and type in the nomodeset at the "splash quiet" location.

---

### Post by oldfred on 2014-05-05
Is this a UEFI system? Or do you just want to install in BIOS boot mode? New systems can be either, but require you to set or choose which way to boot from UEFI/BIOS menu. Both options should be present.

       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If not also installing Windows, I also suggest using gpt partitioning. Ubuntu can boot from a drive partitioned with gpt in either BIOS or UEFI boot modes if correct supporting partitions are on drive. But Windows only boots from gpt with UEFI, so if installing Windows you may want BIOS boot with MBR(msdos) partitions.
With gpt include a 300MB efi partition first on drive for UEFI boot, and/or a 1 or 2MB unformatted partition with the bios_grub flag for BIOS boot. Then which ever mode you install in, you can easily convert later if desired. It can be difficult to add an efi partition later if you want to convert to UEFI as efi partition is supposed to be near front of drive.

Any system with nVidia needs nomodeset as suggested by ubfan1.

You also need very recent nVidia driver.

 Maxwell 750 
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

---

### Post by Marc_Edwards on 2014-05-05
it's not a uefi system, it's booting into the purple screen. what i want to do is dual boot win7 and ubuntu, game with windows and work on linux. windows 7 is already installed.

nomodeset didn't work, gives the exact same screen. thanks to both of you for your help!

---

### Post by oldfred on 2014-05-05
Was drive gpt partitioned before converting to Windows 7. The Windows 7 DVD only installs in BIOS mode and will convert a gpt drive to MBR(msdos), but does not do it correctly.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Some Asus need additional boot parameters to the nomodeset.
But the only posts I have seen were with Intel based and those probably are different settings just for Intel.

---

### Post by Marc_Edwards on 2014-05-05
no, windows 7 came pre-installed, i've just shrunk the main partition and was planning on installing in that space. it's likely the mother board in that case, i'll have a look tomorrow night, need sleep now. thanks.

---

