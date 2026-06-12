---
title: "[Jaunty] Today's problems- User switcher, floppy access"
date: 2008-11-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kevbert on 2008-11-08
When is the [[COLOR="Red"]bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255651") for sorting out Floppy drive access going to be officially fixed ? It doesn't work in Intrepid and by default Jaunty.  To make the floppy accessible every time you boot you have to modify two files:
Fstab - add to the end of the file
```
/dev/fd0 /media/floppy0 auto rw,auto,user,sync 0 0
```
/etc/modules -add to the end of the file
```
floppy
```
Thanks to alienexplorers for this solution.
*** Unfortunately I still get unable to mount floppy as mount point does not exist and org.freedesktop.DBus.Error.NoReply  occassionally ***
The other problem seem to be User switcher. There seem to be a problem loading this module as the username does not always appear in the righthand corner of the top panel and a message may be displayed.  The error message seem to be random in what is displayed and does not always appear when the username is not displayed. This error seems to be very hit and miss as to whether it occurs (I've had it occur four times in nine reboots).  This is on 32 bit Jaunty (yet to try on 64 bit).

---

### Post by Bert Mariën on 2009-03-28
Editing the /etc/modules file worked for me in Interpid.
It does no longer in Jaunty (beta).
The most appropriate bug for this is [https://bugs.launchpad.net/ubuntu-doc/+bug/330314/](https://bugs.launchpad.net/ubuntu-doc/+bug/330314/)

---

### Post by Dr. C on 2009-03-29
I just installed the Jaunty beta 64 bit and was pleasantly surprised that the floppy (3.5in) actually worked fine.

---

