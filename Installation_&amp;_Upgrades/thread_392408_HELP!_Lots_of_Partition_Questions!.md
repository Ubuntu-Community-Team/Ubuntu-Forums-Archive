---
title: "HELP! Lots of Partition Questions!"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-24
I am right now in the process of installing Ubuntu 6.10.

In the end, this is will mostly be a local file server running SAMBA, OpenSSH, and Apache2.

90% (at least) of the 500GB disk space will go towards the file server.

At the moment, I am using the Guided Partition:

#1 primary 498.6GB ext3 /
#5 logical 1.5GB swap swap.

Question #1: Should I use ext3 or LVM? I don't even know what the latter is.

Question #2: What is a mount point? 

If I think a mount point is what I think it is, I should consider creating one primary partition that is 98.6GB in size for the system and one 400GB partition with the mount point of /home since this is where most of the files will be stored for the file server.

Am I using correct logic here?

---

### Post by eapache on 2007-03-24
LVM I believe stands for Linux Virtual Machine (could be wrong). I think you should use ext3 (that's the normal linux fs, there may be something different for servers, but I doubt it).

As for the root and home setup, you are correct. If anything, I would make the system partition even smaller (unless you will be running a lot of large software on the server).

---

### Post by Holzmann on 2007-03-24
Thanks.

Would there be any advantage to giving the 400GB /home partition a FAT32 file system or does SAMBA kind of deal with that later.

Also, when I finally log in as root, will I still be able to simply type "cd /home" to get to that directory despite it being on a different partition? Or will I have to mount it first? And I assume that in the SAMBA configuration routine, I will be able to "point" it to that partition?

---

### Post by eapache on 2007-03-24
There is no advantage to giving it a FAT32 fs unless you want windows to be a able to read it when Ubuntu isn't on. Samba will share ext3 to a windows network with no problems.

Normally you would have to mount it first, but if you install it with that setup(as opposed to setting it up like that after install), it will be added to the list of partitions that get automatically mounted on start-up.

I'm not sure that you understand how mount works. Any higher-level software (cmd-line, samba, etc.) doesn't even recognize it as a separate partition, just as a folder on your root partition. They get linked together by the lower-level software.

---

### Post by Holzmann on 2007-03-24
So now I have...

#1 primary 98.6GB B F ext3 /
#3 primary 400.0GB  f ext3 /home
#5 logial 1.5GB  F swap swap

I didn't know if I should make #3 a logical or primary partition.

And I am not sure what the little "f" is all about compared to the big "F" on #1.

---

### Post by Holzmann on 2007-03-24
If you think my partition table looks good I will continue...

Thanks for your help.

---

### Post by Holzmann on 2007-03-24
No one can quickly proof my parition scheme?

I think I am ready to continue just need some added support.

---

### Post by Holzmann on 2007-03-24
Okay, I will assume that not commentary means I am on the right track.

---

### Post by hansoffate on 2007-03-26
Hi,

eapache was wrong in what he said LVM stands for.

Here is a link that describes it.  [http://ubuntuforums.org/showthread.php?t=385643&highlight=LVM](http://ubuntuforums.org/showthread.php?t=385643&highlight=LVM)

You partition scheme looks fine to me.  If anything your / partition may be too big.   I only have 10gbs for my /  partition which is plenty.  My fresh ubuntu install with mythtv is only around 5gbs.

I am switching from a non LVM to an LVM setup.  I am researching it currently.

-Hans

---

