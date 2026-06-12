---
title: "Is my swap active?"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by mibadt on 2008-11-06
Hi,
I'm on Kubuntu Hardy+KDE 4.1.
While dmesg and top report an active swap, it does NOT appear in mtab. Is my swap active, and if so, why isn't it listed in mtab?

Thanks

Michael Badt

---------- copy of related commands (as root)---
root@Miki-Desk:/etc# dmesg | grep swap
[   51.546207] Adding 4096564k swap on /dev/sda2.  Priority:-1 extents:1 across:4096564k

root@Miki-Desk:/etc# cat  fstab | grep swap
UUID=c12d4efe-d82e-483c-8a98-3ea72da7849d none            swap    sw              0       0

root@Miki-Desk:/etc# cat mtab | grep swap
root@Miki-Desk:/etc#

---

### Post by SilverWave on 2008-11-07
Hmm I was looking into this in response to this article:
[Warning: Ubuntu/Arch Linux Slowdown? Check Your Swap](http://the.linux-hardcore.com/node/11)


so UUID=1270564a-eaf9-4634-add7-4a3e3a52ebee is correct in both blkid and ftab ... but no swap in mtab?

/goes looking at old backups...

[EDIT]
[http://bbs.archlinux.org/viewtopic.php?pid=445615](http://bbs.archlinux.org/viewtopic.php?pid=445615)
> AurGlass:
I'm not sure why you would be looking in /etc/mtab (or /proc/mounts) for your swap partitions.  I've never seen them listed there.

As fukawi2 mentioned, `swapon -s` or `cat /proc/swaps` will tell you whether your swap partitions are active.

```
:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3959       3888         70          0       1292        499
-/+ buffers/cache:       2097       1861
Swap:         4094          3       4091

:~$ cat /proc/swaps
Filename				Type		Size	Used	Priority
/dev/sda8                               partition	4192924	3544	-1
:~$ 
```

---

### Post by mibadt on 2008-11-07
Thanks a lot!
Turns out my swap is functioning. :)

Michael Badt

---

