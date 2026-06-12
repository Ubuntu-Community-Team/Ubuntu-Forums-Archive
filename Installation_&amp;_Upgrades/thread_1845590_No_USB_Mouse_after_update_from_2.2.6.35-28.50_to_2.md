---
title: "No USB Mouse after update from 2.2.6.35-28.50 to 2.2.6.35-30.59"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by ozite on 2011-09-17
Ubuntu 10.10, 64 bit.  After installing normal updates through update-manager, I can't get any USB mouse to work (wired or wireless).  Restarting in previous kernel version, the mouse still works.  I tried 'sudo dpkg-reconfigure -a' and still no mouse.  There weren't any obvious errors about a mouse in the log files.

What should I try next to get a mouse working in the updated 2.2.6.35-30.59 version?

I upgraded to 11.04 and have all the updates installed.  I also tried installing proposed updates and this broke LIRC (again).  I still don't have a working mouse in the new kernel and MythTV doesn't work on the old kernel.

I tried running "sudo dpkg-reconfigure -a", but this stops after console fonts and after:

...
update-initramfs: Generating /boot/initrd.img-2.6.38-11-generic
stop: Unknown instance:
dpkg-maintscript-helper: error: couldn't identify the package


---
On booting into the older kernel, the mouse still works in 11.04.

```
htpc@htpc-EP35-DS3L:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
htpc@htpc-EP35-DS3L:~$ uname -r
2.6.35-28-generic

```

In earlier VMware conflict, I had 'blacklist usbhid' and 'blacklist snd-usb-audio' in /etc/modprobe.d/blacklist.conf. to get a Linksys CIT-200 working. I commented these line, then restarted.  The mouse is now working.

---

