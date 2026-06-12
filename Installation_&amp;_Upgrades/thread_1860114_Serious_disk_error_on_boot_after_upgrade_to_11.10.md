---
title: "Serious disk error on boot after upgrade to 11.10"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by axe87 on 2011-10-14
Hi,

Having upgraded to 11.10 I'm getting a Serious disk error being reported each time I boot on an NTFS filesystem If I ignore the error the filesystem seems to mount OK.

The boot.log reports the following:

fsck: fsck.ntfs-3g: not found

fsck: Error 2 while executing fsck.ntfs-3g for /dev/sda2

mountall: fsck /media/archive [328] terminated with status 8

mountall: Unrecoverable fsck error: /media/archive

I've tried running ntfsresize -fi /dev/sda2 and no errors are reported.

Is this as simple as I need to change the pass value to 0 in fstab? If so what changed in 11.10?

---

### Post by scuter on 2011-10-14
I have the same problem, I just wait if the anyone do solution for it. Sorry for my english,...
edit: on the hard disc is a few fail sector, it could be the problem

---

### Post by Hakunka-Matata on 2011-10-14
ntfs-3g is a package, looks like it is not installed.

This is what I have on it, should install that package by default I thought.  

```
das@1110beta2:~$ sudo apt-get install ntfs-3g
[sudo] password for das: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ntfs-3g is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
das@1110beta2:~$ 


```

---

### Post by oldfred on 2011-10-14
Ubuntu cannot do chkdsk on a NTFS partition. Its fsck only works on Linux partitions. So pass should be 0. But you may need to run chkdsk periodically yourself as system will not do it automatically nor will Windows. You need a Windows repairCD to run the chkdsk then.

man fstab
 > If  the sixth field is not present or zero, a value of zero is returned and fsck will assume that the filesystem does not  need  to be checked.


---

### Post by scuter on 2011-10-14
> **oldfred said:**
> Ubuntu cannot do chkdsk on a NTFS partition. Its fsck only works on Linux partitions. So pass should be 0. But you may need to run chkdsk periodically yourself as system will not do it automatically nor will Windows. You need a Windows repairCD to run the chkdsk then.

man fstab

Yeah, you are right, I just change it and it work, thank you. But it is necessary change disk, because bad sector is dangerous.

---

### Post by GhodMode on 2011-10-15
I ran into this problem as well.  Changing the sixth field in the fstab to '0' fixed it for me.

Since it has worked for several Ubuntu versions, I wonder exactly what changed.

If fsck doesn't check NTFS file systems, shouldn't it fail gracefully?  

Was there an fsck.ntfs before the upgrade?  What did it do?

Currently (11.10), fsck exits with a code of 8.  According to the man page, that's an "Operational Error".

My guess is that fsck.ntfs was part of the ntfs-3g package and has been removed.

---

