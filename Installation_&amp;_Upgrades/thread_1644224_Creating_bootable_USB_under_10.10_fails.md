---
title: "Creating bootable USB under 10.10 fails"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by nedfunnell on 2010-12-13
Hello,
I am operating Ubuntu 10.10 installed to disk on a desktop and trying to create a bootable USB of the same to install on my netbook. I am using the instructions found [here]("https://help.ubuntu.com/community/Installation/FromUSBStick") but every time I try to create the bootable USB, it fails. I get various error messages, such as:

```
org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

```
An uncaught exception was raised:
[Errno 5] Input/output error
```

or others. I think I've seen four or five others. Once I got 80% finished then it failed with a generic error stating that creating the bootable disk failed. I've tried formatting the USB drive as ext3, ext4, NTFS, and FAT, but I always get failures. I am writing from a physical CD, the same one I used to install the 10.10 that I am posting from. 

Any suggestions?
Thanks!

---

### Post by C.S.Cameron on 2010-12-13
Flash drive should be formatted FAT32.
Use System/Administration/Startup Disk Creator.
Or try UNetbootin.

You might check the iso using MD5SUM.

---

### Post by Lynn X on 2011-07-16
My experience:
New Kingston 4mb drive fat32 (sdb) , Ubuntu Server 11.04 32bit iso
1) <system><administration><create startup disk> sdb1:"fail" | sdb: "fail" | :(
2) <system><administration><disk utility> formatted to fat16
3) <system><administration><create startup disk> sdb1:"fail" | sdb: "fail" | :(
4) <system><administration><gparted> recreated mbr, formatted to fat32
5) <system><administration><create startup disk> sdb1:"fail" | sdb: "fail" | :(
And the winner is . . .
6) <system><administration><disk utility> noticed 3 instances of the iso shown as "mounted"; unmounted all three.  Also checked "bootable" (for reasons I do not know)
7) <system><administration><create startup disk> sdb1:SUCCESS  :D
Its all magic to me

---

