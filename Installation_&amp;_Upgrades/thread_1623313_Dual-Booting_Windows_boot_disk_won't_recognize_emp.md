---
title: "Dual-Booting: Windows boot disk won't recognize empty partition"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by lazypeterson on 2010-11-16
I've had Ubuntu 10.10 installed for a while and I recently cleared a partition to install Windows XP. However, when I load from the Windows XP boot CD, I get "7379one MB disk 0 at ID 0 on ?Bus 0 on atapi(Setup cannot access this disk)". I've tried just about everything. 

Here's what my gparted looks like:

[img]http://i51.tinypic.com/24c8dxk.jpg[/img]

Any suggestions?

---

### Post by psusi on 2010-11-16
IIRC, xp doesn't have the AHCI SATA driver built in, so you need to feed it the driver disk ( actual floppy, if you still have one of those ).

---

### Post by lazypeterson on 2010-11-16
Ah, thank you. Is there any way to load it without a floppy?

Edit: think I found something, [link]http://aps2.toshiba-tro.de/kb0/TSB85017Z0000R01.htm[/link]

I'll give that a shot. I appreciate your help.

---

### Post by lazypeterson on 2010-11-16
Well I tried both the floppy and a patched setup disk to no avail. With the floppy I kept getting blue screens saying the setup was aborted in order to prevent harming my computer. 

I don't know what to do at this point.

---

### Post by oldfred on 2010-11-16
Please do not have duplicate threads on the same topic.

See
[http://ubuntuforums.org/showthread.php?t=1612226](http://ubuntuforums.org/showthread.php?t=1612226)

---

