---
title: "Asking for advice migrating data to new harddrive."
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by CJNyfalt on 2010-11-17
Hi,

I got a new external 2 TB harddrive today, since my last one started having space problems.

Now I know how to make partitions, but the rest is causing problems.

1. How do I best transfer the data from an old partition to a new?

2. How should I set up my new partition scheme?
My old one is:
1 GB /
0.5 GB swap
82 GB /home
0.2 GB /tmp
4.1 GB /var
32 GB /usr
All of them except /usr and swap have become too small.
Would it be smartest to move home to the 2 TB drive, and redistribute the rest among the old drive?

3. Setting up fstab. I managed to do this in the old days, but this UUID stuff has me confused. Is there some program to configure it nowadays? Or some way to figure out the UUID?

---

### Post by CTBuckweed on 2010-11-17
> **CJNyfalt said:**
> Hi,

I got a new external 2 TB harddrive today, since my last one started having space problems.

Now I know how to make partitions, but the rest is causing problems.

1. How do I best transfer the data from an old partition to a new?

2. How should I set up my new partition scheme?
My old one is:
1 GB /
0.5 GB swap
82 GB /home
0.2 GB /tmp
4.1 GB /var
32 GB /usr
All of them except /usr and swap have become too small.
Would it be smartest to move home to the 2 TB drive, and redistribute the rest among the old drive?

3. Setting up fstab. I managed to do this in the old days, but this UUID stuff has me confused. Is there some program to configure it nowadays? Or some way to figure out the UUID?

well, I can't tell you how to partition up your new disk. That UUID stuff - each partition has a UUID associated with it. You can display each partition's UUID by the command 'ls -l /dev/disk/by-uuid'.

On my system, I have the root partition on a 34GB SCSI drive and /home is on a partition on my SATA drive. To separate /home from the root partition, I used the live CD and used tools in it to separate them out.

After I copied over the files from old /home to the new /home, I then edited /etc/fstab to mount the new partition that houses the newly copied files as /home on boot-up. I believe that ubuntu automatically creates a UUID for each partition it creates. Again, 'ls -l /dev/disk/by-uuid' shows the UUIDs for the partitions.

I hope that this helps. I also keep 2 bootable partitions on my system - one to fix the other if something screws up. Also, the live CD comes in handy when doing all the gritty-dirty work.

---

### Post by oldfred on 2010-11-17
Everyone has different opinions on the best way to partition. My standard suggestion:

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

I do not believe you need the system partitions separate. If you have a server or RAID then maybe you would need a separate /boot.

Herman on advantages/disadvantages of separate system partitions
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by CJNyfalt on 2010-11-18
Well, thanks for the answers so far. Still, there are things that I need a bit more clarifications on.

First this:
> **CTBuckweed said:**
> 
After I copied over the files from old /home to the new /home,

What is the favored way to copy over the files? cp? tar? dd? something else?

Second, what would be the need for the /tmp and /var partitions? My old /tmp has problems with larger movies, and my old /var is too small to upgrade to 10.10. 1 GB /tmp and 10 GM /var?

---

### Post by oldfred on 2010-11-18
If you do not make them separate partitions you do not have to worry about sizes. Your overall / including all the partitions you are making separate need some working room. I have heard that if writing a DVD you need the 4GB extra in / as it writes temporary files ( I assume into /tmp).

I saved 3 different ways to copy /home. For example with cp you have to be sure to use -a parameter or root takes ownership.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by wkulecz on 2010-11-18
Use rsync -ax to move the data.  Read up on it, its a great and powerfull tool.

Years of experience has shown me than partitions (other than a second one for swap) are counterproductive when you only have a single drive as it usually ends up one is filled while the other still has plenty of space.

You also increase data latency as the head has to move farther to skip the empty space in one partition to get data from the other.  With only a single partiton, on average the data is "closer" to previous head position.

My advice, unless you need to multiboot, anything other than / and swap on a single drive is only pain with no gain.

---

### Post by zalletn on 2010-11-18
i would do 
1) 100/200(ext3/4) gig is file system mount point "/" this way u don't need to separate it as swap /home /tmp /var /usr 
2)swap double amount of ur RAM
3)and the rest in another partition for music/pic/videos/etc.(ext3/4)
3.v2)or if u work with windows in the same PC 
create one more partition 100/200 gig (ntfs) for winwos needs
and the rest is NTFS partition so u can have the same files in both OS since windows does not support etx

that's what i have on my PC 
[IMG]http://clip2net.com/clip/m31684/1290098241-clipj19231-34kb.png[/IMG]

and u can always make ur second partition mount in ur home folder or any other folders for media files
[http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/]("http://mesanna.com/2009/02/02/how-to-mount-a-partition-automatically-in-ubuntu-linux/")

---

### Post by CJNyfalt on 2010-11-18
> **oldfred said:**
> 
I saved 3 different ways to copy /home. For example with cp you have to be sure to use -a parameter or root takes ownership.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


OK, I managed to migrate /home to my new external 2 TB drive. That helps me a lot. Thanks for the answers so far. :D

Still, things are not done yet.

Now the issue is moving and resizing the old drive.

AFAIK, I have two alternatives:

1. Fresh system install.

2. Move and resize the system partitions to use the space that was formerly used by /home.

Right now that drive is as following:
/ 1GB primary
rest in extended in the following order
- 0.5GB swap
- former /home, big
- 0.2 GB /tmp
- 4.1 GB /var
- 32 GB /usr

Concerning using only / and /home, the problem is that booting needs ext3, and I can't stand using ext3 for big partitions because of the long fsck times. So I want to use ext4 for the non-boot ones.

So is it possible to delete old home, move swap to the right, and shrink the extended partition?

---

### Post by CTBuckweed on 2010-11-18
The directories ( /media /mnt /proc /systmp ) are required to be on the system partition.

/tmp   needs to be there too - lots of application use it for temporary storage.

/lost+found should be on every linux partition (I think)

For copying all data to a new location, I use "cp -pR <fromDir> <toDir>" There may be other and better ways to do it.

---

### Post by oldfred on 2010-11-19
After using upgrade in place for years, I did clean install with Karmic and now am a fan of clean installs.

You can move partitions around with gparted. If you move too much, you may have to reinstall grub or edit fstab. But normally UUIDs do not change. 

I do not understand your comment on booting from ext3. You can boot from ext4.

---

### Post by CJNyfalt on 2010-11-19
> **oldfred said:**
> 
I do not understand your comment on booting from ext3. You can boot from ext4.

I read somewhere that GRUB can't handle ext4.

---

### Post by oldfred on 2010-11-19
You are correct for grub legacy prior to Ubuntu's 9.04 and some other distributions. Grub 0.97 has not been maintained for years and each distribution made tweaks even though the version was still 0.97.

When Ubuntu added the option of ext4 with 9.04, it modified grub legacy to boot ext4 partitions.

Grub2 boots ext4 but I think it will not boot some of the very newest partition formats.

---

### Post by CTBuckweed on 2010-11-19
wkulecz, thanks for the tip about rsync. There are so many new tools that I haven't yet discovered. I was a Unix programmer back in the '80s. Then I went on to QNX, then Windows programming. For Unix, I learned the tools I needed for my daily use and system maintenance. Now, there are so many extra tools to learn about.

It's so good to be out of all the Microsoft crap.

Tom

---

### Post by CJNyfalt on 2010-11-22
OK, I managed to resize the partitions with an Ubuntu 10.04 CD and GParted. Problem solved. Thanks everyone!

---

