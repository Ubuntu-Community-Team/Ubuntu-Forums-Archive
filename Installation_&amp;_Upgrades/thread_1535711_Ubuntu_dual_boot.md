---
title: "Ubuntu dual boot"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by aspencade on 2010-07-21
I am a little experienced with linux, not really proficient with programming language but am having the following issue.
I have a Toshiba Satellite & have been running Windows & PC Linux dual boot.

Pc Linux is disconnecting / dropping the wireless signal when the phone rings,Phone, Internet, TV all through same modem.  Thought  I'd try Ubuntu, ran live cd for a couple of days, no problem
Decided  to install Ubuntu, During install it asked how i wanted to set up the  boot,
 1 - format whole drive - No
2 - Manual - No
3 - Along side  existing systems, Windows / PC Linux - Yes
4 - Went through install  defaulting everything
5 - Now, Windows & PC will not boot (option  is given @ start up)
 6 - When I try to access my old folders  (Win / PC Linux) they are  locked & I'm told I am not the owner  & do not have access.
7  - The pic attachment from Gparted  shows a "KEY" beside sda/3, 8, 9
8 - sda/ 3 -  Windows
 9 - sda/5 - PC Linux
10 - sda/8 - Ubuntu

My live CD was approx 1 year old & Ubuntu up graded to most recent after install. 

Can I repair /  restore Boot and regain access to the locked partitions ???? OR is it  reformat time ???

Thanks for any help..

---

### Post by lechien73 on 2010-07-21
The key icon just shows that the partition is locked - usually because it is mounted. In your case, sda3 is actually the extended partition "container", not Windows. The other mounted partitions are sda8 for Ubuntu and sda9 as swap. Your Windows partition is sda2.

There are a number of reasons why you may not be able to mount the partitions. The error message can be somewhat misleading. If the partitions are "dirty" - i.e. needing a disk check, then they could fail to mount. In which case, you could try forcing the partition to mount:

```
sudo mkdir /media/disk1
sudo mkdir /media/disk2
sudo mount -t ntfs /dev/sda2 /media/disk1 -o force
sudo mount -t ext4 /dev/sda5 /media/disk2 -o force
```

---

### Post by aspencade on 2010-07-21
Thanks Matt; you are making it sound better already, the partitions are in fine shape, I would like to replace PC linux with Ubuntu, & have a dual boot, can you give me directions to accomplish this & how to manipulate the partitions ?
As you can see the folders with the "X", I'm being told I do not have permission to view these ??
Thanks again

---

### Post by lechien73 on 2010-07-21
No problem. You can take ownership of the folders on the old Linux partition by opening a terminal window and typing:

```
sudo chown -R your-user-name: /path-to-folder
```

So, if you used /media/disk2 as the mount point for the PC Linux partition, as mentioned in my previous post, and your username was "bob", you could type:

```
sudo chown -R bob: /media/disk2
```

**[COLOR="Red"]IMPORTANT:[/COLOR]** This will change the owner and group details for *all* files and folders on this partition. PC Linux will most likely be completely un-bootable after this. This command is purely to give you access to the directories you're currently locked out of!

Thanks for your PM, I'll drop you a line a bit later :-)

---

### Post by lechien73 on 2010-07-21
Just sent you a PM. Hope it makes things clearer, or at least slightly less confusing!!

---

