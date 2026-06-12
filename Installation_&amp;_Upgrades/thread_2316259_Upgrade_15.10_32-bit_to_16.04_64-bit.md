---
title: "Upgrade 15.10 32-bit to 16.04 64-bit"
date: 2016-03-06
forum: Installation &amp; Upgrades
---

### Post by OiPenguin on 2016-03-06
I bought a decent server a few months ago and installed Ubuntu desktop with server setup and use the machine as a headless server. Due to some issues with the 64-bit version of Ubuntu 15.10 (total system freeze during installation) I decided to use the 32-bit version. I would prefer to change to 64-bit when upgrading and understand that a clean install is preferable (rather than upgrade from 32-bit to 64-bit). 

I've got a raid10-setup (currently with one SSD and 2 x 3GB HD for raid, but will add to more at a later stage). This is the essential parts of my setup:
- /data - Homevideos, pictures etc in sub folders
- /home - home areas of family members

Can I do a regular advanced installation where / is reinstalled and formatted, but retain the current /data in the same way as I usually retain /home/ when doing a clean install on my laptop?

A sidenote: Assuming proper backup, is 16.4, although not final nor production ready, stable enough to upgrade to for this server during the coming weeks?

Yours, 

Lars

---

### Post by goofprog on 2016-03-06
Honestly to me, I believe that it is not a good upgrade from 32 to 64 bit Ubuntu.  If the problem is just retaining data on a fresh installation then I would just back up the data to an external drive and copy it back over to the new 64 bit OS.  I mean it seems the easiest way to do it.

---

### Post by grahammechanical on 2016-03-06
Are /data & /home on separate partitions? If so, then re-installing into the / partition and formatting the partition will not touch /home (especially if you do not tick to format) or /data.

Regards.

---

### Post by OiPenguin on 2016-03-07
> **grahammechanical said:**
> Are /data & /home on separate partitions? If so, then re-installing into the / partition and formatting the partition will not touch /home (especially if you do not tick to format) or /data.


Yeah. Both /data and /home are on seperate partitions. I've posted my entire setup below.

```

user@server:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            3,9G     0  3,9G   0% /dev
tmpfs           799M   11M  789M   2% /run
/dev/sdc5        23G   12G   11G  52% /
tmpfs           3,9G   84K  3,9G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           3,9G     0  3,9G   0% /sys/fs/cgroup
/dev/sdc6        81G   47G   30G  62% /home
/dev/sdc1       922M  137M  722M  16% /boot
/dev/md0        2,7T  946G  1,7T  37% /data
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           799M   56K  799M   1% /run/user/1000
tmpfs           799M     0  799M   0% /run/user/1004

```

---

### Post by mörgæs on 2016-03-07
> **OiPenguin said:**
> understand that a clean install is preferable (rather than upgrade from 32-bit to 64-bit). 


Not only preferable, it's the only way to go. One can't upgrade from 32 to a 64 bit version.

Would be great if you could test 16.04 and report the bugs if you find any.

---

### Post by oldfred on 2016-03-08
If you have installed lots of applications, you want to export that list. 
 from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5) 


And your /etc/fstab, so you do not have to manually recreate all your mounts. You may have other entries in /etc and if a server various installed apps inside / (root) that you want to save settings or databases.
 
So good backups are required to make it easy to restore to a good working install.

---

### Post by OiPenguin on 2016-03-11
Thanks for all replies. I've upgraded (clean install, /home kept) my laptop, but will wait until the final version before upgrading my server. Upgrade were fairly smooth, but my language keyboard was not available before I upgraded all packages and rebooted. 

The tip about how to backup all packages were great. I've not used it for the laptop since part of my problem was that I had installed too much clutter, but I may use it when upgrading my server.

---

