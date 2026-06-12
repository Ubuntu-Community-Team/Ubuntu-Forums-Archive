---
title: "Installing Ubuntu 1.4-problems"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by luckyme_7 on 2008-10-06
I am currently trying to install Ultimate Ubuntu 1.4 off a disk onto my computer which is using Ubuntu 7.10. Every time the installer will begin and will ask whether i want to install it, open it in graphics mode, install with driver update CD etc, but my keyboard seems to become disable there. Ubuntu 1.4 then opens up and begins loading but afterward i receive the following messages:

udevd-event [1937]: run_program: '/sbin/modprobe' abnormal exit


then over and over again:

end_request: I/O error,dev fdO, sector 0
Buffer I/O error on device fdO, logical block 0

Does anyone know any way i can fix this so ubuntu can install? I have tried plugging in my floppy drive as i had read it may fix it, but it didn't work. 
Thankyou.

---

### Post by luckyme_7 on 2008-10-06
Update:
Once it stops sending these messages it states this:

Busybox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built in shell(ash)
Enter'help' for a list of built-in commands.
/bin/sh:can't access tty:job control turned off
(initramfs) _

---

### Post by Sef on 2008-10-06
Here are some command lines for [checking for bad blocks]("http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command").

---

