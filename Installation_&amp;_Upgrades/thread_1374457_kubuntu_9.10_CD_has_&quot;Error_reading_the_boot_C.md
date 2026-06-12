---
title: "kubuntu 9.10 CD has &quot;Error reading the boot CD&quot; on Acer X1800"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by albertkao on 2010-01-06
The kubuntu 9.10 CD boots normally and present all the install options on Acer computer M3202 (AMD Athlon II X3 triple-core processor) and M3100 (AM3100-UD5200A. AMD Athlon64 x2) but not X1800 (AX1800-E9232. Intel Core2 Quad Processor Q8200).
The "804200EF" number appears on the top left corner of the screen.  The error screen with the red title "I/O error" and the message "Error reading the boot CD. Reboot". appear.
Windows 7 is running ok on Acer X1800 so its hardware should be ok.
Please help.

BTW, the System Rescue CD 1.3.4 does not work on Acer M3202 and X1800 but works correctly on M3100.

---

### Post by dstew on 2010-01-07
Some CD drives are more "fastidious" than others. That is, small errors in the CD which other drives tolerate can make a disk unreadable in others. Sometimes a firmware update can make the drive more forgiving. Sometimes making a better disk will help. You should burn the disk at a slow speed, no more than 4x. Sometimes cleaning the lens in the disk drive is helpful.

Are you trying to use a Kubuntu Live CD? It sounds like you never got to the point where the Live CD kernel boots, but if you did, you should know that sometimes the Live CD kernel has trouble with certain hardware. You can try kernel parameters to try to get it to work, but if you just want to install Kubuntu, download and burn the [Alternate Install]("http://releases.ubuntu.com/kubuntu/karmic/") CD. It installs the same Kubuntu desktop as the Live CD, but uses a text-based installer that is a little more forgiving of hardware quirks.

There are also ways to install without a CD. If you have a downloaded .iso, and you have a working Ubuntu installation, you can [copy it to a USB stick using **usb-creator**]("https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Linux"). Then, boot the USB stick. There are also other ways to make a Live USB stick from Windows and Linux.

---

