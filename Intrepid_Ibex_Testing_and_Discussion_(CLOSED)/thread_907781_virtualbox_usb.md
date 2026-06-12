---
title: "virtualbox usb"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by FishRCynic on 2008-09-01
simple solution

from

[http://virtualbox.org/wiki/User_FAQ](http://virtualbox.org/wiki/User_FAQ)


USB on openSUSE: Add the following entry to /etc/fstab:

none  /proc/bus/usb  usbfs  auto,busgid=XXX,busmode=0775,devgid=XXX,devmode=0664  0  0

Replace XXX by the group ID of the group vboxusers. You can determine this value by executing

grep vboxusers /etc/group

Of course, the current user should be member of that group. After the next reboot, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user of the vboxusers group. 

just change openSUSE to Intrepid Ibex :-)

maybe a
$ sudo mount -a 
to get things rolling without rebooting

hope this helps

---

### Post by jbernardo on 2008-09-24
Unfortunately for me that didn't fully help. Virtualbox can see the USB devices, but they all show up as unavailable (dimmed). I really wanted virtualbox only to be able to update a TomTom one maps.

---

### Post by jbernardo on 2008-09-24
Ok, my mistake. it now works - after I corrected a mistype in the fstab line.
Sorry.

---

