---
title: "no ipod"
date: 2009-08-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by giorsat on 2009-08-23
I have a strange problem . my ipod is mounted on nautilus but nor banshee nor songbird are able to see it mounted.
what could I try?

---

### Post by Kobalt on 2009-08-23
What kind of iPod is this ?

---

### Post by ronacc on 2009-08-23
hey you're lucky , nothing sees my sandisk sansa e240 , not even lsusb :( . It works fine with my jaunty install on the same box .

---

### Post by PGScooter on 2009-08-23
> **ronacc said:**
> hey you're lucky , nothing sees my sandisk sansa e240 , not even lsusb :( . It works fine with my jaunty install on the same box .

Strange. I would have thought that Karmic would be fine for the sansa players because this fix for jaunty uses karmic packages:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

---

### Post by ronacc on 2009-08-23
> **PGScooter said:**
> Strange. I would have thought that Karmic would be fine for the sansa players because this fix for jaunty uses karmic packages:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

as I said it works fine in jaunty . This I think is something more than that bug . as I said even lsusb does not see it , only the usb controllers (2) it does not show in place>computer (although a 2nd cdrom which I DON"T have does show ??? . If I unplug the sansa and plug in a usb stick places>computer shows that as being the sansa ?? I can mount and read the usbstick but  it still shows as being the (unplugged) sansa .

edit: I think its time for another bug report .

edit: filed Bug #417823

---

### Post by PGScooter on 2009-08-23
> **ronacc said:**
> as I said it works fine in jaunty . This I think is something more than that bug . as I said even lsusb does not see it , only the usb controllers (2) it does not show in place>computer (although a 2nd cdrom which I DON"T have does show ??? . If I unplug the sansa and plug in a usb stick places>computer shows that as being the sansa ?? I can mount and read the usbstick but  it still shows as being the (unplugged) sansa .

edit: I think its time for another bug report .

how extremely strange! That sounds either like one super bug or a bunch of bugs. I'm sorry to hear about your trouble and I hope that it ends up working out.

---

### Post by jmmL on 2009-08-23
I can confirm this with a 5.5 generation 80GB iPod. Nautilus picks it up, banshee doesn't do anything, but rhythmbox at least sees it. When I try to sync with rhythmbox (which I much prefer to do with banshee because album art is broken for rhythmbox), the sync will be "successfully" completed, but nothing new will appear on the iPod.

---

### Post by giorsat on 2009-08-26
mine is a last generation ipod (normal, no touch) 8 giga
still with the latest updates nautilus sees it but banshee and songbird don't

> **jmmL said:**
> I can confirm this with a 5.5 generation 80GB iPod. Nautilus picks it up, banshee doesn't do anything, but rhythmbox at least sees it. When I try to sync with rhythmbox (which I much prefer to do with banshee because album art is broken for rhythmbox), the sync will be "successfully" completed, but nothing new will appear on the iPod.

---

### Post by jmmL on 2009-08-26
[COLOR=Silver]> **giorsat said:**
> mine is a last generation ipod (normal, no touch) 8 giga
still with the latest updates nautilus sees it but banshee and songbird don't

[/COLOR]  [COLOR=Silver]Do you mean one of the new nanos? As far as I know, there isn't support for that in linux generally, thanks to apple being evil with it's encryption scheme which remains unbroken. I think 1st gen nanos worked, but not 2nd or 3rd. Someone correct me if I'm wrong.[/COLOR]

On the other hand, mine should definitely work, as should any iPod older than it (built in 2006 or before).

---

### Post by giorsat on 2009-08-28
what a bunch of crap! ipod nanos are fully supported in ubuntu 904 and previous. it is a problem with some library. ipods are seen in nautilus but not in the music software like banshee or songbird

---

### Post by jmmL on 2009-08-28
Okay, retracted.
Try to keep it polite though; I was only trying to help.

---

### Post by lamalex on 2009-08-31
This is because of the switch to devicekit-disks. The media players in question are probably relying on HAL which has been more or less purged from the desktop.

---

### Post by alienclone on 2009-08-31
try gtkpod

EDIT: sorry just realized this was the Karmic Koala Testing forum, im not using or testing Karmic so ignore my suggestion if it isnt relevant.

---

