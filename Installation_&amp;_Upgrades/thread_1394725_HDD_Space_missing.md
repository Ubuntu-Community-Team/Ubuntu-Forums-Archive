---
title: "HDD Space missing"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by DRBRG on 2010-01-31
Hi,
I have finished installing Ubuntu 9.10 and now I can only see 40GB of my 160 GB HDD.
When I run df -h it shows :

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu--Svr2-root
                       36G   27G  6.6G  81% /
udev                  501M  276K  501M   1% /dev
none                  501M  100K  501M   1% /dev/shm
none                  501M  264K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
/dev/sda5             228M   28M  189M  13% /boot

and Gparted is showing what is in the attached PNG.

It seems that /dev/sda1/ has 148 GB but only 40 GB are available for the filesystem.
I only have 1 HDD ( /dev/sda/ ).

Please help :)

Tks

---

### Post by Herman on 2010-01-31
You can have your file system resized to fill your partition by booting a Ubuntu Live CD and without mounting the file system, run 'sudo resize2fs -p /dev/sda1', 
```
sudo resize2fs -p /dev/sda1 
```If you don't like the running terminal commands the GUI way is to open GParted, right click on the partition and click 'check'. Then click the apply icon and when the confirmation box opens hit the 'Apply' button and wait a few minutes. GParted will run a file system check in your partition for you and then resize2fs.

Either of those two choices should solve your problem providing you're using an ext series file system, which is currently the most popular and default for all standard Ubuntu installations.

---

### Post by Herman on 2010-01-31
> I have finished installing Ubuntu 9.10 and now I can only see 40GB of my 160 GB HDD.
When I run df -h it shows :

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu--Svr2-root
                       36G   27G  6.6G  81% /
udev                  501M  276K  501M   1% /dev
none                  501M  100K  501M   1% /dev/shm
none                  501M  264K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
none                  501M     0  501M   0% /lib/init/rw
/dev/sda5             228M   28M  189M  13% /boot
Is this a regular install or did you install in LVM?

---

### Post by DRBRG on 2010-01-31
Good question..
It was on LVM. I just installed the Logical Volume Management tool ( system-config-lvm on Synaptic ) and found the "missing" 120 GB as unused space. ( sorry but I am beginner using this file systems :(  )

Using LVM tool was really easy to create a new partition with the left space and mount it on /Data. ( Attached .png ).

Case closed.

Thanks for your time and support ! :D

---

