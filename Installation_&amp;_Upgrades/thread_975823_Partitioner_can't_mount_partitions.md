---
title: "Partitioner can't mount partitions"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by etoD on 2008-11-08
I have 4 partitions on my hdd: 
a. ntfs partition with XP
b. ntfs partition with Vista
c. ext2 - blank, waiting for ubuntu
d. swap partition.

when i choose to write to disk however, an error tells me that the vista partition could not be mounted.

a. can I fix this?
b. when i set it to not mount, a message then comes up "the partition will not be used at all." if i continue, ignoring that (because that's fine really), will it format the partition?

thanks
m

p.s. it's probably relevant that this is server edition

---

### Post by taurus on 2008-11-08
Are you trying to install Ubuntu to a vista partition?  Just tell the installer to use the empty ext2 partition and you don't have to mount those two windows partitions right now if you don't want to.  You can mount them later after you have installed Ubuntu.

---

### Post by etoD on 2008-11-08
Nah the ext2 is mounted to /.
It's just the fact it can't mount the two ntfs partitions, is sort of annoying.

---

### Post by taurus on 2008-11-08
So you have already installed Ubuntu (server version) to your machine?  If you want to mount those two ntfs partitions, you just need to add two entries in /etc/fstab so they would be mounted automatically each time you boot Ubuntu.

Edit /etc/fstab

```
sudo nano -Bw /etc/fstab
```
and add these two lines at the end of it.

```

/dev/sda1   /media/sda1   ntfs-3g   defaults,locale=en_US.utf8  0  0
/dev/sda2   /media/sda2   ntfs-3g   defaults,locale=en_US.utf8  0  0

```
Save the chances by holding down <Ctrl> while pressing x.  Answer the question with Y.

Now, you need to create two new mount points and mount them.

```
sudo mkdir /media/sda1 /media/sda2
sudo mount -a
df -h
```

I assume your ntfs partitions are /dev/sda1 & /dev/sda2, okay.  If not sure, look at the output of this command from a prompt.

```
sudo fdisk -l
```

---

### Post by etoD on 2008-11-08
Yep yep. Was just wondering why the installer couldn't automatically mount them. Kinda odd. And since it also says "the partitions will not be used at all" after saying "It will also destroy all data on partitions which are not used" or words to that effect, obviously a bit concerned. :P

---

### Post by taurus on 2008-11-08
You have to tell the installer to mount them when you install it.  Otherwise, it will not touch your windows partitions.

---

### Post by etoD on 2008-11-08
No, I mean.. I did tell it to mount them. And it came back with an error saying it couldn't, and to go back to the partition tool.

---

