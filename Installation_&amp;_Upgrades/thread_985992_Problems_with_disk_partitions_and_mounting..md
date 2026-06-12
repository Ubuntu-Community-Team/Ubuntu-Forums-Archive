---
title: "Problems with disk partitions and mounting."
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Smithy963@hotmail.com on 2008-11-18
Hi guys,

I recently decided to give Linux a blast - and Ubuntu was my choice,

The problem:

During the manual disk partition on installing i set these partitions:

Partition size - File system - Mounting point

6gb - swap area

30gb - Ext2 - /
40gb - Ext2 - /usr
20gb - Ext2 - /boot

Now the trouble is when the installation is all done and dusted,
I have 1 file system (30gb) - whats more is, the other directories that I stated should be on other partitions, are on my 30gb partition.

Is there any infomation I can be pointed towards that address's this issue.

Thanks in advance, 

Smithy.

Ps. The reason I would like a solution to this problem is because I read some material that says I need separate partitions for /root and /usr.

---

### Post by Elfy on 2008-11-18
Can you run these 2 and post the outputs please

```
sudo fdisk -l
df -h
```
First will need your password - it will be invisible, that is normal.

If you actually have those partitions then I would say that they are vastly oversized - I have 5 or 6 different setups on my pc and the /boots for all of them come to less than 200Mb :)
There is a lot of info on the net about linux and seperate partitions but most advice here would be the opposite. I've never needed to use seperate partitions other than /home but I believe that it can be useful if you're running a server installation.

You might be better of reinstalling and redoing the partitions - if you do and have updated you can backup the updates so you don't need to download again.

---

### Post by Smithy963@hotmail.com on 2008-11-18
[SIZE="1"]Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb673b673

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1019     8185086   27  Unknown
/dev/sda2   *        1020        5903    39223489    7  HPFS/NTFS
/dev/sda3            5904       16967    88871580    5  Extended
/dev/sda5            5904        6632     5855661   82  Linux swap / Solaris
/dev/sda6            6633        9064    19535008+  83  Linux
/dev/sda7            9065       13927    39062016   83  Linux
/dev/sda8           13928       15143     9767488+  83  Linux
/dev/sda9           15144       16967    14651248+  83  Linux
shaun@shaun-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda8             9.2G  458M  8.3G   6% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  104K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  104K  1.5G   1% /dev/shm
lrm                   1.5G  2.0M  1.5G   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda6              19G   49M   18G   1% /home
/dev/sda7              37G  1.7G   34G   5% /usr
/dev/sda9              14G  164M   13G   2% /usr/local
[/SIZE]


Haha, I guess I've been discovered - I'm a noob from windows.

I assumed mounting the directories to different partitions would create multiple file systems within Computer.

The previous post was just an example - i didnt really give /boot 10gb lol. 

If i right click File System in Computer though - it says I only have 8.3gb free?

---

### Post by Smithy963@hotmail.com on 2008-11-18
Ah, if i enter filesystem, right click - properties on usr folder - it says i have 17gb free.

Ok would you be so kind as to help me set up a new partitioning scheme...

3 gb RAM - ive heard x2 and x1.5 - I'm going with the x2

6gb swap area

10gb - /
the rest of my space - /home 

?

will that ensure i can upgrade without losing any important data - but still allow me to install an unlimited amount of GBs worth of applications?

---

### Post by Linteg on 2008-11-18
> **Smithy963@hotmail.com said:**
> [SIZE="1"]
If i right click File System in Computer though - it says I only have 8.3gb free?
Well it's because / only has 8.3 gb free. your setup is not like you wrote in the first post, you have:
/ 9.2Gb
/home 18Gb
/usr 37Gb
/usr/local /14Gb <- a complete waste of space


You could also have used use the "File Systems" tab of the system monitor (System->Administration->System Monitor).

I do second forestpixie on reinstalling. The following would probably be ok in your case:
/ 10-20Gb
swap 1gb (as little as you want to but more than nothing)
/home the rest
if you feel like it you could have a small /boot partition with 200-250Mb

The 2xRAM in swap is an OLD rule of thumb which should be ignored nowadays.

---

### Post by Smithy963@hotmail.com on 2008-11-18
I'm sorry for the confusion on what dirs i gave to what partitions - i couldnt remember properly, and just gave examples. - i don't care much for putting /boot on a separate partition.

My main aim is the ability to upgrade and still keep my /home.

Also do you happen to know where all my applications/games/etc. are installed to ? is it /home ? or should i manually install everything to /home from now on ?

I'm planing on having greater than 10-20gbs worth of application installs.

---

### Post by Elfy on 2008-11-18
Ok - if you're going to reinstall and want loads of room for apps then maybe go for 20Gb as / but I doubt if you'll use it.

Remainder as home once you've dealt with some swap space - Linteg is right - up to a point - if you want to hibernate then SWAP must at least equal RAM so if that's the case then SWAP of 3.2Gb will be more thna enough - if you don't hibernate then maximum of 1Gb should do it - if you find it's not you can add swap files later.

---

### Post by Smithy963@hotmail.com on 2008-11-18
Ok. I think I got it - going for round no.5 or something like that.

Thank you very much for your help.

---

### Post by Bartender on 2008-11-18
Something else that might be helpful - take a screenshot of your partitions.
With the Ubuntu LiveCD up and running, plug in a USB thumb drive.  Wait for it to appear on the desktop.  Take note of its description - if confused, go into Places>Computer and you'll see something like /dev/usb
Now go to the partitioner.  When the partition map is up, mouse over to Applications>Accessories>Screenshot and take a screenshot.  Save to the thumb drive.  Get back out of the LiveCD, boot into Windows, attach the screenie to a post.
Some of these guys who live and breathe Linux can read fdisk -l easily.  Pictures are easier for me!

---

