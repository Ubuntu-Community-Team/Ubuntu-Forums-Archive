---
title: "Grub USB flash-drive -&gt; No bootable partition in table"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by c5f8 on 2007-07-29
I'm trying to dual-boot XP/Ubuntu with a USB flash-drive. I want Grub on a USB flash to start Ubuntu and XP to start otherwise. XP is on the 1st primary partition. Ubuntu is on the 2nd primary partition with its Grub loader.

I used the live CD to create a USB flash-drive Grub boot-loader. I access the flash drive by mounting it with the command:
mount /dev/sdb1 /media

I installed Grub onto the flash drive using:
root@ubuntu:/media# grub-install --root-directory=/media /dev/sdb1

Message was:
Installation finished. No error reported.
This is the contents of the device map /media/boot/grub/device.map:
(fd0) /dev/fd0
(hd0) /dev/sda
(hd1) /dev/sdb
Re-run grub-install if not correct.

I reboot computer with USB set as first device and got message:
"No bootable partition in table"

Using the live Ubuntu CD I see stage1/stage2 installed on the flash-drive in the directory:
/media/usbdisk/boot/grub/

In a terminal window I checked the location of Grub using:
sudo grub
find /boot/grub/stage1
computer returned:
(hd0,1)
(hd1,0)

I get a message "No bootable partition in table".

---

### Post by c5f8 on 2007-07-29
Here is an example of how a floppy can be used to boot Ubuntu.
[http://www.justlinux.com/forum/showthread.php?s=&threadid=130715](http://www.justlinux.com/forum/showthread.php?s=&threadid=130715)

What do I have to change to get the USB flash-drive to boot Ubuntu.

---

### Post by MQMike on 2007-07-29
I haven’t used the method you’ve used there.  But I have done it another way and wrote that up as a How-To, in case you might want to look at that:

How To Make GRUB Thumb Drive
[http://kubuntuforums.net/forums/index.php?topic=3081748.0](http://kubuntuforums.net/forums/index.php?topic=3081748.0)


(You will note that after getting the GRUB files copied to the UFD, I did a root – setup *to the UFD *.  Did you set up GRUB on your UFDs MBR?  (I first partitioned my UFD using Gparted, to be sure there would be a good MBR on it, etc.)  The other thing to note is the issue of drive-shifting, how your UFD may bump up to position hd0 when plugged in, and how I dealt with this by using a new Super Grub Disk GRUB that uses a usbshift function.  Etc.  It’s all there.)

---

### Post by c5f8 on 2007-07-31
Thanks for the response and the links.
My USB flash-drive now can boot Linux. 

The main links that helped me were:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_add_Grub_to_your_USB_thumb_drive).
[http://kubuntuforums.net/forums/index.php?topic=12995.0](http://kubuntuforums.net/forums/index.php?topic=12995.0)

First I followed bigponds steps
sudo grub
grub> find /boot/grub/stage1
grub> geometry (hd1)
grub> root (hd2,0
grub> setup (hd2)
grub> quit
sudo chmod -R 777 /media/usbdisk/boot/grub

Then I edited menu.list on the USF.
root=(hd0,1)	=/dev/sda2

Change to:
root=(hd1,1)	=/dev/sda2

---

### Post by MQMike on 2007-07-31
Glad you got it, and thanks for your feedback.

---

