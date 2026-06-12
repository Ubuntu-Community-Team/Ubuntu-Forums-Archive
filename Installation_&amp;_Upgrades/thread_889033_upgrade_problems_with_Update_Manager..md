---
title: "upgrade problems with Update Manager."
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by kimme on 2008-08-13
This problem happened recently. When I try to run the Update Manager from the tools panel I get this requester....

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

And when I try to run the above mentioned "dpkg --configure -a" command from the terminal as an super user I get this message in the terminal...

root@ubuntu:/home/kimme# dpkg --configure -a
dpkg: klarte ikke skrive status-post om «dvdisaster» til «/var/lib/dpkg/status»: No space left on device
root@ubuntu:/home/kimme# 

The output is in Norwegian it's translated as "Could not write status-post about "dvdisaster" to «/var/lib/dpkg/status»: No space left on device.

How ca<n I fix this problem?

Thanks in advance.

---

### Post by Pumalite on 2008-08-13
Post:
df -h

---

### Post by kimme on 2008-08-14
kimme@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              20G   20G     0 100% /
varrun               1014M  224K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   64K 1014M   1% /dev
devshm               1014M   60K 1014M   1% /dev/shm
lrm                  1014M   20M  995M   2% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             207G   20G  178G  10% /home
overflow              1,0M   36K  988K   4% /tmp
gvfs-fuse-daemon       20G   20G     0 100% /home/kimme/.gvfs
/dev/sdb1             466G  166G  301G  36% /media/IcyBox
kimme@ubuntu:~$ 

I see now that my / device is full, but that I have lot's of space available on my /home device. Is it possible to resize the / device with the /home device?

---

### Post by Pumalite on 2008-08-14
Post a screenshot of Gparted

---

