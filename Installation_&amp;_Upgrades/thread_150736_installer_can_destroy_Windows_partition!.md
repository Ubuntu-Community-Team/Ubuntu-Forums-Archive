---
title: "installer can destroy Windows partition!"
date: 2006-03-26
forum: Installation &amp; Upgrades
---

### Post by Ninjagecko on 2006-03-26
Just wanted to give a warning: back up your data before using the partition utility in the installer!

It's worked fine in the past, but when I used it on my desktop it corrupted the Windows partition when I tried to resize the partition to roughly 500MB more than the amount of data I had.

Beware!

And please fix...

---

### Post by Ninjagecko on 2006-03-26
more info: apparently it corrupts bits and pieces of data, e.g. Windows still attempts to boot up but blue-screens saying its registry is corrupt.

symptoms: the resize operation never works, but instead returns an error screen saying it failed; attempts to resize the partition a second time result in a prompt saying "The minimum size you can use is 512 bytes" -- restarting the installer returns you to a normal prompt of "the minimum size you can use is 41.2GB [or whatever you have stored on your HD]"

---

### Post by Sef on 2006-04-07
Have you taken a look at Trinity Rescue Kit 3.1?  It can write to ntfs.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

