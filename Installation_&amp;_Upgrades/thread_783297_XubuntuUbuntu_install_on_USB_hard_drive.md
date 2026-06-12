---
title: "Xubuntu/Ubuntu install on USB hard drive"
date: 2008-05-05
forum: Installation &amp; Upgrades
---

### Post by abcrossfrank on 2008-05-05
[FONT="Arial"]I am considering an install of Xubuntu 8.04 and Ubuntu 8.04 on an external USB hard drive.  I move the hard drive between two computers, one an old, weak, laptop with a 300 Mhz processor and 200 MB of RAM, the other more capable and able to run Ubuntu.  I’d like to install Xubuntu on the external hard drive for the laptop and be able to move the hard drive to the desktop an install Ubuntu there using the same partition for both installs, maybe even using the same files, I’m not sure.  Is this possible and am I going to run into problems or not?  Also, if I decide to uninstall these later, will I encounter big problems in doing so and removing any partitions created?  Should I be considering the Wubi install first for trying this out?  Thanks for any suggestions.[/FONT]

---

### Post by ChronoSphere on 2008-05-06
First, see if the laptop and PC can boot from a usb device. There should be a BIOS option. If the laptop is too old, then you might not be able to boot from usb.

The best way to check for this is to boot to a GRUB prompt (with the USB attached) and type "root (TABKEY" and see if hd1 shows up. If it does, then the usb is detected at boottime and you can use grub to boot from it. If only hd0 shows up, you obviously can't boot from hd1.

You can easily remove any partition on the usb drive with gparted.

---

### Post by abcrossfrank on 2008-05-08
So if I understand correctly, I cannot boot from, for example, the C: drive, but have most of my Xubuntu files on a USB drive unless I'm able to boot to the USB drive?  I'm completely new to Xubuntu and Ubuntu, so this is not something I'm familiar with.  Thanks.

---

### Post by Pumalite on 2008-05-08
This might help understand the problem:
[http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598961&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive](http://ubuntuforums.org/showthread.php?t=598787&highlight=boot+from+external+drive)
[http://ubuntuforums.org/showthread.php?t=598961](http://ubuntuforums.org/showthread.php?t=598961)
[http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/](http://www.ubuntuswitch.com/2006/08/01/installing-ubuntu-on-an-external-usb-hard-drive/)
[http://ubuntuforums.org/showthread.php?t=614913](http://ubuntuforums.org/showthread.php?t=614913)
[http://ubuntuforums.org/showthread.php?t=614863](http://ubuntuforums.org/showthread.php?t=614863)

---

