---
title: "partition created while installation is read write protected"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by deeptiaggarwal on 2009-11-28
i have newly installed ubuntu 9.10 in my system.during installation, i create 2 partitions 1 as /root and other as /data. now this /data partition is not shown inside. there is one data folder in file system which is read n write protected. is this the same partition i created or it is just another folder...
hoe shud i get /data partition

---

### Post by phillw on 2009-11-28
can you post the output of
```
sudo fdisk -l
```
and 
```
df -ha
```

It'll let us see what you have (mounted)

Regards,

Phill.

---

### Post by presence1960 on 2009-11-28
> **deeptiaggarwal said:**
> i have newly installed ubuntu 9.10 in my system.during installation, i create 2 partitions 1 as /root and other as /data. now this /data partition is not shown inside. there is one data folder in file system which is read n write protected. is this the same partition i created or it is just another folder...
hoe shud i get /data partition

you need to change permissions on /data. here is a GUI solution. Open file browser and mount data by clicking on it.

Now open a terminal and run ```
gksu nautilus
```

Go File System > media > data. Right click data and choose properties. Click the permissions tab. set owner as your user name and set folder access to create & delete files.

Set group to the group you belong to. Set folder access to access files. Close and should now have read/write priveledges on /data. I am not sure- you may need to reboot.

---

