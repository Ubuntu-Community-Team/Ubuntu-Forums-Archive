---
title: "Move partition ?"
date: 2008-10-13
forum: Installation &amp; Upgrades
---

### Post by mpierce on 2008-10-13
Here are my partitions. Am wondering if I can umount /usr/local and move it to root? If so, how?

mpierce@daisy:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda1              19G  433M   18G   3% /
varrun               1013M  276K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   76K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   39M  975M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda7             965M   37M  881M   4% /boot
/dev/sda9             430G   19G  390G   5% /home
/dev/sda5             3.8G   73M  3.6G   2% /tmp
/dev/sda8             3.8G  3.5G  182M  96% /usr
/dev/sda6             3.8G  734M  2.9G  20% /var

---

### Post by aysiu on 2008-10-13
Yes, you can do it, but you'd need a live CD to move the files over and change your /etc/fstab appropriately.

---

