---
title: "How to install to SD Card (PCI card reader, NOT USB!!!)?"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by QcQccbM on 2013-08-03
Hey all,

I'm trying to install Ubuntu (or one of it's flavors) to an SD card in my Toshiba R600 (circa 2009) laptop.  I tried the Universal USB Installer, which creates a "live-USB" install with persistence file, however it does not boot on my laptop.  When I select the SD card in BIOS boot device selection, the SD indicator on the machine blinks, but 20 seconds later the machine just boots Windows from hard drive.
While troubleshooting this I found that my SD controller is a Ricoh with hardware ID PCI\VEN_1180&DEV_0822, and apparently does floppy emulation on boot (no settings I can change).  Acronis Disk Director identifies the SD card as "Super Floppy".
I am using an 8GB Transcend class 6 SD card.

I would appreciate if someone could advise me how to install and boot Ubuntu (or any distro, really), onto an SD card on a PCI controller.

Thanks!

PS the new login system mangled my username when transferring it from old forums from years ago :(

---

### Post by ubfan1 on 2013-08-03
Never had any trouble creating a bootable SD card in an SD reader, but then never tried an 8G card either.  Try putting a 2G partition on the card and install to that.  Use the rest of the space if needed for data, make it FAT32 or something both Ubuntu and Windows can read/write

---

### Post by QcQccbM on 2013-08-03
> **ubfan1 said:**
> Never had any trouble creating a bootable SD card in an SD reader, but then never tried an 8G card either.  Try putting a 2G partition on the card and install to that.  Use the rest of the space if needed for data, make it FAT32 or something both Ubuntu and Windows can read/write

Could you be more specific what kind of "SD reader" you had experience with?  On USB or PCI bus (this is important!)?

Unfortunately smaller partition had no effect.  I was using FAT32 on both attempts.

---

### Post by coldraven on 2013-08-03
Buy a 99 cent USB card reader stick. I use one to format SD and micro SD cards and to create bootable SD cards.
Similar to this example:
[http://www.ebay.co.uk/itm/High-Speed-USB-2-0-SD-SDHC-MMC-RS-MMC-Memory-Card-Reader-Adapter-New-2-/400334614133?pt=UK_Computing_CablesConnectors_RL&hash=item5d35cd6e75](http://www.ebay.co.uk/itm/High-Speed-USB-2-0-SD-SDHC-MMC-RS-MMC-Memory-Card-Reader-Adapter-New-2-/400334614133?pt=UK_Computing_CablesConnectors_RL&hash=item5d35cd6e75)

---

### Post by ubfan1 on 2013-08-03
The "SD reader" I referred to was the slot on the side of my laptop (/dev/mmcblk0p1).  But I have used usb readers too, neither gave any problems.  Is your card good? Try another one.

---

### Post by Rebelli0us on 2013-08-03
Your buil-in card reader is probably not bootable. Install to  a USB flash drive and boot off a USB port.

---

### Post by QcQccbM on 2013-08-03
> **coldraven said:**
> Buy a 99 cent USB card reader stick. I use one to format SD and micro SD cards and to create bootable SD cards.
Similar to this example:
[http://www.ebay.co.uk/itm/High-Speed-USB-2-0-SD-SDHC-MMC-RS-MMC-Memory-Card-Reader-Adapter-New-2-/400334614133?pt=UK_Computing_CablesConnectors_RL&hash=item5d35cd6e75](http://www.ebay.co.uk/itm/High-Speed-USB-2-0-SD-SDHC-MMC-RS-MMC-Memory-Card-Reader-Adapter-New-2-/400334614133?pt=UK_Computing_CablesConnectors_RL&hash=item5d35cd6e75)
Sorry, not relevant to this thread. (I do have one laying around though, but again, it's not relevant)

> **ubfan1 said:**
> The "SD reader" I referred to was the slot on the side of my laptop (/dev/mmcblk0p1). But I have used usb readers too, neither gave any problems. Is your card good? Try another one.
Some internal card readers are wired to the USB bus, yours might be.  The SD card is fine, I got another idea, perhaps it's the SD vs. SDHC kind of a deal?

> **Rebelli0us said:**
> Your buil-in card reader is probably not bootable. Install to a USB flash drive and boot off a USB port.
Luckily, your guess is wrong.  I just got MS-DOS to boot from an SD card in this internal card reader.  I did mention above that I *do* have an option in BIOS to boot from SD.

My progress:
I remembered that I did have a smaller 2GB SD card in my old Garmin GPS in my car, so I'm now working with that.

Toshiba provides a utility for creation of bootable SD media for my laptop, it's called "TOSHIBA SD Memory Boot Utility", does what it says on the can :).  Unfortunately it does not support cards over 2GB in size, but now I have one to play with.  The utility wants either a floppy or an image file with extension .img, .flp, or .vfd.  I have an image of MS-DOS 6.22 floppy, I provided it to the utility.  The creation of the bootable SD with MS-DOS 6.22 succeeded, I was able to boot MS-DOS 6.22 from SD.
I then booted Windows to check the SD contents.  The TOSHIBA SD Memory Boot Utility formatted the SD with FAT32 and created an image file (!) on the SD, the file name is **$TOSFD00.VFD** on the SD (file size 1.4MB), that's the only file on the 2GB FAT32 partition.  Make note of this.  Like I said before, this BIOS does some fancy floppy emulation at boot.

I then tried the Universal USB Installer again (this is the "pendrive" way) with the 2GB card.  No boot, as I predicted.
Next, I made a VHD (virtual hard drive) image of the SD card with Ubuntu USB installation, and fed it to the TOSHIBA SD Memory Boot Utility.  It gave me an error message "Format not supported.", I changed the extension of the file to VFD (virtual floppy drive), but still same error.  I will try other image formats...

So, as it stands I have established the following:

1.  My laptop is capable of booting from SD
2.  My laptop uses a "non-standard" format of bootable SD
3.  The typical USB "pendrive" distro installation method is not compatible with #2.
4.  My laptop uses Toshiba's own custom proprietary BIOS, *not* Phoenix/Award/AMI

I will also check the SD vs. SDHC thing by placing the VFD file created by the Toshiba utility onto the 8GB card to see if BIOS will work with SDHC card.

**My idea:**

If large (greater than 1.4MB) virtual images don't work, I think this could be done another way.  Perhaps placing just the bootloader and maybe kernel on the floppy image, and then the rest just on SD.  That way the bootloader and possibly kernel starts from the emulated floppy, and then takes control of SD and boots the rest of the distro from SD directly?

It would be nice if someone with some advanced experience chimes in.  Like I said before, this is not a "pendrive" install.

---

### Post by QcQccbM on 2013-08-03
Fascinating!

My idea looks promising now.  Here is what I tried:

I put the MS-DOS 6.22 VFD on the SD, and I put an application (DOOM2 for nostalgia's sake) in the root of the SD (FAT32 partition).

When MS-DOS 6.22 booted, the VFD became the drive A, and the SD root became drive C.  (DOOM2 ended up being C:\DOOM2\)

So, I need to boot my distro from the VFD, and the rest of the distro can reside in the SD root.  I suppose it could be possible to boot Linux from DOS, I think a number of boot CDs do that (like Hiren's).

Anyone with experience of booting Linux with (virtual) floppy + SD combination?

*EDIT*

GRUB4DOS?

---

### Post by QcQccbM on 2013-08-04
And success.

I was able to set up GRUB4DOS.  If anyone is curious the device mapping is as follows, fd0 is the VFD, hd0 is laptop hard drive, hd1 is the SD.  Booting the hd1 MBR from GRUB4DOS boots the "pendrive" install.

I ran into the outstanding bug in casper, where casper does not find the squashfs image on SD because it doesn't search card readers.
Link to the bug report:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/810484](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/810484)
Workaround is to pass LIVEMEDIA=/dev/mmcblk0p1 to the kernel.

I should note that loading vmlinuz and initrd from the SD using BIOS emulation takes about 5 minutes, it's excruciatingly slow.  Not sure if it can be made to work faster, but I will try the SDHC card later.  Things do speed up once the kernel loads though.

Anyway, I got Ubuntu up and running, and looks like most devices are set up correctly.  The open source Intel graphics drivers suck big time.  Graphics performance is worse than in a virtual machine with guest add-ons.
Are there any better closed source drivers available for Intel graphics chipsets?

I have to give major kudos to Toshiba though, this VFD feature is brilliant.  I can quickly boot floppy images on this floppy-less machine without formatting USB sticks or SD cards, and can have larger filesystem accessible at the same time.  All that is needed is for the floppy image to be named $TOSFD00.VFD and be in the SD root.

---

### Post by Stephen_Schiff on 2013-10-17
Here is how I installed Ubuntu 12.04.3 on my EeePC (which came preloaded with Windows 7 Starter).  1)  plug a 16 GB SD card into the slot; 2)  download the Ubuntu .iso file; 3) download wubi.exe (from the Ubuntu site); 4) run wubi, selecting the SD card as the installation location.  What then happened is that it installed Linux on the SD card and changed the boot manager, so that now when I turn the machine on, I get a choice of Windows or Linux.  It could not have been simpler!  
I was confused for a while, and thought I needed to follow the procedure for installing on a USB drive.  That makes a portable OS; what I did was not the same and probably isn't portable.  (But I can't test it because my other machines are 64 bit and the ASUS is 32.

---

