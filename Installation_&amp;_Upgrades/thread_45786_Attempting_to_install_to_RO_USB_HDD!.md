---
title: "Attempting to install to R/O USB HDD!"
date: 2005-07-01
forum: Installation &amp; Upgrades
---

### Post by EchoBeach on 2005-07-01
This is my first attempt to install Linux.

I am trying to install HH onto a 20Gb HDD connected by USB2 in a disk caddy - by booting from an Install CD.
The last line in '/var/log/messages' after the base system install has failed, seems to suggest that it thinks the HDD is read-only.
How can I make the HDD Read/Write before the install?
Presumably I will need to bring up a 'command shell' and type something.  But what?

---

### Post by EchoBeach on 2005-07-12
I've had a look around the forums and reckon I need to remount the drive as Read/Write at the beginning of the install process.
I found a command in a post by rossriley thus:
```
mount -o rw,remount /path/to/mount
``` with the quoted example:
```
sudo mount -o rw,remount /media/sdb1
```

My question is:
How do I find out what the current '/path/to/mount' is for my USB drive?
What command do I need to use?
Thanks
Echo

---

### Post by EchoBeach on 2005-07-13
I've just had another go.
When the CD first boots up, I enter 'Expert' as a parameter - as recommended elsewhere.
I eventually reach the point in the process where it's about to install the base system.
At this point I 'Execute a shell' and type 'mount' and see the following list:
```
BusyBox v1 ...
~# mount
tempfs on / type tmpfs (rw)
none on /proc type proc (rw,nodiratime)
sysfs on /sys type sysfs (rw)
none on /dev type tmpfs (rw)
none on /.dev type tmpfs (rw)
none on /dev/pts type devpts (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/cdroms/cdrom0 on /cdrom type iso9660 (ro)
/dev/scsi/host2/bus0/target0/lun0/part1 on /target type ext3 (rw)
~#
```
'Exit' back and continue with the install; it fails again.
Back to the shell and I type 'mount' again.
There are no carriage returns or line feeds in the display (overlaid on the failed install screen), but I can see that the last line has changed:
```
/dev/scsi/host2/bus0/target0/lun0/part1 on /target type ext3 (ro)
```

Help ](*,)

---

