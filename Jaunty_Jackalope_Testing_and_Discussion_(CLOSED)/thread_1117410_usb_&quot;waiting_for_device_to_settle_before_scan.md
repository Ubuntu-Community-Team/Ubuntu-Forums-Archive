---
title: "usb &quot;waiting for device to settle before scanning&quot;"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mud.Knee.Havoc on 2009-04-05
I'm experiencing a new problem with Jaunty that did not exist under Intrepid.  I have a Sansa e270 mp3 player that connects via usb cable and is seen as usb storage.  After upgrading from 8.10 to 9.04 amd_64, it would no longer mount.  I eventually reinstalled 9.04 (thinking that something got fubar'd during the upgrade), but the problem still remains.  I've got powered and unpowered usb ports - this exists with all of them.

Here's what dmesg gives me re. the mp3 player.

```
[ 2043.365473] usb 2-2.4: new full speed USB device using ohci_hcd and address 8
[ 2044.197475] usb 2-2.4: not running at top speed; connect to a high speed hub
[ 2044.215539] usb 2-2.4: configuration #128 chosen from 1 choice
[ 2044.231613] scsi10 : SCSI emulation for USB Mass Storage devices
[ 2044.231804] usb-storage: device found at 8
[ 2044.231805] usb-storage: waiting for device to settle before scanning
```

Any ideas?  I'll be submitting a bug report if it is actually a bug. :)

---

### Post by Mud.Knee.Havoc on 2009-04-20
Replying to my own post here... but for reference, a patch has been submitted to launchpad.net:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/355998)

apt-get install build-essential devscripts
apt-get build-dep libgphoto2
apt-get source libgphoto2
wget [http://launchpadlibrarian.net/25783305/libgphoto_sansa.diff](http://launchpadlibrarian.net/25783305/libgphoto_sansa.diff)
patch -p0 -i libgphoto_sansa.diff
cd libgphoto2-2.4.2
debuild -uc -us
cd ..
dpkg -i libgphoto2-2_2.4.2-0ubuntu4_i386.deb

Or, if you're running 64-bit Ubuntu, the final line will be 
dpkg -i libgphoto2-2_2.4.2-0ubuntu4_amd64.deb

---

