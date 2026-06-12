---
title: "Best way to backup the root partition before performing an upgrade"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by kevinp on 2007-10-13
I am presently running a Kubunty Edgy 64 server as my home network file and application server.  It has a ton of stuff installed and configured on it, so I have no desire to repeat all of the configuration when I upgrade to Gutsy.

So I will probably perform the upgrade procedure.  Question:  What is the best way to backup the / partition so I can roll back to it in case of problems?  I presently have a tar backup that runs periodically, but I don't fully understand how it works and it gives me strange messages especially in /var/run and /sys/module.  So I am not entirely comfortable that the tar backup is getting everything.

Can I use dd to copy the partition on which / is mounted (by booting from the install CD)?  Then I could use dd to roll back in case of insurmountable problems during the upgrade.  How does this sound?  I have plenty of spare disk space, so that is not a problem.  All the large files and /home are mounted on different partitions which I can leave alone.

Thanks in advance!

---

### Post by logos34 on 2007-10-13
> **kevinp said:**
> Can I use dd to copy the partition on which / is mounted (by booting from the install CD)?  Then I could use dd to roll back in case of insurmountable problems during the upgrade.  How does this sound?  I have plenty of spare disk space, so that is not a problem.

yep, dd.  Or use Partimage.

---

### Post by kevinp on 2007-10-13
A further question:  My root partition was set up on a software RAID array using the Ubuntu Edgy installer.  It is a RAID1 (mirrored) array comprising of the first partition on three disks:

cat /proc/mdstat :

```
md0 : active raid1 sda1[0] sdb1[1](S) sdc1[2](S)
      9767424 blocks [1/1] [U]
```


sudo mdadm --detail md0 :

...

```
    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1

       1       8       17        -      spare   /dev/sdb1
       2       8       33        -      spare   /dev/sdc1
```

So, in this case, it would seem that:
* Booting from the CDROM and doing a dd on /dev/sda1 should create the backup
* In case I need to restore, I should boot from the CDROM, and restore to /dev/sda1 and sdb1 and sdc1

Am I correct?

---

