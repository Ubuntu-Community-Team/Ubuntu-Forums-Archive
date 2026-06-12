---
title: "installation fails by migration assistant"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by hadian on 2011-04-30
Hi
i want to install ubuntu 11.4 on a system alongside some other linux and windows. i installed the whole system on one partition ( / on /dev/sda12) before completing the installation "migration-assistant" nags that:
Migration assistant wants to mount a partition but /dev/sda10 can not be unmounted.
the "continue" option can not unmount that partition and come back to that menu. "go back" option results in breaking the installation. though it says that the installation is complete but the grub is nut installed and i cannot boot the installed ubuntu.
here is the results of df commant:
```
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
aufs                   1676496     65756   1610740   4% /
none                   1669608       764   1668844   1% /dev
/dev/sr0                701742    701742         0 100% /cdrom
/dev/loop0              673664    673664         0 100% /rofs
none                   1676496       200   1676296   1% /dev/shm
tmpfs                  1676496        36   1676460   1% /tmp
none                   1676496       112   1676384   1% /var/run
none                   1676496         4   1676492   1% /var/lock
/dev/sda12            43254272   2224756  38832320   6% /target
/dev/sda10            43254272   2224756  38832320   6% /target
/dev/sda11            43254272   2224756  38832320   6% /target
/dev/sda13            43254272   2224756  38832320   6% /target
/dev/sda9             43254272   2224756  38832320   6% /target

```
it should be mentioned that i can not mount any partitions in nautilus.
Any comment or help will be welcomed!

---

### Post by hadian on 2011-05-01
and this is the last line is /var/log/syslog:
May  1 09:17:18 ubuntu ubiquity: umount: cannot umount /dev/sda10 -- /dev/sda9 is mounted over it on the same point.

---

