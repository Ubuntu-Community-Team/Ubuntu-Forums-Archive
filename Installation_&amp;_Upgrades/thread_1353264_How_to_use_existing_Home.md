---
title: "How to use existing /Home"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by sethhikari on 2009-12-12
I knew that I would be messing with my system so I made a / partition and a /home partition. Now I want to reinstall my system but I want to make sure that I know how to make the install just use my old home partition.

---

### Post by darkod on 2009-12-12
> **sethhikari said:**
> I knew that I would be messing with my system so I made a / partition and a /home partition. Now I want to reinstall my system but I want to make sure that I know how to make the install just use my old home partition.

In the installer you will have to select Manual partitioning option.
Select your / and click at the bottom on Change button. Set the filesystem as ext4 for example, tick the format box, select mount point as /.
Click on /home partition, select the filesystem same as the old /home (if it was ext3 not sure you are allowed to change it to ext4 like this), DO NOT TICK FORMAT BOX, select mount point as /home.
Do the same for swap partition and any other partition you have separate. That's it.

---

### Post by sethhikari on 2009-12-12
Thank you this makes sense. Just wanted to make sure before I started the process

---

### Post by acho on 2009-12-12
create 3 partition.... from your hdd. Then you must set one partition just for /home partition.... look like this:

ext3   | /
ext3   | /home
swap   | swap

if i want to reinstall it, try to not format your /home partition.

---

