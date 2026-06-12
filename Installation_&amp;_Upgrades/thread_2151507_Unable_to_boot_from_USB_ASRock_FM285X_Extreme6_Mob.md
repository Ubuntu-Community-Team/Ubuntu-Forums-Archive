---
title: "Unable to boot from USB ASRock FM285X Extreme6 Mobo"
date: 2013-06-04
forum: Installation &amp; Upgrades
---

### Post by tbagster on 2013-06-04
Hi all, I'm trying to boot into a USB Xubuntu install on my rig with the titular mobo. I'm using 2 Sandisk Cruzer 8 GB sticks (1 with the installation media via unetbootin and 1 to serve as HD). However when I attempt to boot in the Power/Reset/Dr. Debug LEDs shut off and the display loses signal within a few seconds. However, the board still seems to receive power. I've tried placing the stick in both USB 2.0 and 3.0 slots to no avail. 

Parts:
AMD A4 5300
Sapphire HD 7950 Vapor-X
Crucial Ballistix 8 GB
No HDD or CD/DVD drive

Here's a video illustrating the problem: [http://www.youtube.com/watch?v=ezd0gfsyCO8](http://www.youtube.com/watch?v=ezd0gfsyCO8)

Thanks in advance.

---

### Post by tbagster on 2013-06-05
x

---

### Post by tbagster on 2013-06-05
[COLOR=#000000]Any suggestions? ASRock technical support and Tom's Hardware seem to be stumped as well[/COLOR]

---

### Post by oldfred on 2013-06-06
On other model Asrock they had this issue.
 So to people with an Asrock Z77 Extreme4 motherboard: if you install Ubuntu, make sure the drives you are installing from and to are not connected to the Asmedia SATA ports!

Someone with a Gigabyte board had to shrink the install partition to less than 4GB for it to work.

Is UEFI/BIOS up to date? Are you trying to install in UEFI mode or BIOS mode? 

I only have nVidia, but sometime video issues:

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by tbagster on 2013-06-06
oldfred, thanks for the reply. I don't have any SATA drives on the system currently, trying to go all USB stick. Installation should be fine but the problem is I cannot even boot into the media, as my video shows. I'm thinking this may not be a fault with Xubuntu but with one of the pieces of hardware

---

### Post by oldfred on 2013-06-06
I have nVidia and I have to use nomodeset to get it to boot. It actually is booting but will not load video correctly without nomodeset. Not sure with AMD.

---

