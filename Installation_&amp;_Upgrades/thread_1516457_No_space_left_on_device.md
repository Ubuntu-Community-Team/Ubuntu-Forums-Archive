---
title: "No space left on device"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by pat_mills on 2010-06-23
I installed 10.04 server 32 bit on a HP with two 160GB drives. During install from live CD created raid1 for root and swap. Installed system all seemed fine. Later decided I wanted to install ubuntu-desktop. Since that point everything I try to do tells me "no space left on device" 

df -h:
patm@bfmail:~$ df -ah
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              146G  2.2G  136G   2% /
proc                     0     0     0   -  /proc
none                     0     0     0   -  /sys
none                     0     0     0   -  /sys/fs/fuse/connections
none                     0     0     0   -  /sys/kernel/debug
none                     0     0     0   -  /sys/kernel/security
none                  2.0G  200K  2.0G   1% /dev
none                     0     0     0   -  /dev/pts
none                  2.0G     0  2.0G   0% /dev/shm
none                  2.0G   92K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
none                  146G  2.2G  136G   2% /var/lib/ureadahead/debugfs
binfmt_misc              0     0     0   -  /proc/sys/fs/binfmt_misc
patm@bfmail:~$ 


Clearly there is tons of space. While running apt-get update:

.
.
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/binary-i386/Packages.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_binary-i386_Packages - open (28: No space left on device) [IP: 91.189.88.46 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/lucid-updates/multiverse/source/Sources.gz)  Could not open file /var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_lucid-updates_multiverse_source_Sources - open (28: No space left on device) [IP: 91.189.92.166 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@bfmail:~# 

if i run dpkg --configure -a 
dpkg: failed to open `/var/lib/dpkg/status' for writing status information: No space left on device

I've done the apt-get clean, autoclean, autoremove all to no avail.

I read somewhere about a problem with raid on Lucid?

I give...............

---

