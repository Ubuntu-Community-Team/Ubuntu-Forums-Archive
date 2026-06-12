---
title: "Fixing screwed up RAID setup"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by CptPicard on 2006-08-29
Ok, so it was my first time setting up software RAID on Linux and I screwed up... :rolleyes: While using the installer, I didn't understand the meaning of a "spare" device in an (RAID-1) array. So what I've got now is

```

root@manticore:/home/eneva# cat /proc/mdstat
Personalities : [raid1]
md0 : active raid1 sda5[0] sdb6[1](S)
      103201408 blocks [1/1] [U]

```

So essentially it seems, if I understand correctly, that there's one non-raided partition with a spare device sitting there doing nothing, while I was obviously going for a regular mirrored setup with sda5 and sdb6 as md0.

Now, the mdadm man page is a "bit" obscure with all the modes one can run the tool on, and I wouldn't want to experiment and lose data while trying to fix this... what should I do? I'd rather not just empty the raid and start anew...

---

### Post by paca on 2006-08-31
morning...

**mdadm --create --level=1 --raid-devices=2 /dev/md0 /dev/loop1 /dev/loop2**
mdadm: array /dev/md0 started.

**mdadm --add /dev/md0 /dev/loop3**
mdadm: hot added /dev/loop3

**cat /proc/mdstat**
Personalities : [raid1]
md0 : active raid1 loop3[2](S) loop2[1] loop1[0]
      51136 blocks [2/2] [UU]

unused devices: <none>

*Now i got the same setup as u, but with one more disk in the array. Add the Spare array to the array with: (u should use --raid-disks=2 and if u use newer mdadm than what comes with dapper --raid-devices=*

**mdadm --grow /dev/md0 --raid-disks=3**
**cat /proc/mdstat**
Personalities : [raid1
md0 : active raid1 loop3[3] loop2[1] loop1[0]
      51136 blocks [3/2] [UU_]
      [==>..................]  recovery = 10.0% (5376/51136) finish=0.2min speed=2688K/sec

unused devices: <none>

Hope this helps u!
/Paca

---

### Post by CptPicard on 2006-08-31
Great, big thanks, sure helped me. Probably would never have figured it out on my own without destroying a few arrays in the process ;)

---

