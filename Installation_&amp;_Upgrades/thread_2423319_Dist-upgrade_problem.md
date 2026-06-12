---
title: "Dist-upgrade problem"
date: 2019-07-20
forum: Installation &amp; Upgrades
---

### Post by rob141 on 2019-07-20
Hello, since i have done a dist-upgrade, i cannot open my ubuntu and i have added the picture of the error i am getting.  Can anyone help me please ?

---

### Post by CatKiller on 2019-07-20
You need to do what it says: run a fsck on /dev/sda1.

Doing it from an install disc is easier than trying to do it through BusyBox.

---

### Post by Bashing-om on 2019-07-20
rob141; Hello -
As per the system's advise:

Run:
```

sudo fdisk -lu

```
to know the target partition is sda1 for sure !

run the file system checks:.
#From liveUSB/DVD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see: man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```
See: fsck [http://www.thegeekstuff.com/2012/08/fsck-command-examples/](http://www.thegeekstuff.com/2012/08/fsck-command-examples/)

-my bit to try and help-

---

### Post by rob141 on 2019-07-20
Thank you very much, i have done it with a live cd and it worked.    Thank sooooo much for the fast replies,  yall are awesome  ;)

---

