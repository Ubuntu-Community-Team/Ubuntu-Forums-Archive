---
title: "Disk Full during upgrade to 10.10"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by HankB on 2010-11-05
My netbook experienced a disk full condition (as in zero free blocks reported by 'df') while configuring packages during the upgrade process. The upgrade tool aborted after it tried running 'dpkg --configure -a'. I ran that manually and surprisingly, it seemed to complete, but it still left me with zero blocks free. I purged the oldest kernel and that completed OK and *still* left zero free blocks. (I'm sure having things like /tmp and /var/log in RAM via tmpfs helped.)

Following reboot I seem to be running 10.10 and found 18 MB free on the root device. Following 'apt-get clean' I have 663 MB free. 'apt-get autoremove' provides no relief.

This leaves me with 82% free space on a 4GB root partition. I think I had about 65% free prior to the upgrade. I'm wondering if some step that removes unused cruft got skipped and if I can run that now manually. I'd prefer to do that rather than have to do a complete reinstall.

Thanks!

-hank

---

### Post by dino99 on 2010-11-05
maybe its time to clean the room dipper: install bleachbit from synaptic and run it as admin (carefully set your prefs)

and a fsck on next reboot will help:

sudo shutdown now -R

---

### Post by silbak04 on 2010-11-05
please post your output of:

```

$ df -h

```

---

### Post by HankB on 2010-11-05
> **dino99 said:**
> maybe its time to clean the room dipper: install bleachbit from synaptic and run it as admin (carefully set your prefs)

and a fsck on next reboot will help:

sudo shutdown now -R

bleachbit doesn't report much savings from my system partition.

How do you force fsck on the next boot? (Aside from an unclean shutdown.)

> **silbak04 said:**
> please post your output of:

```

$ df -h

```

```
root@bonsai:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             3.7G  2.9G  702M  81% /
none                  997M   32M  965M   4% /dev
none                 1002M  760K 1002M   1% /dev/shm
tmpfs                1002M   32K 1002M   1% /tmp
tmpfs                1002M  112K 1002M   1% /var/run
tmpfs                1002M     0 1002M   0% /var/lock
tmpfs                1002M  668K 1002M   1% /var/log
none                  3.7G  2.9G  702M  81% /var/lib/ureadahead/debugfs
/dev/sdb1              15G  5.9G  8.3G  42% /home

```

thanks,
hank

---

### Post by silbak04 on 2010-11-05
According to your output of "df-h" it's saying you only have 3.7G partitioned on the filesystem (/dev/sda1, in this case) and then you have your /home folder mounted on /dev/sdb1. I'm not sure what to do in this case other than just go ahead and reinstall...but when you reinstall make sure you give Ubuntu more space...so give your filesystem (Ubuntu) like 15G mounted on "/".

Or if there is a better solution, I'm sure someone will respond to this thread.

---

### Post by HankB on 2010-11-05
> **silbak04 said:**
> According to your output of "df-h" it's saying you only have 3.7G partitioned on the filesystem (/dev/sda1, in this case) and then you have your /home folder mounted on /dev/sdb1. I'm not sure what to do in this case other than just go ahead and reinstall...but when you reinstall make sure you give Ubuntu more space...so give your filesystem (Ubuntu) like 15G mounted on "/".

Or if there is a better solution, I'm sure someone will respond to this thread.
I'm sort of constrained by the Eee PC 901 H/W. It actually has two SSDs. The first is 4GB and the second is 16GB. It's convenient to use the the 4GB SSD for the root partition and the other for /home, but I could share some of the larger with the smaller through the creative use of links. I've gone down that path before and it can be awkward. I could use LVM, but then I give up the ability to install to the system partition w/out tampering with /home.

thanks,
hank

---

### Post by oldfred on 2010-11-06
You should be able to make 4GB work, but you will have to be agressive on housecleaning and perhaps remove a large app or two and substitute smaller versions. OpenOffice or firefox

HouseKeeping:
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
sudo apt-get autoremove  #removes depenancies no longer needed
# removes .deb
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
Sometimes this does more?
sudo apt-get dist-upgrade  #updates dependancies

 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

Go to Synaptic Package Manager and search for linux-image.
More info in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

# remove log files if no issues
cd /var/log
sudo rm -f messages.*
sudo rm -v /var/log/*.gz

#check for large files:
sudo du -h --max-depth=1 / | grep '[0-9]G\>'   # folders larger than 1GB
sudo find / -name '*' -size +1G    # files larger than 1GB

Large Packages
dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -n

gksudo nautilus /root/.local/share/Trash/files  # Be sure to enable viewing of hidden files.

---

### Post by HankB on 2010-11-06
Hi oldfred,
Thanks for the tips. Most of them I already covered and the few remaining seemed moot, but it is good to know that I haven't overlooked much.

I've already moved /tmp, /var/{log|lock|run} to tmpfs so deleting logs won't help. I did remove most of evolution since I don't use it anyway. 

I have 33 video drivers:
```
root@bonsai:~# dpkg -l|grep xserver-xorg-video|wc -l
33
```
I wonder if I can remove the ones that don't match my H/W.

I'm presently at 75% which probably means I'll need to do something different during the next upgrade.

-hank

---

