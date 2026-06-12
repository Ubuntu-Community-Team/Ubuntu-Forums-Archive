---
title: "Partitioning Hard Drive"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by scratched on 2006-03-21
I plan to install Ubuntu on my external hard drive this afternoon using DaBruGo's Installation guide. The hard drive I'm using is a 200GB drive and already has a 90GB partition with data that I don't want to lose and can't reformat. I have partitionMagic so I'm going to create an ext2 and swap partition using that.

What I want to know is, how big should my swap partition be, and does it matter where the ext2 & swap partitions are located on the drive (should they be at the beginning or end?)

---

### Post by Aewheros on 2006-03-21
You don't have to use partition magic, the ubuntu installer can leave your existing partition alone without problems.

A rule of thumb is to have a swap equal to the size of your ram but there is nothing wrong with adding 50% (or even more) extra just to be sure.

---

### Post by yota on 2006-03-21
Hi, a rule of thumb about swap can be so set it to be 1.5 times your ram.
It doesn't matter where the partitions are, as long you reference them correctly, but please consider the more modern ext3 instead of ext2 as a filesystem for your installation.

Now some questions and (unrequired ;) ) advices: why do you want to use partition magic istead of the partitioner in the ubuntu install? Probably the latter would be easier.
And moreover, is this your first ubuntu installation? If so i suggest to play a while with it somewhere else before installing on disks containing data you fear loosing.
An emulated environment such as vmware is perfect for experimenting.
Ubuntu by itself is perfectly safe, but it's better to gain some experience with the tool before using it, expecially since the installation on an external HD puts extra complexity in.

Hope this helps!

---

### Post by scratched on 2006-03-21
I have used linux for a little while now, but only on live CDs. I've tried out ubuntu and Knoppix live and I feel that I can handle an actual installed distro and all the complexities of installing it on an external drive. I consider myself fairly tech savvy, I've just never installed a linux distro yet.

I'm not** too **worried about losing the data on the hard drive since it is just a backup of another computer of mine which I can backup again any time if data gets destroyed. I'd just prefer not to have to copy 80 gigs of data over again;). 

To answer your question about using partitionMagic, I already have the extra 110GB partitioned to NTFS so I was going to re-partition it since I wasn't sure if ubuntu would be able to partition the already existing NTFS partition correctly.

Now I'm curious though, what things could happen to my hard drive if something went wrong during installation:confused: ?

---

### Post by DaBruGo on 2006-03-21
[QUOTE=scratched]I plan to install Ubuntu on my external hard drive this afternoon using DaBruGo's Installation guide. The hard drive I'm using is a 200GB drive and already has a 90GB partition with data that I don't want to lose and can't reformat. I have partitionMagic so I'm going to create an ext2 and swap partition using that.

What I want to know is, how big should my swap partition be, and does it matter where the ext2 & swap partitions are located on the drive (should they be at the beginning or end?)[/QUOTE]

scratched,

Let me know how the install goes for you.


DAVE

---

### Post by scratched on 2006-03-21
It didn't work completely. I don't think I messed up **too **much, but I got an error when ubuntu loads. I posted details on DaBruGo's thread about USB installation.

[post #309]("http://ubuntuforums.org/showpost.php?p=847764&postcount=309")

---

