---
title: "Update failed - run dpkg manually"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by William_in_Kanata on 2008-07-04
New install of ubuntu. Install went ok, and I then tried to update to latest releases of all packages which ran as expected until near the end. when something failed and the process crashed. Didn't catch the error messages. I then tried to restart synaptic, and received the following message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report. 

Running dpkg as requested produces the following messages:

Setting up initramfs-tools (0.85eubuntu39.1) ...
update-initramfs: deferring update (trigger activated)

Setting up linux-ubuntu-modules-2.6.24-19-generic (2.6.24-19.28)
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-19-generic (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-19-generic; however:
  Package linux-ubuntu-modules-2.6.24-19-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.19.21); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1


The problem as I see it is the gzip "no space on device" error. Question is: Which device?. /boot is on its own partition, of 37.9 GB, and System Monitor says there are 5.0 Mb free, with 3.1 Mb available. (Why are these numbers not the same?) Do I need to re-install with a larger boot partition? If so how big should I make it? If not boot, how do I figure out which device is the problem? I have plenty of disk space, but is allocated to other partitions.

TIA

---

### Post by Pumalite on 2008-07-04
Post>
df -h

---

### Post by William_in_Kanata on 2008-07-04
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.3G  416M  8.4G   5% /
varrun                887M  100K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M   68K  887M   1% /dev
devshm                887M   12K  887M   1% /dev/shm
lrm                   887M   38M  849M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              38M   33M  3.1M  92% /boot
/dev/sda4             102G  207M   97G   1% /home
/dev/sdb3              28G  173M   27G   1% /opt
/dev/sdb4              28G  176M   27G   1% /tmp
/dev/sdb1              28G  1.8G   25G   7% /usr
/dev/sdb2              28G  639M   26G   3% /var

---

### Post by William_in_Kanata on 2008-07-04
[FONT="Courier New"] df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             9.3G  416M  8.4G   5% /
varrun                887M  100K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M   68K  887M   1% /dev
devshm                887M   12K  887M   1% /dev/shm
lrm                   887M   38M  849M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda1              38M   33M  3.1M  92% /boot
/dev/sda4             102G  207M   97G   1% /home
/dev/sdb3              28G  173M   27G   1% /opt
/dev/sdb4              28G  176M   27G   1% /tmp
/dev/sdb1              28G  1.8G   25G   7% /usr
/dev/sdb2              28G  639M   26G   3% /var[/FONT]

---

### Post by Pumalite on 2008-07-04
/dev/sda1 38M 33M 3.1M 92% /boot
Remove some of the stuff from this folder.

---

