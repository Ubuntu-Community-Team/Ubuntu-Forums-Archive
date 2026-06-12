---
title: "[SOLVED] Can't install ubuntu to a USB stick"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by SlickRick on 2008-11-03
When I click format, it comes up with an error
```
Unable to create a partition table:
Warning: Device /dev/sdi has a logical sector size of 2048.
Not all parts of GNU Parted support this at the moment,
and the working code is HIGHLY EXPERIMENTAL.
```
What can I do?

---

### Post by C.S.Cameron on 2008-11-03
Are you doing a full install of Ubuntu from CD to flash drive?
Does this happen during manual partitioning?

---

### Post by SlickRick on 2008-11-04
Basically, I found my old ubuntu hardy live CD and wanted to install it on a usb stick. I currently have intrepid (upgraded from hardy).
I don't know anything about manual partitioning.

---

### Post by n6yga on 2008-11-04
Try this site:
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

You may find everything you need to know there...



Mark.

---

### Post by C.S.Cameron on 2008-11-04
How are you installing to USB?
Are you using 8.10's install to USB option, (cd-creator), or are you doing a normal Install from the CD?

---

### Post by SlickRick on 2008-11-04
System>Administration>Create a USB Startup Disk
I'm on 8.10 and installing with a 8.04 disk. Although installing isn't the problem. It says I need to format my usb but I can't.

That website doesn't help

---

### Post by n6yga on 2008-11-04
> **SlickRick said:**
> System>Administration>Create a USB Startup Disk
I'm on 8.10 and installing with a 8.04 disk. Although installing isn't the problem. It says I need to format my usb but I can't.

That website doesn't help

Sorry, bud. Just trying to brainstorm for ya...


Mark.

---

### Post by C.S.Cameron on 2008-11-05
Usb-creator does not work installing 8.04.1 for me.
There is a flaw in 8.04.1's casper that prevents persistence.

---

### Post by sandy8925 on 2008-11-05
> **SlickRick said:**
> System>Administration>Create a USB Startup Disk
I'm on 8.10 and installing with a 8.04 disk. Although installing isn't the problem. It says I need to format my usb but I can't.

That website doesn't help

how can you be on 8.10 and installing with a 8.04 disk ?

use the 8.10 live cd if you have it. i used that to installed to usb and it runs great !

---

### Post by SlickRick on 2008-11-05
I don't have the 8.10 live cd because I upgraded from 8.4 to 8.10 with the update manager. All I have is the 8.4 live cd and I wanted to see if i could install ubuntu on my usb without having to burn a 8.10 CD.

---

### Post by C.S.Cameron on 2008-11-05
Unibootin works ok for installing 8.04.1 to USB, but it will not be persistent without some work.
To make 8.04.1 persistent see here:
[http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/)

---

### Post by SlickRick on 2008-11-05
Working to get stuff working is what linux is about ;}
However, the method in the link requires mounting which I've had trouble with before. Anyway, I don't need this that much, so I think I'll just leave it. Maybe get puppy because I've had success with installing that using virtualbox but I wanted to install ubuntu since I's my preferred distro.

---

