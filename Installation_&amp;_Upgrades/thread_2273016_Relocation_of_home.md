---
title: "Relocation of /home"
date: 2015-04-10
forum: Installation &amp; Upgrades
---

### Post by zkab on 2015-04-10
I have a new system with 2 disks (sda & sdb) and want to make a fresh installation of Ubuntu server on sda1.
sdb1 I want to use for /home and data.

I will use [use entire disk] option to install Ubuntu on sda1.
After the installation is done and rebooted I will ...

1. sudo mkfs.ext4 /dev/sdb1
2. specify in fstab that /home will be on sdb1 like ...

UUID=0c89eb5d-ac58-46c0-b309-597b35a542e8 /home ext4 defaults,errors=remount-ro 0 1

where UUID is for sdb1.

Will this work ?

---

### Post by Elfy on 2015-04-10
Create partitions during the install. Use Something Else (or whatever it's called lately) at the partition stage, you'll be able to specify / and /home there before you install. No need to fiddle afterwards

---

### Post by zkab on 2015-04-10
OK - but don't I have to specify size (not sure what to specify) for 'Use Something Else'

/
/boot
swap

For [use entire disk] option then Ubuntu would grab what it needs ...

---

### Post by Elfy on 2015-04-10
You said you were going to install, then create partition for home, then add it to fstab. 

I'm saying create the partition during the install.

Not sure where size comes into it, you'd have to know how big it was the other way too.

---

### Post by zkab on 2015-04-10
OK - thanks.
When I checked some documentation the LVM option seems exciting - have no experience in LVM but I will test it ...

---

### Post by Bucky Ball on 2015-04-10
You may also fall on your derrière as LVM can cause some issues if you are not using it for a specific purpose and/or are fairly familiar with its pros and cons. One way to learn about them, though. ;) 

As Elfy says, choose 'Something Else' and create your /home partition on sdb during install. Much easier. As for sizes, get a piece of paper and a writing implement, grab your favourite beverage, sketch out your hard drives and their sizes and make a plan rather than waiting until you get to the partitioning section of the install to decide what goes where and how big. Best way. Good luck.

---

### Post by dino99 on 2015-04-10
if you only need a 'standard' installation (no additional needs for heavy apps or programming dev) we usually set :
/ about 10/12 gb
swap about 4 gb (with hdd, no really need if ssd with large ram)
/home the rest of the disk

note: lvm is not mature and have many issues needing some knowledge to get around

---

### Post by Bucky Ball on 2015-04-10
2Gb is all you need for /swap, unless you intend hibernating, in which case same size as your installed RAM. ;)

---

### Post by zkab on 2015-04-10
Thanks for all your input - most valuable.
I read the LVM documentation carefully and it is pretty straight forward and not hard to understand.
What makes me hesitate is when you say that it is not mature yet ... strange to hear that when it has been around for quite a while.
So maybe the best solution is to - [COLOR="#0000FF"]get a piece of paper and a writing implement, grab my favourite beverage, sketch out my hard drives and their sizes[/COLOR] - and go for the simple  'Something Else' solution ...

A nice weekend to all of you.

---

### Post by oldfred on 2015-04-10
This user seems to like LVM, but posts both pros & cons. 

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I prefer reliability, so the idea that any drive failure causes loss of all data on both drives makes me not to want to use LVM. But if using a server you should have good backup procedures anyway and that is assumed if using LVM.

---

