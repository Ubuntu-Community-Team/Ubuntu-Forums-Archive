---
title: "Cannot burn ISO onto CR-RW"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by ZxhPeter on 2011-05-18
**I am unable to burn the ubuntu-11.04-desktop-amd64.iso onto a rewritable CD (CR-RW).**
Plain TDK 700MB CD-RW discs (I have tried 2 of them); blanking succeeded (there was a previous iso content on the CDs), writing iso (either with Brasero or other program) seemingly succeeded, but checking failed (either checking the crc with "dd if=/dev/cdrw | head -c 732112896 | md5sum", either mounting the CD and comparing the contents).

$ stat --format=%s ubuntu-11.04-desktop-amd64.iso
732112896

$ dd if=/dev/cdrw | head -c 732112896 | md5sum
dd: reading `/dev/cdrw': Input/output error
1383496+0 records in
1383496+0 records out
708349952 bytes (708 MB) copied, 182,957 s, 3,9 MB/s
6dff11fd595aa999bcd042ed0940279c  -

...
$ diff -r /mnt /media/Ubuntu\ 11.04\ amd64
diff: /media/Ubuntu 11.04 amd64/casper/filesystem.squashfs: Input/output error

Tried other CD writer, and even other operating system. Results are the same.

Maybe some capacity problem?.. This ISO is a bit too large?..

---

### Post by Dutch70 on 2011-05-18
Edit: I must have overlooked the (708MB), that is definitely too large. There should be bug reports on it.
The one *(64-bit PC (AMD64) desktop CD)* on this page is 698MB & should be fine.
[[COLOR="Red"]http://releases.ubuntu.com/natty/[/COLOR]]("http://releases.ubuntu.com/natty/") 

The .iso should be under 700MB. I have came across some that are too large lately though, just make sure it's under 700MB. 
K3b is a much better program for burning .iso's.

If you have a usb stick, it's much faster & easier. It only needs to be 1GB, even though the site says 2GB minimum. If you do have one that you can use, even if you have to borrow it. You can use start up disk creator or Unetbootin to create the usb stick.

---

### Post by tommcd on 2011-05-19
> **ZxhPeter said:**
> **I am unable to burn the ubuntu-11.04-desktop-amd64.iso onto a rewritable CD (CR-RW).**.
If you still have problems, then try burning the iso to a regular CDR, not RW. Rewritable CDRWs can become unreliable with repeated use. Also be sure to burn the iso to CD at the slowest possible speed.

---

