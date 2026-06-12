---
title: "running out of disk space my / is full"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by contactmayankjain on 2008-08-14
Hi,

MY / is full how can I free it what are the extra things which are present in the default installation that is of no use and can help me to free my / space. Is there any way to increase my space. 
 df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda10             3.0G   2.8G    68M  98% /
varrun                 1.1G   119k   1.1G   1% /var/run
varlock                1.1G      0   1.1G   0% /var/lock
udev                   1.1G    87k   1.1G   1% /dev
devshm                 1.1G    41k   1.1G   1% /dev/shm
lrm                    1.1G    47M   1.1G   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda9              9.0G   2.3G   6.3G  27% /home
/dev/sda8              996M    19M   928M   2% /tmp
gvfs-fuse-daemon       3.0G   2.8G    68M  98% /home/mayank/.gvfs
/dev/sda6               42G    19G    23G  46% /media/disk-3


Thanks
Mayank Jain

---

### Post by iaculallad on 2008-08-14
You could try:

```
sudo apt-get clean
sudo apt-get autoclean
```

and try deleting the .bak files in your /boot directory.

```
sudo rm /boot/*.bak
```

---

### Post by contactmayankjain on 2008-08-14
it helped but not much I have already tried this one. Thanks for your prompt reply :)

---

### Post by contactmayankjain on 2008-08-14
I am running out of space and now my / is 100% full and I am getting errors no disk space left ... I need some urgent help. :popcorn:

---

