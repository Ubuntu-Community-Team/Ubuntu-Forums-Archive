---
title: "Filesystem for SSDs - Karmic"
date: 2009-10-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ianmillington on 2009-10-22
Hi

Acer Aspire One 110 with 8+8 Gb cards. Running jaunty UNR on cards formatted in Ext 2 - At the time I was advised to avoid journalling file-systems on the cards.

When Karmic is formally released the netbook will be upgraded. Is the advice I received still valid please i.e should I stick with ext2?

Thanks

Ian

---

### Post by Mighty_Joe on 2009-10-22
I've been searching for the same thing.  Is using ext2 justified for performance reasons?  [probably not]("http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/").  How about for endurance reasons?  [probably not]("http://www.storagesearch.com/ssdmyths-endurance.html").
I installed 9.04 using ext2 and ext3 to USB flash drives.  The ext2 drive had "volume not unmounted cleanly" errors nearly every boot ([Bug 125702]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702")).  The ext3 drive doesn't have this problem and *seems *faster.  I haven't used them enough to get anywhere near their expected end-of-life (and probably never will, according to the previous links).
Just to be safe, I save everything I want to keep on a NAS.

---

### Post by Saghaulor on 2009-10-22
You'll want to not use swap unless you absolutely must, as that will reduce the number of read/writes.

Ext4 is much better than ext3 as far as speed. If I remember correctly, it also performs checkdisk less frequently, which would be good for ssd's.

---

### Post by RTrev on 2009-10-22
I've yet to get into tweaking ext4, but I've been wondering if using noatime, nodiratime, and the like would be a good idea with an SSD?  I have no need to know the time a file was last read in most cases.

Do the netbook versions have these (or any other) tweaks to the file system for the SSD drives?

---

