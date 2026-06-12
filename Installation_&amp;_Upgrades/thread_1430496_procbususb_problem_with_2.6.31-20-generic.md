---
title: "proc/bus/usb problem with 2.6.31-20-generic"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by speed32219 on 2010-03-15
I did a fresh install on a working HTPC (2.6.31-15-generic).

lsusb: 
Bus 003 Device 002: ID 15c2:0043 SoundGraph Inc.

Trying to setup a remote control to work, I ran this command: 

sudo mount -t usbfs none /proc/bus/usb 

(to see if the usbhid drivers were loaded for device 15C2:0043.) 

This is the error i get back:

mount: mount point /proc/bus/usb does not exist.


Here is my /etc/fstab.  Layout looks identical to a previous backup of the system as well as another htpc that I have in the bedroom with the same remote. 

cat /etc/fstab:
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9b8cbace-5577-4b79-8885-7012d70cbc58 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=9a359247-57d8-46b1-aca4-92a8a65ec73c /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=32f440ff-926a-49cc-b9af-a63939ff0ee6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
 
I also ran this to add the usbfs by editing /etc/fstab and rebooting but still no joy, can not find/mount file system error.
~$: echo 'none /proc/bus/usb usbfs auto,devmode=0777 0 0' >> /etc/fstab 

Any suggestions, I am about ready to install a down rev kernel to see if it comes back to life.

I forgot that under Karmic the procedure for remote controls had changed.  I loaded a CF card that I used before (2.6.31-20-generic) and my remote came back to life, but I do not have the processes I used to get it to work from intrepid to Karmic.  I need to find out where I wrote down my sequence for Karmic, I hope I did, took me awhile to get everything working properly.

---

