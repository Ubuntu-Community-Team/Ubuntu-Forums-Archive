---
title: "Ubuntu 7.04 installation issues on laptop Asus Z96Jm"
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by Nodjo on 2008-03-30
I need to install Ubuntu 7.04 on my laptop and i'm encountering issues while trying to.

I have a Asus Z96Jm laptop with a dual core 2ghz and an ati radeon X1600.

I first tried the desktop CD, but after selecting "run and install ubuntu" from the menu, i get this error message:

udevd_event[3160]: wait_for_sysfs: waiting for '/sys/devices/pci0000:00/0000:00:1d.7/usb5-3/5-3:1.0/host3/target3:0:0/3:0:0:0/ioerr_cnt' failed

/bin/sh: can't access tty; job control turned off
(initramfs)


I tried applying this solution i could find, but it didn't work for me:
[http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control](http://ubuntuforums.org/showthread.php?t=421588&highlight=tty+job+control)

After that, I tried the alternate CD and i encountered a different problem: an error message that says the CD-Rom driver is not installed or mounted.


I then tried to use the mini ubuntu iso to perform a net install. unfortunately, my ethernet interface wasn't detected (driver problem?).


If you have any hints that would help me installing ubuntu 7.04, i'm eager to hear them...

Thank you in advance

---

### Post by warp99 on 2008-03-30
Re-burn the disc at a slower speed or you can order one at Ubuntu.com for free. Hope this helps.

---

### Post by Nodjo on 2008-03-31
Thank you, both the live cd and the alternate cd were badly burned... i could install it :-)

---

