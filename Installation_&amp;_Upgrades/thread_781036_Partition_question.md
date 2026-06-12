---
title: "Partition question"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by geovino on 2008-05-03
When I was about to install Hardy last week I used a new hard drive and created a / (100GB)and a /home partition (145GB)  and swap before the installation. Was that the correct way to do it? I am not sure that I have use of the /home partition now. I thought that it is good to have a /home partition. I do see that in the file manager that I have 206.8 GB free of the original 250 GB hdd. So maybe I do have use of all the space.

Everything is working very well and I don't want to redo partitions at this point. Should this be a concern? 

I was also looking for GParted and it's not listed. I wanted to make a snapshot to show the partitions.

---

### Post by Bakon Jarser on 2008-05-03
> **geovino said:**
> When I was about to install Hardy last week I used a new hard drive and created a / (100GB)and a /home partition (145GB)  and swap before the installation. Was that the correct way to do it? I am not sure that I have use of the /home partition now. I thought that it is good to have a /home partition. I do see that in the file manager that I have 206.8 GB free of the original 250 GB hdd. So maybe I do have use of all the space.

Everything is working very well and I don't want to redo partitions at this point. Should this be a concern? 

I was also looking for GParted and it's not listed. I wanted to make a snapshot to show the partitions.

gparted isn't installed by default.  if you want it it is in the synaptic package manager.  it sounds to me like it installed everything on a single partition.  I like to have a seperate partition for my home folder because if I have to do a reinstall i don't have to delete all the custom settings for my programs, but you'll be fine without one.

---

### Post by zvacet on 2008-05-04
You can check your free space with 

```
df -h
```

and i think 100GB for root is to much.It depends what are you want to do but I have my root on 10Gb and it is not  half full.Maybe if you want to use servers and other  things,but it is to big anyway.You can resize it (if you want) with [Gparted live Cd.]("http://gparted.sourceforge.net/")

---

### Post by geovino on 2008-05-04
> **zvacet said:**
> You can check your free space with 

```
df -h
```

and i think 100GB for root is to much.It depends what are you want to do but I have my root on 10Gb and it is not  half full.Maybe if you want to use servers and other  things,but it is to big anyway.You can resize it (if you want) with [Gparted live Cd.]("http://gparted.sourceforge.net/")

Here's my $ df -h

davek@davek-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             226G  7.2G  207G   4% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   60K 1014M   1% /dev
devshm               1014M   48K 1014M   1% /dev/shm
lrm                  1014M   38M  977M   4% /lib/modules/2.6.24-16-generic/volatile
gvfs-fuse-daemon      226G  7.2G  207G   4% /home/davek/.gvfs
davek@davek-desktop:~$ 


How should it be? or does it matter? 

Otherwise, everything runs great. Hardy is and best Ubuntu I've used.

---

### Post by HunterThomson on 2008-05-04
I don't realy under stand what the out put you posted meens exept that it looks like you have an execivly larg partiton for your /boot???

This is one thing my $50 book came in handy for. I set my harddrive up like this.

150M label /boot format ext2 primary
4000M format swap (no need to label) primary
18000M label /   format ext3 logical
(the rest of the drive like 220GB) label /home  format ext3 primary

I did this when I installed Ubuntu. I chose "Manual" when I got to the partitioning part. If you set it up like this and you reinstall you have to use the same user name and password. You also have to use the manual partitioning if you do a reinstall and re-label the partitions back to /boot, /, /swap and /home. You also check the box 'format' for the /boot and / partitions but don't format /home. Also, I have both KDE and Gnome on my laptop and a bunch of programs and I only use like 6GB of my / ((root partition)) but keep in mind that you want to have like 20% free space on a partition... so don't make the / partition smaller then say 10GB if you ask me.

---

### Post by Pumalite on 2008-05-04
If you do an 'Automatic' installation, the installer will take most of the available space for '/' and leave 4 to 6 GB for /swap depending on the size of the HDD, Home will hang from '/'
Much better is to use Gparted Live CD and apply this scheme:
20 GB for '/'
1 GB for /swap (/swap=RAM in laptops for hibernation)
The rest for /home.

---

