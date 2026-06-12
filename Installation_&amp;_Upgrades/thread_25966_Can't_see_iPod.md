---
title: "Can't see iPod"
date: 2005-04-11
forum: Installation &amp; Upgrades
---

### Post by bigblop on 2005-04-11
I have a third gen. 20 GB iPod USB2. When I start ubuntu the stop sign is turned on at some point in the startup so I guess it finds something.

But when I look for devices I can't see it, this is what I got:

Hard Disc (hdb1) [/]
Hard Disc (sda) [/media/usb0]
Hard Disc (sdb) [/media/usb1]
Hard Disc (sdc) [/media/usb2]
Hard Disc [/sys]


If I choose one of these:

Hard Disc (sda) [/media/usb0]
Hard Disc (sdb) [/media/usb1]
Hard Disc (sdc) [/media/usb2]

I get this error:

mount: I could not determine the filesystem type, and none was specified
Please check that the disk is entered correctly.


My iPod is FAT32 so I guees it should be possible to see it, what am I doing wrong??

---

### Post by kjerstib on 2005-04-11
What does dmesg say? It should tell you which of the usbs is the ipod. Have you edited your /etc/fstab? I have edited it so that it always mounts the ipod as /media/ipod.

---

### Post by bigblop on 2005-04-11
If I type dmesq in a shell I just get command not found.


I have not edited my fstab file have no idea what I should type in it.

---

### Post by dalbjerg on 2005-05-07
[QUOTE=bigblop]If I type dmesq in a shell I just get command not found.[/QUOTE] It was dmesg you should type, not dmesq.

---

