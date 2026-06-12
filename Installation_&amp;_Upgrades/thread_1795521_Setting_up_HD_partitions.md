---
title: "Setting up HD partitions"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by Wiking on 2011-07-02
Hi, I want to install Kubuntu on my computer alongside W7.

So from what I have read Kubuntu requires around 4 different partitions. Do I make these partitions using Windows partitions tool before installation? So that when I install they are partitioned? Or do I just use the Kubuntu installer partition tool? 

My setup is like this:

HD 1
Drive C: Windows 7 - 33GB of 326 GB free

Drive E: ( 9GB Factory Partition I deleted - want to Install boot for Kubuntu here ) 

Do I format in Windows or just leave the space unallocated?

HD 2
Drive D: Docs, Videos - 40GB of 335GB free

HD3
Drive G: Docs, Videos - 77GB of 590GB free

Hard Drive 3 has around 70 GB free that I can use for the other partitions, do I do these partitions in Windows? Or using the Kubuntu CD? 

When installing I get 2 Guided options.

1 - To install Kubuntu on Drive: G wiping out the whole HD.

2 - To install Kubuntu on Drive: G using 45GB or 10% of space.

If I do option #2 will it erase the docs and videos currently on the HD? Will it be just 1 partion or several?

I wanted to ( using Manual partition )install the boot, and system files on HD 1 Drive: E, and the swap and /home partition on HD 3 Drive: G.

If I  make new partitions and re-size partitions using the Kubuntu CD will I erase any video, and doc files currently on my HDs? Or should I make these partitions in Windows and then install the respective Kubuntu partitions where I want them to go?

Or should I just buy a blank HD?

I'm sorry first Linux install.

---

### Post by Bucky Ball on 2011-07-02
Leave space unallocated (don't format in Windows as Ubuntu uses EXT file format which Windows knows nothing about). Leave free space and when you get to the partitioning part of the Ubuntu install choose 'Manual Partitioning' to select where you want to install and set up partitions (a separate /home is wise).

---

### Post by oldfred on 2011-07-02
+1 on Bucky Ball's suggestions.

I like to keep an operation system on one drive and have its boot loader also on that drive. Then if one drive fails the other drive is still bootable. Of course you can use liveCDs and should have current Windows repair CD and Ubuntu liveCD to make repairs if need be.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate them from drive to drive.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Bucky Ball on 2011-07-02
As oldfred says; the mountpoints he mentions are defaults in the 'manual partitioning' section of the install. Think it is 'Mount as?' and the drop down list has /, /home,/swap, and a heap of other defaults (/boot is also there).

You can create your own, too, if there is any need.

---

### Post by moore.bryan on 2011-07-02
Just to throw-in my two cents and add to the consensus; root and /home on different parts is a good idea... anything more is usually just overkill.

---

### Post by Bucky Ball on 2011-07-02
> **moore.bryan said:**
> ... root and /home on different parts is a good idea... anything more is usually just overkill.

I don't use any others, either, but 'horses for courses', moore.bryan. In some situations might be appropriate. ;)

---

### Post by oldfred on 2011-07-02
Herman posted some good comments on separate system partitions. I think they are more for servers or other with special requirements like RAID or LVM.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by moore.bryan on 2011-07-02
> **Bucky Ball said:**
> I don't use any others, either, but 'horses for courses', moore.bryan. In some situations might be appropriate. ;)

Nah, screw horses... ;-)

---

### Post by Wiking on 2011-07-02
Thanks to all.

So I can install the /boot and the system files into the 10GB of "free space", with the Kubuntu CD creating seperate partitions within that "free space" if it needs to for ( /boot, and / ).

Then I use the Kubuntu CD to resize my Drive: G thus creating more "free space" which I can then partition and allocate it to my /home and swap? All the while preserving the other 500 GB of files on my Drive: G

Should that work?

---

### Post by Bucky Ball on 2011-07-02
All good, but I would include a /home there also (or else your /home will be a *directory* inside the 10Gb / rather than a separate *partition* of whatever size you want - /home is where music, video, etc. live so you want that big).

There are other ways of getting around this but creating a separate /home good idea. If your system breaks or for any other reason you want to do a clean install your /home data is safe on a separate partition and you can just install the OS over / without losing anything (new install will use the existing /home and /swap). If /home is a directory inside /, then ...

---

