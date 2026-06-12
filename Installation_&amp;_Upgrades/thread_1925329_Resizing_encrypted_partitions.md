---
title: "Resizing encrypted partitions"
date: 2012-02-14
forum: Installation &amp; Upgrades
---

### Post by apamix on 2012-02-14
Hello everybody,

I have one little big problem. I Have a encrypted hdd but the root partition is to little :( 

```

[root@PCrevisie:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/PCrevisie-root
                      322M  292M   [COLOR=Red]14M[/COLOR]  [COLOR=Red]96%[/COLOR] /
tmpfs                1013M     0 1013M   0% /lib/init/rw
udev                 1008M  228K 1008M   1% /dev
tmpfs                1013M  4.0K 1013M   1% /dev/shm
/dev/sda1             228M   16M  201M   7% /boot
/dev/mapper/PCrevisie-home
                       58G   36G   20G  65% /home

```So my idea is now to cut 1GB from the /home partition and add it to the root partition but I will need some help. After I read some tutorials I think the prodcedure must go this way : 

1) BACK UP  before I start crying 

2) Boot the live cd and then : 

```

sudo apt-get update && sudo apt-get install lvm2 cryptsetup

# Loading it to kernel 
sudo modprobe dm-crypt

# Open the encrypted partition 

sudo cryptsetup luksOpen /dev/sda2 crypt1

# And we must recognize him.
sudo vgscan --mknodes
sudo vgchange -ay


```Here was easy and I think I will have no problems.. but now come the hard part. And I'm not sure about it so here I will need some help. I think will be something like : 

```

# Checking the partition for errors 
sudo e2fsck -f /dev/mapper/PCrevisie-home
# Because I want to reduce the home partition with 1GB 
sudo lvreduce -L -1G /dev/PCrevisie/home
# Now I want to add this 1GB to the root partition 
lvresize -L +1G /dev/PCrevisie/root
#Now I Need to lock the partition again 
sudo pvchange -x n /dev/mapper/crypt1 
#And now I must resize the filesystem 
sudo e2fsck -f /dev/mapper/PCrevisie-root
sudo resize2fs -p /dev/mapper/PCrevisie-root

```If I'm getting somewhere wrong will be very nice to get some assist.

---

### Post by WthIteh on 2012-02-14
Before reducing size of logical volume using lvreduce, it's required to reduce size of the filesystem. Otherwise lvreduce may corrupt it.
For reducing size of filesystem of /dev/mapper/PCrevisie-home you may use gparted.
Other parts of your process are OK.

---

### Post by apamix on 2012-02-14
Ok ;)) Here I got wrong :P 

Why I must reduce the filesystem when I just migrate the free place from /home to the root partition :) 

Thanks in advance for the answer :popcorn:

---

### Post by WthIteh on 2012-02-14
The logical volume in respect to the filesystem is like physical hard disk in non-LVM configurations. The filesystem of /home have thought it has n GB and so it may have placed some data at the end of its n GB space (some file creation/removal may lead to empty holes within the partition space). So reducing 1 GB by lvreduce without reducing filesystem itself first, can corrupt all files which are placed at the end of partition by filesystem (which is possible even if the partition has enough free space).

Indeed you do not move free space. You first remove it from one logical volume and when this task was finished completely, you add it to another independent logical volume ;)

---

### Post by apamix on 2012-02-15
Thanks for the good info :popcorn:.

---

