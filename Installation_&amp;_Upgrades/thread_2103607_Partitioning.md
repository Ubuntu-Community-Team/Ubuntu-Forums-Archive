---
title: "Partitioning"
date: 2013-01-10
forum: Installation &amp; Upgrades
---

### Post by freddo63 on 2013-01-10
I'm getting rid of Win7 for good because as far as I see it 8 is worse  than any they've ever made, and besides which, I can't afford to buy a  new laptop to handle it. Anyways, I'm much more comfortable now with  Ubuntu and am planning on wiping the drive to redo my partitioning,  since i didn't know what I was doing before. I hope this is the right  place for me to ask this. I want to triple boot, Xubuntu, Backtrack, and  FreeBSD.

Here's what I want to allocate so far and I'm not really sure how much I  will allocate for FreeBSD, but my current plan will leave about 100GBs  on my 250 GB drive:
Xubuntu                BackTrack
/          2.5GB         /     2.5GB
/usr    40GB          /usr 15GB
/var    4GB            /var 5GB
/tmp   10GB         /tmp  5GB
/home   40GB      /home   20GB
swap    4GB          swap is shared with the other one

Anyways, I intend to use Xubuntu for normal everyday use and then play  around with BackTrack and begin learning about security auditing. I also  want to put in FreeBSD to learn UNIX . I intend this only for my own  personal use, and I got these sizes from the recommendations from the  ubuntu online manual (if that's what it was... =/)

I hope someone can give me yes or no on whether this sounds good as soon  as possible, because it's 7pm here and I hope to have at least Xubuntu  installed sometime before 10pm tonight. Also, I wonder if creating a  partition for /boot so that the boot manager can be changed as necessary  when I install the other two operating systems. Also, I intend to  install Xubuntu first, then BackTrack, and then FreeBSD. Does that sound  like an alright order to go in?

Thank you guys so much for all the help you can provide me with!!!

---

### Post by nothingspecial on 2013-01-10
> **freddo63 said:**
> 
Xubuntu                BackTrack
/          2.5GB         /     2.5GB
/usr    40GB          /usr 15GB
/var    4GB            /var 5GB
/tmp   10GB         /tmp  5GB
/home   40GB      /home   20GB
swap    4GB          swap is shared with the other one


Hi, you really don't need all those partitions. One / partition would be fine. You might want a seperate /home or a data partition but partitions for /tmp, /usr and /var are unnecessary.

---

### Post by ibjsb4 on 2013-01-10
You may find a data partition useful.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by freddo63 on 2013-01-10
> **nothingspecial said:**
> Hi, you really don't need all those partitions. One / partition would be fine. You might want a seperate /home or a data partition but partitions for /tmp, /usr and /var are unnecessary.


Alright, so that only makes things more complicated I suppose? What about a /boot for the triple boot GRUB that will probably get replaced a couple of times? And if I do a /data, can that be a single one for both Backtrack and xubuntu? and recommended allocations? So does the /data take care of whatever programs I want to install via the package manager? Such as games and other things?

and any specific order I should install the OSes in?

---

### Post by oldfred on 2013-01-10
You cannot share /boot, and should not share /home although if systems are very close some have said it works (at least for a while). Many settings in /home may conflict with different versions, if doing an upgrade to a new version it adds new settings, but then old version may get confused.

Programs are in / (root) normally but some can be installed in /home.

---

### Post by Bufeu on 2013-01-10
> **nothingspecial said:**
> Hi, you really don't need all those partitions. One / partition would be fine. You might want a seperate /home or a data partition but partitions for /tmp, /usr and /var are unnecessary.
Why not? If you have more than one drive you actually want to decide where to put /tmp, /usr and /var.

---

### Post by freddo63 on 2013-01-10
> **oldfred said:**
> You cannot share /boot, and should not share /home although if systems are very close some have said it works (at least for a while). Many settings in /home may conflict with different versions, if doing an upgrade to a new version it adds new settings, but then old version may get confused.

Programs are in / (root) normally but some can be installed in /home.

Ok so am I mistaken in thinking that /boot holds the bootloader? Can you tell me what order to install these three OSes if I should want all three to show up in the bootloader, or does it matter?

Ok fine don't share /home, but /home or /data?

---

### Post by freddo63 on 2013-01-10
> **Bufeu said:**
> Why not? If you have more than one drive you actually want to decide where to put /tmp, /usr and /var.

Yes sir, but I don't have more than one drive, I just want to partition things, and heard that separating those makes it easy to repair stuff later. However, since I will be the only user on my laptop, I have an inkling that one or more of those really are unnecessary.

---

### Post by oldfred on 2013-01-10
Herman goes the other way and has just /. He does not even use swap as a partition so eveything can share the same unused space.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

---

### Post by freddo63 on 2013-01-10
> **oldfred said:**
> Herman goes the other way and has just /. He does not even use swap as a partition so eveything can share the same unused space.

       Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Cool, so it looks like I'm going to be doing just that, having a single /, although I doubt I won't have a swap partition, because frankly the swapspace programs sounds a little iffy to me from their description (esp when I saw the 44gb thing in their test run). Besides, I've read that BackTrack can break if you install too many extra things not from the same repositories, and so I figure, why not just have a 4gb swap and be done with it. Oh and should I go with Reiser or ext 3 or 4? what are the pros and cons between those or should I google that?

Anyways, that still leaves one question, is there an installation order I should follow or is that just for windows, since microsoft is such a bum? would it be good to have FreeBSD on the first partition or does that matter?

Oh and I suppose a thank you is in order for all of you who posted above!

---

### Post by oldfred on 2013-01-11
I have not kept track of the BSD, but some where are year or two ago someone posted than one of the BSDs did not play well with Linux. They suggested a separate drive. I do think BSD has to be a primary partition and has its own file system, so I assume that is part of the issue.

While ext4 is not always first it is near the top in almost all cases. Only if you have very specific file sizes (like a media server) may another be better.
       Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox ssd
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

---

### Post by Bufeu on 2013-01-11
> **freddo63 said:**
> Yes sir, but I don't have more than one drive, I just want to partition things, and heard that separating those makes it easy to repair stuff later. However, since I will be the only user on my laptop, I have an inkling that one or more of those really are unnecessary.
Yeah, separating thing making it's easier to repair something. I recommend to at least put /boot, /tmp and /home on different partitions.

---

### Post by Herman on 2013-01-11
> Yeah, separating thing making it's easier to repair something. I  recommend to at least put /boot, /tmp and /home on different partitions.How?

It's easy enough to chroot into a one-piece installation and run most commands that a person might need to use for repairing almost any major operating system problem.
Splitting the installation up into separate partitions makes setting up a chroot environment quite a bit more complicated, (and unnecessarily so).

Besides that it's easier and faster to maintain a single file system and it's easier to recover if necessary, and easier to make a single back up and restore a single partition from a single backup if that's ever necessary.

How can making the operating system more complicated by splitting it up into many partitions make maintenance and repair tasks easier, simpler or faster?

---

### Post by freddo63 on 2013-01-11
> **Herman said:**
> How?

It's easy enough to chroot into a one-piece installation and run most commands that a person might need to use for repairing almost any major operating system problem.
Splitting the installation up into separate partitions makes setting up a chroot environment quite a bit more complicated, (and unnecessarily so).

Besides that it's easier and faster to maintain a single file system and it's easier to recover if necessary, and easier to make a single back up and restore a single partition from a single backup if that's ever necessary.

How can making the operating system more complicated by splitting it up into many partitions make maintenance and repair tasks easier, simpler or faster?

THANKS!!!!! I agree with Herman, although I would like to hear a response to his last question if possible.

---

### Post by Herman on 2013-01-15
Machtelt Garrels explained some of the best reasons I've seen in favour of multiple partitioning scheme for Gnu/Linux installations in  [Introduction to Linux A Hands on Guide]("http://tldp.org/LDP/intro-linux/html/index.html"). I agree very much with what she has to say. 

Chapter 3 is particulary relevant to the current discussion, but I have enjoyed re-reading the entire book. The way I understand it she is recommending using separate partitions for servers, and for single user workstations pc a single / and swap is best.

---

