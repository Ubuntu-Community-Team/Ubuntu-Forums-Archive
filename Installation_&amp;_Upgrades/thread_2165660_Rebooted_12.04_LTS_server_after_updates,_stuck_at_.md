---
title: "Rebooted 12.04 LTS server after updates, stuck at (initramfs) prompt now"
date: 2013-08-05
forum: Installation &amp; Upgrades
---

### Post by talz13 on 2013-08-05
I just rebooted my server this morning and noticed that the server never came back online.  I just got home, and turned the old monitor on, and it was sitting at the "(initramfs)" prompt.  I just ran dmesg, and at the end it shows (paraphrased):

```
md/raid:md0: device sdc1 operational as raid disk 0
md/raid:md0: device sdd1 operational as raid disk 2
md/raid:md0: device sdb1 operational as raid disk 1
md/raid:md0: allocated 4280kB
md/raid:md0: raid level 5 active with 3 out of 4 devices, algorithm 2
RAID conf printout:
 --- level: 5 rd:4 wd:3
 disk 0, o:1, dev:sdc1
 disk 1, o:1, dev:sdb1
 disk 2, o:1, dev:sdd1
md0: detected capacity change from 0 to 3000606523392
 md0: unknown partition table
md: linear personality registered for level -1
md: multipath personality registered for level -4
md: raid0 personality registered for level 0
md: raid 1 personality registered for level 1
md: raid10 personality registered for level 10
```

Did one of my raid 5 drives die? What else could be causing issues? I boot from a separate 640gb sda drive, but /home is mounted on the md0 drive.


edit: Scrolling up the dmesg output a bit shows:
```
md: bind<sde1>
md: bind<sdb1>
md: bind<sdd1>
md: bind<sdc1>
...
md: kicking non-fresh sde1 from array!
md: unbind<sde1>
```

---

### Post by talz13 on 2013-08-06
Solved my issue... I had to re-add the "sde1" disk back to the raid 5 array, as it was marked as "non-fresh".  It re-built the sde1 disk in about 3 hours, and then the system booted up fine afterwards.

I ran this command to re-add the sde1 disk back to the array:```
/sbin/mdadm /dev/md0 --add /dev/sda5
```

---

