---
title: "installation cd-rom counldn't be mounted"
date: 2015-08-17
forum: Installation &amp; Upgrades
---

### Post by Phezz on 2015-08-17
I was attempting to install a 'server' Ubuntu 14.04 and failed. 
After booting to the installer, the system failed a found 'mount' commands (which quickly flashed by) and then handed me the error in the subject line.  

I am using a Lenovo w541 (but I've had the problem on other Lenovo hardware as well - I blame their bios firmware)

I found this post explains the problem and solution.  

[http://serverfault.com/questions/685302/unattended-installation-of-ubuntu-from-usb-drive-not-mounted-correctly](http://serverfault.com/questions/685302/unattended-installation-of-ubuntu-from-usb-drive-not-mounted-correctly)  

In the interest of avoiding dead links to useful information: 

>  I think it comes from the debian-installer that, at an early stage of the installation, tries to mount a partition from the first drive on /media. And then mounts the USB drive in /cdrom.  In the above cases, the hard drive is detected later during the installation process, making the USB drive the first drive and therefore mounting it on /media and not on /cdrom.  

The solution is simply to remount the usb device as '/cdrom':  

1 - umount /media/  

Identify the USB drive sdX in the device list (sda, sdb, sdc, …)  
2 - ls -l /sys/block/sd* | grep usb  

Mount the USB drive to /cdrom  
3 - mount /dev/sdX /cdrom

---

