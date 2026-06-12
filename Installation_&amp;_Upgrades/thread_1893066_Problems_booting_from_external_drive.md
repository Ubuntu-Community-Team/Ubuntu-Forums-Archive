---
title: "Problems booting from external drive"
date: 2011-12-09
forum: Installation &amp; Upgrades
---

### Post by Colin@oxford on 2011-12-09
I am trying to get my Xubuntu to boot from an external (USB) drive.  I have copied the / partition (while a different OS was running) to the external disk as well as the /home partition.  I have ensured that GRUB is installed and all the boot files are in the right place.  Also fixed the fstab file in the external disk, which reads:

```

proc            /proc           proc    defaults        0       0
UUID=d8a16f20-a285-4bd2-95cf-c7690ccef525 / ext3 errors=remount-ro 0       1
UUID=e3e0901a-46b5-4596-9bbf-68ec9bb6a453 	/home           ext3   defaults    0       2

```

All seems OK until fairly late in the boot process when I get the message:

```

Mount point '/var/lock' does not exist. Skipping mount.
touch: cannot touch `/var/lock/.ramfs': No such file or directory

```

and a similar one about /dev/shm


I know I have succeeded in doing this before (with an earlier version of Ubuntu) so I must have forgotten something.  Can anyone suggest what I have missed?

---

### Post by cj13579 on 2011-12-09
Have you seen this...  [http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/](http://www.digizenstudio.com/blog/2007/06/14/watch-out-when-you-move-var-in-ubuntu/)

Can you manually create them if they don't exist? On my box /var/lock, /var/tmp, /var/crash and /var/mail all have sticky bits. not sure whether or not that makes a difference...

---

### Post by Colin@oxford on 2011-12-10
They do exist, this is the directory that would be /var:

```

drwxr-xr-x  2 root root  4096 2011-12-02 09:24 backups
drwxr-xr-x 24 root root  4096 2011-11-04 12:32 cache
drwxrwxrwt  2 root root  4096 2011-10-12 16:50 crash
drwxr-xr-x  2 root root  4096 2011-10-12 16:50 games
drwxr-xr-x 87 root root  4096 2011-11-06 07:38 lib
drwxrwsr-x  2 root staff 4096 2011-10-09 08:29 local
lrwxrwxrwx  1 root root     9 2011-12-07 12:28 lock -> /run/lock
drwxr-xr-x 18 root root  4096 2011-12-09 15:14 log
drwxrwsr-x  2 root mail  4096 2011-10-12 16:46 mail
drwxr-xr-x  2 root root  4096 2011-10-12 16:46 opt
lrwxrwxrwx  1 root root     4 2011-12-07 12:28 run -> /run
drwxr-xr-x  9 root root  4096 2011-11-01 05:37 spool
drwxrwxrwt  3 root root  4096 2011-12-07 12:47 tmp
drwxr-xr-x  2 root root  4096 2011-11-04 12:33 www

```

This is identical to the internal disc's /var directory.  The links in /run also exist as required.

I created the internal OS by copying it in the first place, so it not working on copying to another disc is very puzzling.

---

### Post by Colin@oxford on 2011-12-10
Ah well.  I have fixed it by wiping the partition and re-copying the files.  Something must have been left lying around that disrupted the boot process.

---

