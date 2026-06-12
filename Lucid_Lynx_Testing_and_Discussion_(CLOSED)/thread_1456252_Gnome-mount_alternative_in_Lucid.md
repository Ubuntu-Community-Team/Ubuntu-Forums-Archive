---
title: "Gnome-mount alternative in Lucid"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by n0_mad on 2010-04-16
Hi,
i was using gnome-mount to automount drives but in lucid it was removed.
So is there any alternatives in lucid except editing fstab and programs that do so?

Gnome-mount is a program which mounts disks using the same facilities as when mounting a disk as a normal user through Nautilus. There is no need to setup mountpoints or filesystems. This is particularly interesting if you want to use the automatically created mountpoints instead of manually specifying them for each disk.

---

### Post by nilarimogard on 2010-04-17
Try Pysdm to be able to set automount. Just for mounting you can also use Disk Utility.

Or, if you just want to set up automount for NTFS drives, there's [a script which does this automatically]("http://www.webupd8.org/2010/04/ubuntu-script-to-automatically-mount.html").

---

### Post by n0_mad on 2010-04-17
..."except editing fstab and programs that do so" 
Every time i ask this question somebody offer me fix fstab one way or another.
But thanks for reply.
Anyway i found solution for this problem, it is possible to use 
gvfs-mount -d /dev/name
It will mount drive to /media/<label> without asking root password. You can add this to startup programs.

---

