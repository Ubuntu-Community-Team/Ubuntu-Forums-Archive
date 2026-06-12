---
title: "Splitting existing drive into 2 partitions"
date: 2019-10-10
forum: Installation &amp; Upgrades
---

### Post by robt800 on 2019-10-10
I've recently installed ubuntu onto a 120GB SSD.

Upon a little reading it has been advised to me to store larger files/ folders not in the home directory, but on a separate partition.

Hence I'd like to create a 60GB split (or potentially more say 30GB OS, 90GB data).

I've read this needs to be done using a live CD & gparted.

I booted up, unmounted the drive in question simply using the files application.  Went into gparted and still have the option to 'deactivate'.  Did that as well.  However Gparted will not let me shrink the existing volume.  The minimum size is set 28mb less than the current size - hence I can only shrink by 28mb...

Any insights much appreciated,

Thanks
Rob

---

### Post by Dennis N on 2019-10-10
You may have an LVM setup which has to be handled differently. Post output from terminal of the command **df -h** to confirm this.

---

### Post by robt800 on 2019-10-10
I think you are right - saw LVM in Gparted.  the output from df -h is:
```
```
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        374M  1.6M  373M   1% /run
/dev/mapper/ubuntu--vg-root  109G  8.4G   95G   9% /
tmpfs                        1.9G     0  1.9G   0% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop0                    15M   15M     0 100% /snap/gnome-logs/45
/dev/loop1                   1.0M  1.0M     0 100% /snap/gnome-logs/81
/dev/loop2                    15M   15M     0 100% /snap/gnome-characters/317
/dev/loop3                    55M   55M     0 100% /snap/core18/1192
/dev/loop4                   4.3M  4.3M     0 100% /snap/gnome-calculator/501
/dev/loop5                   3.8M  3.8M     0 100% /snap/gnome-system-monitor/100
/dev/loop6                    91M   91M     0 100% /snap/core/6350
/dev/loop9                    43M   43M     0 100% /snap/gtk-common-themes/1313
/dev/loop7                   150M  150M     0 100% /snap/gnome-3-28-1804/71
/dev/loop10                   13M   13M     0 100% /snap/gnome-characters/139
/dev/loop8                   141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop11                  2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop12                   35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop13                   90M   90M     0 100% /snap/core/7713
/dev/loop14                  3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop15                  141M  141M     0 100% /snap/gnome-3-26-1604/92
tmpfs                        374M   24K  374M   1% /run/user/1000
```
```

Thank

---

### Post by TheFu on 2019-10-10
Yep, you are using LVM. These would help:
```
lsblk -o name,size,type,fstype,mountpoint
sudo pvs
sudo vgs
sudo lvs

```
The good news is that dealing with LVM is easier than partitioning, just different.  But you should think about storage a little differently.  Think about what you need to allocate today, not what you might need in a year.  With LVM+ext4, growing an LV is trivial, while the system is running and being used. Shrinking is a little harder and does need to be performed from alternative boot. Also, LVM doesn't have any GUI management, so everything is handled using shell commands.

You'll need to use **lvreduce** (with some options) but first you'll need to activate the VG from that alternative boot media, **sudo vgchange -ay** is how that gets done.  In the Live environment, it might be necessary to install the lvm tools. **sudo apt install lvm2**

That should be enough hints to get you through this.  I'd do smaller than 30G for the OS, BTW.  Shrinking is harder than growing.

---

### Post by robt800 on 2019-10-10
Managed to sort with your hints!

Thanks!

---

### Post by TheFu on 2019-10-10
This is the way these forums are supposed to work!
Any chance you could post the commands used, in order, to help out others?

---

