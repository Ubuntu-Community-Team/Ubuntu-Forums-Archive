---
title: "migrating transmission downloads to new ubuntu install"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Ananth on 2010-10-28
Hi,

I've recently installed new Ubuntu 10.10 alongside existing 9.10
There are some unfinished torrents in transmission, old install. I keep going back to 9.10 to let them complete. Is there a way to migrate the torrents to the new installation, 10.10, so that transmission resumes where it left off.

my download folder is common to both installations. (lvm, /mnt/downloads)

Thanks in advance.

---

### Post by cchhrriiss121212 on 2010-10-28
Just open the torrent file in 10.10 and save it in the same place, then Transmission should see the file is there, check the progress and resume downloading.

---

### Post by jamesisin on 2011-02-17
What if you don't have the original .torrent file?  Is there a simple way to make that migration without it?

---

### Post by jamesisin on 2011-02-17
Found it:

~/.config/transmission/torrents

---

