---
title: "I used 'Disk Creator' to make bootable usb thumb drive not what I expected"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by l6griffin on 2015-10-13
As the subject says used Disk Creator to install 15.04 on a 128GB thumb drive. What I want to is use it to back the HD in my laptop Now when I try determine what gets copied where, no lsdev, fstab, gparted, not installed. Try to install, not found. Should I have installed without disk creator?Are there some other programs I should be using.

---

### Post by Bucky Ball on 2015-10-13
Are you creating a persistence install to the USB? Are you sure you're not just creating install media from the USB device? Not sure if Disk Creator can create persistent installs or not ...

Have a look because if you are looking to run Ubuntu from the USB dongle like you would from a hard drive, and retain all files and changes on re-boot, persistence install is what you're after.

---

### Post by l6griffin on 2015-10-14
I wanted a persistence drive. I should have installed without using 'Disk Creator'. I'll redo the drive in the morn.

---

### Post by sudodus on 2015-10-14
Do you want to install Ubuntu to the thumb drive like a regular install to an internal drive? Or do you want a persistent live drive?

Both systems will have persistence (saved files, tweaks and installed programs will 'survive a reboot'). This is in contrast to a 'live only' system. See the following link for more details about different ways to run Ubuntu from a thumb drive.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

You find several tools to make ***persistent live drives*** at the next link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I made [mkusb](https://help.ubuntu.com/community/mkusb), and think it is a good tool, but there are several other tools that are good too. Try some them until you find one that works well for ***you*** :-)

-o-

If you want an ***installed system in the thumb drive*** you should first make a live drive (or persistent live drive) in a first thumb drive or a DVD disk, and boot from that drive. Then you should use ***ubiquity***, which is started by the ***desktop icon "Install Ubuntu"*** and install Ubuntu into a second thumb drive.

---

