---
title: "File System Compression"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by sibleytr on 2011-06-20
Hello Ubuntu Fans,

Question:
Looking for answer to drive compression options for Ubuntu.

Server Overview:
The server is a project archive server. The entire structure consist of old project that have been archived for historical reference.

Specs:
The entire / is on a RAID1 set of 500GB drives and the archived projects are stored on RAID1 set of 2TB drives that are being reference by the server as /media/vol1. Vol1 has two folders containing the archived projects according to the discipline of the project and each are shared to the windows based network.

Ubuntu Desktop
Release 10.04 (lucid)
2TB RAID1 set is EXT4

Again, does anyone have any idea how we can compress the entire 2TB RAID1 set?

---

### Post by psusi on 2011-06-20
You can't.

On the fly compression is one of the features of the up and coming btrfs filesystem, but it is nowhere near ready for production use.  There were once some patches floating around to add support for it to ext[234], but they never got merged into mainline.

---

### Post by sibleytr on 2011-06-20
That's what I was afraid of. Hate to go back and reformate for Win just to get the compression function.

Thanks for the quick reply.

---

