---
title: "/ 100% Used! How to fix?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by lpanebr on 2009-11-23
I have a Hardy 8.04.2 installed with partitions set manually and now it looks like I am having some problem because I get a permanent overflow /tmp partition mounted even after reboot.

I guess that when I set the partitions I did not include a /tmp partition and also did not leave enough space on the / partition...

How do I fix this?
 
- sda is a 250GB drive where ubuntu was installed (it has enough spare space on /cubo partition)
- sdb is a 500GB drive installed later on for backup purposes only

Below is the output of df -h

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              28G   28G     0 100% /
varrun                950M  100K  950M   1% /var/run
varlock               950M     0  950M   0% /var/lock
udev                  950M   48K  950M   1% /dev
devshm                950M     0  950M   0% /dev/shm
lrm                   950M   39M  912M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda6             194G  1.3G  183G   1% /cubo
/dev/sda5             4.7G  154M  4.3G   4% /home
/dev/sdb1             463G  220G  220G  50% /media/backup
overflow              1.0M  4.0K 1020K   1% /tmp

```

Thanks in advance,

Luciano

---

### Post by ptn107 on 2009-11-23
Pop in the live CD and boot to the live desktop.  Open up System -> Administration -> Gparted and drag to resize your partitions and click apply.  Resizing can take a matter of hours.

---

### Post by audiomick on 2009-11-23
Backup first!!!
I had a problem recently where I had to resize / because it was full.
/home was a separate partiton, which I shrunk, and gave the freed up space to /. I subsequently did a fresh install to 9.10 ( the machine had 8.04 on it) , using the resized existing /home partition. Now the "places"  menu does weird stuff. I don't know what the problem is. I posted it, but got no reply.

---

### Post by lpanebr on 2009-11-23
Thanks for the fast reply! 

Should I also create a /tmp partition??

Luciano

---

### Post by Simian Man on 2009-11-23
28 gigs is rather a lot for /.  I generally use around 5-10 gigs at the most.  Maybe you can just try uninstalling some applications that you don't use.

---

### Post by oldfred on 2009-11-24
You may want to check where you space is going:

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB
gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

and you may want to do some housekeeping:

HouseKeeping:
sudo apt-get update 
sudo apt-get upgrade 
sudo apt-get autoremove
# removes .deb
sudo apt-get autoclean

I think Autoclean just cleans up files you don't need, while autoremove deletes unneded files..
Autoclean cleans up the downloaded archives (.gz or .tar) files used to install things. Autoremove cleans libraries that are no longer needed.
you can run any "apt-get" command predeccesed by the "-s" (simulate) switch

---

