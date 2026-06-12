---
title: "Edgy to Feisty"
date: 2007-11-06
forum: Installation &amp; Upgrades
---

### Post by coolboarderguy on 2007-11-06
Hi All,

I am getting this error on my laptop,

The upgrade aborts now. Please free at least 222M of disk space on /usr. Empty your Deleted Items folder and remove temporary packages of former installations using 'sudo apt-get clean'.

Below is the output of df

df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/sda5             5.8G  4.1G  1.4G  75% /
varrun                506M  156K  505M   1% /var/run
varlock               506M  4.0K  505M   1% /var/lock
procbususb             10M  132K  9.9M   2% /proc/bus/usb
udev                   10M  132K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   18M  488M   4% /lib/modules/2.6.17-12-386/volatile
/dev/sda7              20G   16G  3.1G  84% /home

I'm sure I have enough space there? I ran apt-get clean to no avail.

---

