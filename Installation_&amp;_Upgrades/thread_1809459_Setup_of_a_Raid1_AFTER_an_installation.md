---
title: "Setup of a Raid1 AFTER an installation"
date: 2011-07-21
forum: Installation &amp; Upgrades
---

### Post by akazia on 2011-07-21
Hello 

I have a working installation of ubuntu 10.10 with one harddisk aktive. Now I like to add a second disk and create a Raid1. I Thought that this might not be common but also not a too strange wish. Well I was surprised to find only few information. 

Unfortunately I run at a very late phase in a problem an I hope that the experts her may can help ..?

Most of my actions are based on information from [this page]("http://arstechnica.com/civis/viewtopic.php?p=21332270")


**So what are the steps I have done already?**
1. I started a live CD unbuntu 11.4 with both disks unmounted

2. I added the partitiontabl from the full disk to the empty disk
```
sfdisk -d /dev/sda1 | sfdisk /dev/sdb1
```

3. I created the raid array
```
sudo mdadm --create /dev/md0 --level=mirror --raid-devices=2 /dev/sdb1 missing

```

4. create the filesystem on raid array
```
sudo mkfs.ext4 /dev/md0
```


5. mount Raid array and full disk
```
sudo mount -t ext4 /dev/md0 /media/raid1
sudo mount -t ext4 /dev/sda1 /media/tb1

```


6. copy all data from the full to the empty disk
```
rsync -av /media/sda1/ /media/raid1
```

7. unmounten  the full original disk
```
sudo umount /media/sda1
```

**HERE THE PROBLEM STARTS:**
8. add the full disk to the raid array
```
sudo mdadm --add /dev/sda1
```

The error message tells me that/dev/sda1 is no md device
Wahts wrong here - concerning to the above mentioned link this would be the next step. 


Beside this I have some more Questions:
- who do I tell the system that is should now use /dev/md0 instead of /dev/sda1 as root -- I guess -> /etc/fstab

- do I need to write something to the mbr of the second disk?

- do I need to update grub??


I hope that you can help here - I have googled so much but I must have missed to solution...

Thanks a lot
Michael

---

