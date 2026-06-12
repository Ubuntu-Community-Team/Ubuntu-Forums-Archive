---
title: "Installing External USB Raid Harddrive Gutsy Gibbon"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by merrydown on 2007-12-05
Hi, I am attempting to build a server for a client - I must have been mad to take it on as I am pretty far off piste.  I have done ok-ish till now and I am stumped.   keep trying to install a Lacie Biggest Quadra 4TB  USB drive into the gutsy gibbon system I have installed (manual lamp basically - using webmin) and I get errors no matter how I approach it.  The drive is set up to be raid 5 and should give a 2TB usable device

On Server startup I get:
[206.436201] usb 6-5: device descriptor read/64. error -110
[221.657765] usb 6-5: device descriptor read/64. error -110
[236.999262] usb 6-5: device descriptor read/64. error -110
[252.220824] usb 6-5: device descriptor read/64. error -110
[257.477936] usb 6-5: device descriptor read/64. error -110
[262.605115] usb 6-5: device descriptor read/64. error -110
[267.862217] usb 6-5: device descriptor read/64. error -110
[272.989394] usb 6-5: device descriptor read/64. error -110

At that point the drive can't be seen on the partition manager through webmin.  If I restart the drive it reappears.  I am trying to mount the drive into a particular folder in the web part of the server to be used as a folder where thousands of images will be stored.  My fstab is as below (the drive reports as sdc and the (linux ext3) partition as sdc1 - I have it referenced currently by id):

------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=57bd6198-9dd0-4e97-9ccf-db53a8a2763a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6592f65b-a815-41f3-839f-1f4e0e68e558 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=57bd6198-9dd0-4e97-9ccf-db53a8a2763a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=6592f65b-a815-41f3-839f-1f4e0e68e558 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
UUID=fd57fb53-63df-481a-9f6a-29623442836b  /var/www/html/imageBank/2007091701  ext3  user,grpid,suid,errors=continue,exec,nodev  0  0

--------------------------------------------------------------------------

I have been stumped at it for 2 weeks and I especially don't know what I am doing now!!!  Any help so gratefully received you wouldn't believe :)

---

### Post by merrydown on 2007-12-05
Can anyone even point me in the right direction?  I keep going around in circles...

Many thanks in advance...

---

