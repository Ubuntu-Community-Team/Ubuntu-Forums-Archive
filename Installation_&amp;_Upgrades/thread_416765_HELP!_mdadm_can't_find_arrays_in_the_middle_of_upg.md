---
title: "HELP! mdadm can't find arrays in the middle of upgrade"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by kalahari875 on 2007-04-21
Can anyone help with mdadm in Feisty? I am in the middle of an upgrade via apt-get (update tool wouldn't work) and it is prompting for the array needed to start the root filesystem. I have three arrays, md0 (swap), md1 (/boot), and md2 (/). But it won't accept md2 as an answer.
 
The package configuration screen in the console says:
[INDENT]
Configuring mdadm
An error occurred: array not listed in mdadm.conf file:
/dev/.static/dev/md2

Please enter a space-separated list of devices, 'all' or 'none'. You may omit the leading '/dev/' and just enter e.g. "md0 md1", or "md/1 md/d0".

MD arrays needed for the root filesystem:
[/INDENT]

My mdadm.conf is:

[INDENT]DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=766f39fb:bac8c930:a6a7e095:7b8ff212
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=32753e09:9a3140a7:e2c9fd32:8747fb66
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=19905e9e:2d1d92a6:bb1c2b0e:d0658573
DEVICE partitions
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=766f39fb:bac8c930:a6a7e095:7b8ff212
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=32753e09:9a3140a7:e2c9fd32:8747fb66
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=19905e9e:2d1d92a6:bb1c2b0e:d0658573
[/INDENT]

 It will accept /dev/.static/dev/md2 but then warns this array isn't listed in mdadm.conf (which has /dev/md2). I have tried entering "md0 md1 md2" and "/dev/md0 /dev/md1 /dev/md2" but it always comes back with the message above. It won't take "all" either. PLEASE HELP!!!

---

### Post by McDorian on 2007-06-17
Sorry I can't help, but I have this problem too. I would like to get it fixed, but have no idea what to do. Funnily enough, KDE and XFCE seem to be functioning fine, but it blocks Gnome.

---

### Post by Cellojazz on 2007-06-18
My mdadm.conf file looks like this

```
ARRAY /dev/md0 level=raid5 num-devices=3 UUID={big-uuid}
     devices=/dev/sdb1,/dev/sdc1,/dev/sdd1
```

so I'm not sure, but either you copy and pasted your mdadm.conf twice, or something looks wrong there. 

I'm still getting really solid on Linux, but if you know the partitions that make up the RAID, you could try adding them below the ARRAY listing like mine above (devices=/dev/hdaX,/dev/hdbX.... etc)

If this advice is wrong, I'd be glad to know, because that would probably help fix my problem.  Otherwise, if I were you, I'd make a backup copy of your existing mdadm.conf, and try to define each array with the specific partitions above, and see if that helps.

Hope this works out for you.

---

### Post by McDorian on 2007-06-19
Well, I had his mdadm problem without ever having set up RAID, or even knowing what it is. Since I have my ubuntu on a single partition, I guessed I didn't need mdadm at all, and followed some other advice on the forum to remove it with 

sudo apt-get remove mdadm

After that, everything was fine. 

As for being in the middle of an upgrade, it should be possible to boot off a live CD, then mount your hard disk partition, remove mdadm, and try a reboot.

However, since I am not a computer person, you should probably look for some better advice before trying out this solution.

---

