---
title: "usb boot"
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by xxxxvector on 2013-08-25
I wanted to reinstall Ubuntu 13.04 by deleting the Ubuntu partition from windows.  After deleting the partition I tried booting from USB but it doesn't work. If I boot without the USB stick I get the grub error because I deleted Ubuntu and when I use the USB it bootloops the small logo appears,  the purple background with a man in the circle where I get options to try.Ubuntu,  install it, memory test but when I select try or install it freezes and restarts. Any help, the last time I didn't have any error

---

### Post by oldfred on 2013-08-25
Is this a BIOS (not UEFI) system?
What Video card/Chip do you have. I have nVidia and have to use nomodeset on all installer boots and first boot after install.

From accessibility screen (tiny icons) press any key and then f6 to choose nomodeset. Perhaps other boot options may be required.

 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by xxxxvector on 2013-08-25
Nope nothing it still restarts after accessibility screen

---

### Post by oldfred on 2013-08-25
What system is this?
Or is it 32bit and you are trying to use the 64 bit, or very old and do not have PAE?

---

### Post by xxxxvector on 2013-08-25
32 bit Ubuntu raring ringtail CPU is and athlon 64 bit and VGA is nvidia geforce 8400 gs

---

### Post by oldfred on 2013-08-25
With nVidia you definitely need nomodeset. But Some systems also need other boot parameters.

On my system I could tell it was still booting as USB flash drive's LED kept flashing, but it turned monitor off. So I use nomodeset all the time until I install the nVidia proprietary drivers.

---

### Post by xxxxvector on 2013-08-25
Nomodeset doesn't work. I didn't need it in the past and I haven't changed anything  from the last time I reinstalled Ubuntu perhaps the USB is corrupted?

---

### Post by oldfred on 2013-08-25
What version did you install last? I had to start using nomodeset when they changed the kernel to use a different mode for video drivers. I think it was about 10.10.
I have a nVidia 9600GT and everyone that has posted with any version of nVidia has need nomodeset.

You can verify download with md5sum and run tests with flash drive if it seems correct.
 [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)



Sometimes BIOS settings also make a difference. Are drives set to AHCI? Not RAID or IDE?

---

### Post by xxxxvector on 2013-08-25
Ubuntu version 13.04 and I'm not sure about ahci but I've found these settings in BIOS : 
Ide hdd block mode enabled, raid is disabled, onchip idea channel0 enabled,  master pio slave pio master udma slave Irma are all auto, ide DmA transfer enabled,  serial ata controller and ide prefetch mode are enabled.  I have no idea what these mean.

---

### Post by oldfred on 2013-08-25
I wonder if previous install corrupted USB installer. Perhaps you install its grub to the flash drive. The installer is on a FAT32 formatted partition and uses syslinux to boot. So if grub gets installed to flash drive it will not boot.

---

### Post by xxxxvector on 2013-08-26
so, burning a live cd or making a new bootable usb is a good idea or not
p.s. wow you are motivated,  thanks for all the help so far

---

### Post by oldfred on 2013-08-26
I have several installers. I actually now use a hard drive to install to my SSD as that is very fast. But before I used flash drives and still maintain at least on with current ISOs. But when I used to install with CD have several repair CD in addition to Ubuntu liveCD. Now installer is too large for CD so flash drive is usually better, but you can use DVD.

---

### Post by xxxxvector on 2013-08-26
thanks for all the help! I eventually formatted the usb stick and burned ubuntu to it using unetbootin after that installation worked perfectly.

---

