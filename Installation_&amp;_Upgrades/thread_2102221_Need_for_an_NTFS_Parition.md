---
title: "Need for an NTFS Parition"
date: 2013-01-06
forum: Installation &amp; Upgrades
---

### Post by Hawkway on 2013-01-06
I'm setting up a home server for the first time and thought I would make one of my HDD an NTFS drive because it seemed that it would be easier to share files with my Windows PCs on the network. However, when I noticed the slower transfer speed, and that Samba allowed me to access the ext4 partitions with no problem (and faster) I started to wonder.
 
Is there any real benefit to having an NTFS partition on a home server that will only be running Ubuntu Server (no dual boot)? Before I reformatted and had all ext4 partitions, I wanted to be sure I wouldn't regret it. Thanks.

---

### Post by darkod on 2013-01-06
No, there is no need for ntfs at all. The Samba shares do all the work to present the network shares to windows machines. The windows client doesn't care about the filesystem on the server.

---

### Post by coffeecat on 2013-01-06
> **Hawkway said:**
> 
Is there any real benefit to having an NTFS partition on a home server that will only be running Ubuntu Server (no dual boot)?

There is one very good reason **not** to use NTFS in this circumstance. If the partition were to suffer filesystem corruption, you do not have access to the chkdsk utility in Windows to fix it. There is no Linux utility that can completely replace chkdsk.

---

### Post by Hawkway on 2013-01-07
Thanks.  I was thnking I wouldn't need an NTFS partition, but wanted to be sure I wasn't missing anything.

---

