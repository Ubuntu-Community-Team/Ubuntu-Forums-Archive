---
title: "error: attempt to read or write outside of disk `hd0'"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by malakar.subhendu on 2013-07-10
I tried to check my hard disk status via the hard disk checking tool of the BIOS. But due to overheating, it stopped in the middle. Now when i tried to start ubuntu, it won't start. It sayas that:

> error: attempt to read or write outside of disk `hd0'

Then it goes into something like grub-rescue and shows initramfs >
I think it occured due to the abnormal termination of the HDD checking tool.

This is a dual boot machine, and it easily can load windows. I've tried boot-repair tool, but its of not much use. Although it removed the error message, but it still comes on the screen before grub loading. And now the boot screen goes on and on. 
The link of boot-repair is:
[http://paste.ubuntu.com/5862326](http://paste.ubuntu.com/5862326)

Please help. I don't want to reinstall Ubuntu.

---

### Post by ajgreeny on 2013-07-10
Try booting to a live DVD or USB and then run sudo e2fsck /dev/sdx# where sdx# is your root partition of Ubuntu.

That will check the filesystem and may find and correct any problems for you.

---

### Post by malakar.subhendu on 2013-07-10
@ajgreeny:
It showed that there were some problems in the inode of some files, it fixed them, but the problem is still there.

---

