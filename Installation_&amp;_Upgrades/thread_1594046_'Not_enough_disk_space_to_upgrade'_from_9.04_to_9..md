---
title: "'Not enough disk space to upgrade' from 9.04 to 9.10"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by petenz on 2010-10-11
Hi All

I need a bit of help - which is a surprise as I've found Ubuntu beyond my expectations on all the machines I've run it on.

I'm trying to upgrade my old desktop from 9.04 to 9.10 (and then 10.04 - same as my laptop), and am running into this message at the start of the upgrade process:

"Not enough free disk space

The upgrade is now aborted. The upgrade needs a total of 3109M free space on disk '/'. Please free at least an additional 1088M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

I've done a bit of searching and have followed the leads I've found but am still stuck. I've emptied trash, cleared out old kernels etc but it hasn't got me there.

Running df -h gives this:
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.8G  5.5G  2.0G  75% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  336K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  156K  501M   1% /dev
tmpfs                 501M  208K  501M   1% /dev/shm
lrm                   501M  2.2M  499M   1% /lib/modules/2.6.28-19-generic/volatile
/dev/sda6             136G   75G   54G  59% /home

Can anyone wiser than me see what's up? I believe /dev/sda1 is the boot partion that the install is failing on???

Thanks for any help you can give.

---

### Post by stee1rat on 2010-10-12
try something from here: [http://ubuntuforums.org/showthread.php?p=800462#post800462](http://ubuntuforums.org/showthread.php?p=800462#post800462)

---

### Post by mikechant on 2010-10-12
5.5Gb is quite a lot for a root partition. Unless you've installed huge amounts of extra software there should be 1-2G space you can recover.
Expanding the directory tree in the disc use analyser will let you drill down through the root filesystem to find out where your space has gone:
[http://www.debianadmin.com/check-disk-space-usage-on-ubuntu.html](http://www.debianadmin.com/check-disk-space-usage-on-ubuntu.html)

---

