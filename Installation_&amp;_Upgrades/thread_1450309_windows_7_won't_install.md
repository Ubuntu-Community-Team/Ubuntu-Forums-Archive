---
title: "windows 7 won't install"
date: 2010-04-08
forum: Installation &amp; Upgrades
---

### Post by rudi009 on 2010-04-08
i tried installing windows 7 on a partition on my laptop but i'm getting this message:
"setup was unable to create a new partition or locate an existing system partition "

i tried googling and found that it has something to do with the number of partitions:
my hard disk layout right now:
p1 ext4 21gb /home
p2 ntfs 64gb
p3 ext3 18gb ubuntu installation
p4 swap 2gb
p5 ntfs 17gb created to install 7
p6 ntfs 31gb to store other stuff
i can't afford to reduce the number of partitions so is there any way around it???:confused:

thanks in advance for help..

---

### Post by Pressondude on 2010-04-08
I also had issues getting Win7 to install recently. After it had supposedly wiped my harddrive, GRUB was still there, though all of my partitions were gone...
I have since given up and gone back to XP

---

### Post by presence1960 on 2010-04-08
> **rudi009 said:**
> i tried installing windows 7 on a partition on my laptop but i'm getting this message:
"setup was unable to create a new partition or locate an existing system partition "

i tried googling and found that it has something to do with the number of partitions:
my hard disk layout right now:
p1 ext4 21gb /home
p2 ntfs 64gb
p3 ext3 18gb ubuntu installation
p4 swap 2gb
p5 ntfs 17gb created to install 7
p6 ntfs 31gb to store other stuff
i can't afford to reduce the number of partitions so is there any way around it???:confused:

thanks in advance for help..

You can only have 4 partitions- either 4 primary or 3 primary and 1 extended. Within the extended partition you can create as many logical partitions you want, the only limit being the size of the extended partition.

There is no way around that.

---

### Post by Pressondude on 2010-04-09
Can you help me with my issue? It wouldnt install at all, even though I told it to wipe the disk. The disk worked for two other computers.

---

### Post by oldfred on 2010-04-09
Windows wants to install in a primary partition. Linux, data and NTFS that are data only can be in logical partitions.
You could move your /home sda1 or your linux install sda3 and let windows install in those partitions. They do not look large enough so you will have to do a lot of moving of partitions also to give windows enough space.
Be sure to have all your data backed up.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by rudi009 on 2010-04-09
is there any way to shrink the extended partition to free up the free space under its domain to make that free space a primary partition?? right now i've my /home as primary and rest everything in one extended. i want to make that 17 gb one as primary too...

---

### Post by oldfred on 2010-04-09
You need to print your entries as the order is important. All the extended have to be in the one primary. I cannot tell what your order is. You also can delete swap and put a new one inside the extended, but would have to manually edit fstab to see the new UUID of the new swap.

```
sudo fdisk -l
```

---

