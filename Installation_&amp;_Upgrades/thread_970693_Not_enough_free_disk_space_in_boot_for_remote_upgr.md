---
title: "Not enough free disk space in /boot for remote upgrade"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by changewand on 2008-11-04
I am currently trying to upgrade to the latest release of Ubuntu remotely and have hit a snag. I received the following message when running the "do-release-upgrade" command:

Calculating the changes

Not enough free disk space 

The upgrade aborts now. The upgrade needs a total of 37.7M free space 
on disk '/boot'. Please free at least an additional 10.2M of disk 
space on '/boot'. Empty your trash and remove temporary packages of 
former installations using 'sudo apt-get clean'. 


Restoring original system state

here's the output from df -a:

ilesystem           1K-blocks      Used Available Use% Mounted on
/dev/md2             151827428  44263644  99851384  31% /
proc                         0         0         0   -  /proc
/sys                         0         0         0   -  /sys
varrun                 1037712       140   1037572   1% /var/run
varlock                1037712         4   1037708   1% /var/lock
udev                   1037712        60   1037652   1% /dev
devshm                 1037712         0   1037712   0% /dev/shm
devpts                       0         0         0   -  /dev/pts
lrm                    1037712     39780    997932   4% /lib/modules/2.6.24-21-generic/volatile
/dev/md0                 45037     15703     26931  37% /boot
securityfs                   0         0         0   -  /sys/kernel/security
binfmt_misc                  0         0         0   -  /proc/sys/fs/binfmt_misc

I have tried running apt-get clean and have no trash to empty. The problem for me is that this server is located at a colo several hundred miles away, so I cannot boot from CD or resize the boot partition. Any suggestions?

---

### Post by cdtech on 2008-11-04
Sounds like you may have excessive kernel images stored within your /boot partition. You could delete unused kernel images or resize your /boot partition using "gparted" before the upgrade.

I myself use around 400M so I can play around with other kernels. Each kernel uses about 45M.

Using the command line:
```
df -h
```
will give you the human readable output.

Hope this helps ya.......

---

### Post by changewand on 2008-11-04
Well, I think I've removed all past kernels and such:

/boot# ls -l
total 11418
-rw-r--r-- 1 root root  422781 2008-08-25 14:00 abi-2.6.24-21-generic
-rw-r--r-- 1 root root   80073 2008-08-25 14:00 config-2.6.24-21-generic
drwxr-xr-x 2 root root    1024 2008-10-20 15:35 grub
-rw-r--r-- 1 root root 8190768 2008-10-20 15:35 initrd.img-2.6.24-21-generic
drwxr-xr-x 2 root root   12288 2006-02-17 04:42 lost+found
-rw-r--r-- 1 root root  103204 2007-09-28 03:06 memtest86+.bin
-rw-r--r-- 1 root root  905365 2008-08-25 14:00 System.map-2.6.24-21-generic
-rw-r--r-- 1 root root 1920376 2008-08-25 14:00 vmlinuz-2.6.24-21-generic

and for the human touch:

/boot# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md2              145G   43G   96G  31% /
varrun               1014M  140K 1014M   1% /var/run
varlock              1014M  4.0K 1014M   1% /var/lock
udev                 1014M   60K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   39M  975M   4% /lib/modules/2.6.24-21-generic/volatile
/dev/md0               44M   16M   27M  37% /boot

can I try and resize the partition remotely? As I said in the OP, I have no physical access to the machine itself right now.

---

### Post by cdtech on 2008-11-04
I see you only have 44M /boot partition which is not enough for an additional kernel upgrade. You will not be able to remotely partition the drive for it has to be unmounted during the partitioning.

Once you re-size the partition you'll be good to go on the upgrade.

---

### Post by changewand on 2008-11-04
so it's really an impossible situation, as I cannot upgrade w/o repartitioning and I can't repartition w/o flying 400 miles and begging access out of my colo provider?

I've been able to do these upgrades for a very long time remotely...is it just that this procedure's requirements have just grown such that I can no longer do so?

Also, is it possible to somehow replace the /boot partition with a symlinked /boot on the main partition?

---

### Post by cdtech on 2008-11-05
> **changewand said:**
> Also, is it possible to somehow replace the /boot partition with a symlinked /boot on the main partition?

Well, it is absolutely possible. You would only need to rename the original /boot partition to maybe /bootbak and create a new directory /boot within, maybe the /dev/md2  which shows 145G before the upgrade. As long as your /etc/fstab file points to the correct directory you should be ok. Copy everything from the old /boot directory to the new.

Doing this remotely, you would need to be absolutely sure that your /etc/fstab and the /boot/grub/menu.lst files where correct before the reboot.

---

