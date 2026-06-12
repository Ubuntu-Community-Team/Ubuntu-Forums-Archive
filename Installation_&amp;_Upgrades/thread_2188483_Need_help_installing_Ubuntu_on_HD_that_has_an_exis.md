---
title: "Need help installing Ubuntu on HD that has an existing encrypted LVM linux distro"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2013-11-17
Hello,

I have an 80GB HD with another Linux distro installed (encrypted LVM) which is taking up the full drive. I'd like to dual boot with Ubuntu. Here's the current partition info:

```
Device           Type      Size            Used
---------------------------------------------
/dev/sda
   /dev/sda1    ext2	254MB         38MB
   /dev/sda5            79769MB     unknown
```	

Normally I could pull this off, but since sda5 is an encrypted LVM, I thought I'd better ask. Should I resize sda5 from within the other OS, or from the Ubuntu installation CD?

---

### Post by clay7 on 2013-11-17
Solved. I found some guides:

[http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](http://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu) 

[https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

---

