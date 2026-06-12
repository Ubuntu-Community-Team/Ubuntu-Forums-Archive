---
title: "[HELP] Install Ubuntu on USB .."
date: 2015-11-20
forum: Installation &amp; Upgrades
---

### Post by Petricevic on 2015-11-20
I want install Ubuntu on USB, but i have this error ..
[http://imgur.com/JjWGd4J](http://imgur.com/JjWGd4J)


Sorry for my bad English ..

---

### Post by sudodus on 2015-11-20
Welcome to the Ubuntu Forums :-)

1. What kind of installation do you want on the USB drive?

- a live system for testing
- a persistent live system, that is portable between computers
- a fully installed system, that can also be portable

See this link [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

2. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card


It makes it possible to give relevant advice. Otherwise we can only guess.

3. And please tell us what tool you were using, when you got the error output shown in the attached file in post #1! See the following link

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by yancek on 2015-11-20
The image you posted shows you are using some version of windows and are 'extracting' the iso.  That won't work.  You need to either burn the iso file 'as an image' to a DVD or use software such as unetbootin or pendrivelinux to create a bootable flash drive.  You would then put the DVD or flash drive in and reboot the computer setting either the DVD or the flash drive to first boot priority in the BIOS.  Boot the computer and you can then 'Try' or 'Install'.  If you want to install, you will likely need to first use the Disk Management tool in windows to shrink the windows partition to make room to install Ubuntu as a windows install will generally take up the entire disk.

---

