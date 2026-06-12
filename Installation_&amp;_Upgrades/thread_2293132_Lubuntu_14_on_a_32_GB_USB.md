---
title: "Lubuntu 14 on a 32 GB USB"
date: 2015-09-02
forum: Installation &amp; Upgrades
---

### Post by Boyntonstu on 2015-09-02
I can boot from the USB to the install page.

Using just that page, I can browse the web but I cannot hear sound from my USB headset.

I cannot find an audio panel for microphone or speakers.

I would like to do the Lubuntu install directly on the USB without touching Win 7.

Can it be done?

Also, I cannot view the files on the Lubuntu USB drive.

I am getting close, but I am not there yet.

Not too shabby for a guy who started on a Wang 2200.

BTW  It seems that  Lubuntu goes onto the USB much quicker than Ubuntu.


I would apreciate some help.

---

### Post by Dennis N on 2015-09-02
You won't be able to do a regular installation of Lubuntu to the same USB drive that the installer is on, if that is what you are thinking. You will need another USB flash drive to install onto.

---

### Post by efflandt on 2015-09-03
Provided that you boot the live/install iso from different USB or DVD, you will want to use "Other" when it comes to partitioning to configure partition(s) how you want and there should also be a drop down list at the bottom of that screen where you would want to select the mbr of that device for grub (like sdx not sdx1, where x is a letter of the device). In BIOS you would set boot order to boot USB before hard drive, but in some cases you may still need to press a hotkey during BIOS splash screen to select the USB device during boot.

There are some other things you can do to minimize writing to it if it is flash memory, like look at /etc/fstab of the live/install system to see how to use tempfs (RAM) for /tmp (since that is erased any time your reboot anyway), and using noatime in mount options for / or other data partition(s) (so it does not write access time each time you just look at a file). If you have enough RAM you might either not use swap at all, or set swappiness to a low value [http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness) . I don't even use swap at all on my 2 GB RAM tablet PC which only has 32 GB SSD w/Win7 and boots Lubuntu or Ubuntu from 32 GB SD card, but do not use it that often or for anything that requires a lot of RAM because it only has a 1 GHz 2 core cpu. If you use ext4 file system, there is a way to disable journaling to reduce writing (or on USB flash or SD card, I have used ext2 which does not do journaling). But if you look up ways to optimize SSD, USB flash memory stick or SD card, etc. do not do TRIM (fstrim).

---

### Post by Dennis N on 2015-09-03
> I cannot find an audio panel for microphone or speakers.

After getting Lubuntu installed, I install these two pulse audio sound system packages:

[B]pulseaudio
pavucontrol
[/B]
These give you the best control of you various sound inputs and outputs with a nice gui. After installing, right click on the volume control icon and select "Settings". It's also accessible from Menu > Sound & Video > PulseAudio Volume Control.

---

### Post by sudodus on 2015-09-03
You have two options

1. Installing Lubuntu as discussed here. Efflandt's tips are very important.

2. Making a persistent live system.

See this link for some more details: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by Boyntonstu on 2015-09-03
Thanks.

Is NTFS-3G (or NTFS) a better format than Fat32?

I need to learn some of the terms used, but now I understand the YouTube video why he used 2 USB sticks for the install.

It seems to me that having a portable Lubuntu on a 32 GB USB would be useful for my two locations and 3 computers.

---

### Post by Dennis N on 2015-09-03
The installer has to be formatted FAT32; for the other USB, Lubuntu must be installed on a Linux file system like ext2, ext3, or ext4. A regular hard drive would normally use ext4. 

You could also create a NTFS or FAT32 file system on another partition to facilitate transfers of data files between Linux and Windows (or skip it and just use a FAT 32 USB to transfer files if needed).

Yes, such an install may prove convenient! If you usb 2.0, don't expect the same read/write/transfer speeds as a hard disk.

I looked up Wang 2200 - 1973?

---

### Post by sudodus on 2015-09-03
Live linux systems are often using the FAT32 file system.

Persistent live systems also need a file with a linux file system inside or a partition with a linux file system (often ext2 or ext4).

Installed linux systems need a partition with a linux file system. Ubuntu uses ext4. There is also a swap partition (with a special swap format).

A data partition with the NTFS file system is good for exchanging data with Windows. If you intend to use it in a USB drive, it must be the first partition, otherwise Windows cannot see it.

---

### Post by Boyntonstu on 2015-09-03
Wang 2200 had 16KB of core ram, 2 audio cassettes, each held 256 files of 256 Bytes, random access, 12" B&W monitor, all for $19,000!

I formatted my 32 GB USB with NTFS and it booted fine and I was able to web browse with it.  I am seeing different opinions regarding the best format for Lubuntu.  Confused???

At BestBuy yesterday, I bought a 32GB USB 3.0 for $11.95.  I plan to buy another tomorrow.

#1 for ISO, #2 for complete install.  Nothing on my  PC.

---

### Post by sudodus on 2015-09-04
The live system might boot from various file systems. FAT32 is a good alternative if you want it to work with various tools and in UEFI as well as in BIOS mode. Some tools overwrite the file system, so it does not matter how you formatted the drive before making it bootable. Other tools require one particular file system, and finally some tools work with several pre-formatted file systems.

-o-

Lubuntu when installed needs a linux file system for its root partition. If you let the installer select file system, you get ext4 (but other linux file systems work too). I do not think you can use NTFS for the root partition.

---

### Post by QIII on 2015-09-04
I've done several USB thumb drive installations (USB install media to USB OS drive).  Have to unhook the rest of the drives to be sure you don't mess up GRUB.  Those were all BIOS installs.  I don't know that UEFI would be much different, provided you do all the normal UEFI prep.  The install media was FAT, but the OS drives were just as if I were putting it on a hard drive.  ext4.

Don't expect very long life out of a USB flash drive installation, though.  I used mine sparingly, mostly for booting Ubuntu when I was away from my own machines.

Rasbian, a Debian variant for the Raspberry Pi, runs on MicroSD cards, if that's any indication to you.  (Mine has only /boot on the SD card and the OS actually runs on a USB hard drive.)

---

### Post by sudodus on 2015-09-04
If you intend to have a portable installed system in UEFI mode, and there is also Windows, there might be problems. Particularly Windows 10 is keen on tampering with the UEFI settings and exclude Ubuntu, but Windows 8 can do it too.

I have failed to make standard installed systems in USB drives survive, but I have made special systems, that work for me. See the following link and links from it.

[FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

---

