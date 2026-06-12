---
title: "How is /dev/usbdev#.# created?"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by andjohn2000 on 2011-03-30
Hello everyone,

I recently upgraded one of legacy system from ubuntu 9.04 to 10.04.

In ubuntu 9.10, I can see the /dev/usbdev#.# are there.

Example:
# ls -al /dev/usbdev*
crw-rw---- 1 root root 254,  0 Jan 29 03:27 /dev/usbdev1.1_ep00
crw-rw---- 1 root root 254,  1 Jan 29 03:27 /dev/usbdev1.1_ep81
crw-rw---- 1 root root 254,  2 Jan 29 03:27 /dev/usbdev2.1_ep00
crw-rw---- 1 root root 254,  3 Jan 29 03:27 /dev/usbdev2.1_ep81
crw-rw---- 1 root root 254,  4 Jan 29 03:27 /dev/usbdev3.1_ep00
crw-rw---- 1 root root 254,  5 Jan 29 03:27 /dev/usbdev3.1_ep81
crw-rw---- 1 root root 254,  6 Jan 29 03:27 /dev/usbdev4.1_ep00
crw-rw---- 1 root root 254,  7 Jan 29 03:27 /dev/usbdev4.1_ep81
crw-rw---- 1 root root 254,  8 Jan 29 03:27 /dev/usbdev5.1_ep00
crw-rw---- 1 root root 254,  9 Jan 29 03:27 /dev/usbdev5.1_ep81
crw-rw---- 1 root root 254, 10 Jan 29 03:27 /dev/usbdev6.1_ep00
crw-rw---- 1 root root 254, 11 Jan 29 03:27 /dev/usbdev6.1_ep81
crw-rw---- 1 root root 254, 12 Jan 29 03:27 /dev/usbdev7.1_ep00
crw-rw---- 1 root root 254, 13 Jan 29 03:27 /dev/usbdev7.1_ep81
crw-rw---- 1 root root 254, 14 Jan 29 03:27 /dev/usbdev8.1_ep00
crw-rw---- 1 root root 254, 15 Jan 29 03:27 /dev/usbdev8.1_ep81

After moving to ubuntu 10.04, I cannot find those usbdev anymore.
Can someone shed me light on this?
Is there a way to recreate those /dev/usbdev#.# in ubuntu 10.04?

Thanks

---

### Post by JerzyTarasiuk on 2012-11-28
Currently (and even before) there are /dev/bus/usb/<bus>/<device>
device files and seems they are sufficient to access USB devices.
<bus> and <device> are 3-digit numbers.
And I would like to know just reverse: what was purpose of  these 
/dev/usbdev#.# and /dev/usbdev<bus>.<device>_ep<ep>?
Seems /dev/usbdev<bus>.<device> (without the _ep part)
is the same as the /dev/bus/usb/<bus>/<device> and they had
symbolic links; but I know nothing about these with _ep<ep>.
Oh, also two notes: these symlinks can be created by UDEV rules;
and if needed, these UDEV rules can also change owner of these
device files (e.g. their group, to make a kind of devices accessible
for users belonging to some group - note crw-rw---- mode).

---

