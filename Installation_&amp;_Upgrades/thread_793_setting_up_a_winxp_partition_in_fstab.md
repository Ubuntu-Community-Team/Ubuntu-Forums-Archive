---
title: "setting up a winxp partition in fstab"
date: 2004-10-15
forum: Installation &amp; Upgrades
---

### Post by snowx1000 on 2004-10-15
Anybody know how to setup a winxp partition in fstab so the normal user can view the mount?  Thanks.

---

### Post by HungSquirrel on 2004-10-15
Here's an example from mine.  I did it like this so my user could load MP3s from my NTFS partition.  Of course, change the partition device and mount point to your needs.

```
/dev/hdb1	/storage	ntfs	ro,user,users,uid=1000	0 0
```

---

### Post by tsykoduk on 2004-10-15
here is the fstab entry that I use

/dev/hd&lt;whatever&gt; /&lt;some mount point&gt; nfts defaults, 0 0

This only works read only. I have never taken the time to get read-write ntfs working

---

### Post by HungSquirrel on 2004-10-15
When I use 'defaults' I cannot read from the drive under my normal user account.

---

### Post by snowx1000 on 2004-10-15
Thanks alot HungSquirrel &amp; tsykoduk.  I went with HungSquirrels method.  Now I can access windows as user.  Yay (giant movie collection).  Ubuntu seems to be one of the speediest distros I have used.  AMD64 is mighty good.  The community is also doing nicely :-)

---

### Post by WebLOCH on 2005-10-31
+++++++++++++++++++++++++++++++++++++
Please ignore this post:
I didn't check which forum I was in, I use Breezy
Mods please delete this post!
+++++++++++++++++++++++++++++++++++++

Hey guys...

  Just taken ubuntu mainstream on my harddrive, re-arranged all the partitions so windows takes up about 30gb including data files.  In doing so I took the advice of a friend and created three linux partitions;   "/"   "/boot"  "/home"

  Now after logging in I edited "fstab" to mount the partitions to "/home/windows/" but then attempted to remount but it always tells me there is no such mount point :P

  I know for a fact the folder exists, I am also referencing it correctly as it works fine if I specify "/mnt/whatever".

  I was wondering if any of you knew what the problem was?  Thanks in advance.

---

