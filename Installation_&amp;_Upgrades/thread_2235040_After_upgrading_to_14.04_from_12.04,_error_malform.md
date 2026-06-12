---
title: "After upgrading to 14.04 from 12.04, error: malformed file"
date: 2014-07-18
forum: Installation &amp; Upgrades
---

### Post by Neale_Graham on 2014-07-18
HI I am a new user to the forum, my observations are:
a) I have just upgraded from 12.02 to 14.04, took most of the night, but it seemed to work. A few things were different.
I discovered I had a broken file pointer on one of my drives (corrupted name and rights) and and so tried to fix it with the command sudo touch /forcecheck.

When the machine reboot I received the error  "error malformed file, press any key to continue",  and the disk check program did not run.
removing the /forcecheck file also fixed the error message.

Perhaps the error message is related to the disk checking program which  i think is fstab.
Does anyone know how else I may be able to check my suspect disk. This disk does not contain the operating system, so I could remove it to check manually but not sure.

---

### Post by oldos2er on 2014-07-18
Post moved to its own thread.

---

### Post by kansasnoob on 2014-07-18
It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

---

