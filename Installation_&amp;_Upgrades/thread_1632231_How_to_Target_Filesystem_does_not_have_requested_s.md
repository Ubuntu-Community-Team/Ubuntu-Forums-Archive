---
title: "How to: Target Filesystem does not have requested /sbin/init/"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by karenyyng on 2010-11-27
1. You will need a linux(ubuntu or slax) live that can be booted from a USB 

***instruction for putting linux on your USB using windows is: ***
[http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/#more-4156](http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/#more-4156)

***instruction for putting linux on your USB using linux is:** *
[http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)

They basically use the same piece of software UNetbootin


2. Boot to your USB linux OS and open a terminal

3. check for the name of the partition that is your ubuntu partition:

$sudo fdisk -l 

your partition 's name would be /dev/sdaX where X is a number like 1 or 2 or 3 etc. 
please be aware that if it's the problem of a failing hard drive this will not help you.

4. then type:

$sudo fsck -fy /dev/sdaX

where X is the number you found above
if you don't find the problem not being all fixed once, use fsck repeatedly.


5. reboot and find it being fixed 

Hope it helps, it fixed my friend's ubuntu.

---

