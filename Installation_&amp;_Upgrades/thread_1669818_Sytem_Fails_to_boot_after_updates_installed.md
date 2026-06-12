---
title: "Sytem Fails to boot after updates installed"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by drums907 on 2011-01-18
I am running Ubuntu Server Edition 10.04 LTS. After installing several updates, my server boots to a screen that has the Ubuntu brand and logo with 5 red dots beneath it. During the boot up it displays a message "The disk drive for /home is not ready yet or not present". It then says to press S to skip or M to Manually restore. The latter line disappears in a few seconds. I am unable to change consoles using the ALT + Fn keys (F1 - F. There is no way to log into the machine. I can reboot with CTL + ALT + DEL and that is all I can do when it gets to this condition.

I can read all of my drives from my Windows box that is networked in using SAMBA.

I can boot a LiveCD and see all of the drives and do file systems checks. These all come back clean.

>Update
Pressing M during the boot, I get the message
File System Check or Mount Failed
Starting Maintenance Console

typing mount at the prompt gives this response
/dev/sda4 on / type ext3
proc on /proc type proc
none on /sys type sysfs
none on /sys/fs/fuse/connections type fusectl
none on /sys/kernel/debug type debugfs
none on /sys/kernel/security type securityfs
none on /dev type devtmpfs
none on /devpts type devpts
none on /devshm type tmpfs
none on /var/run type tmpfs
none on /var/lock type tmpfs
none on /lib/init/rw type tmpfs
/dev/sda1 on / type ext3
/dev/sda3 on /data type ext3
/dev/sdb1 on /multimedia type ext3

I am not sure how to proceed to get this computer back to fully operational status.

---

