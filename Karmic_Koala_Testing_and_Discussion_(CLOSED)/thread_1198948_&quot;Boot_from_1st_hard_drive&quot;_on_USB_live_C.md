---
title: "&quot;Boot from 1st hard drive&quot; on USB live CD"
date: 2009-06-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-06-28
I have the live CD on a USB stick. If I boot from it, and choose "Boot from first hard drive", it reboots the USB stick. :confused:

---

### Post by jimv on 2009-06-28
USB sticks show up as hard drives, so technically, it IS the first drive.

---

### Post by phenest on 2009-06-28
Yes, but not much point in booting itself.

---

### Post by ronacc on 2009-06-28
not much point but probably unavoidable without making a special image for usb sticks . Its your bios that sees it as a hard drive .

---

### Post by phenest on 2009-06-28
Can't the software detect what drive it's running from and choose another instead?

---

### Post by ronacc on 2009-06-28
it should be able to but the livecd img expects to be running from a cd not an "hd" , file a bug on it .

---

### Post by phenest on 2009-06-28
[Bug 393153]("https://bugs.launchpad.net/ubuntu/+bug/393153")

Launchpad was experiencing some problems, and I ended up reporting this 4 times.

---

### Post by jimv on 2009-06-29
I think if you use Unetbootin to put the image onto the USB drive then you don't have this issue.

---

