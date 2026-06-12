---
title: "[SOLVED] Cant install Dapper"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by bazil270 on 2007-12-03
Im trying out the dapper live cd. I cant access my hda at all. it says cannot mount drive. I'm currently using windows to use internet since my linux still cant use the internet. oh and i tried installing it to the
hard drive but it also said the same thing. I think it sees my hard disk as a removable drive but cant make sure of it.:confused:


Any ideas?

Thanx in advance

PS: I'm a complete NOOB so dont expect me to understand certain things.

Please post Step by Step so i can follow. Thx

---

### Post by foxmulder881 on 2007-12-03
> **bazil270 said:**
> Im trying out the dapper live cd. I cant access my hda at all. it says cannot mount drive. I'm currently using windows to use internet since my linux still cant use the internet. oh and i tried installing it to the
hard drive but it also said the same thing. I think it sees my hard disk as a removable drive but cant make sure of it.:confused:


Any ideas?

Thanx in advance

PS: I'm a complete NOOB so dont expect me to understand certain things.

Please post Step by Step so i can follow. Thx

You obviously don't have enough free space on your current drive to install Ubuntu.

Download the GParted LiveCD and create some free space. Then install Ubuntu on the free partition.

---

### Post by bazil270 on 2007-12-03
how many gbs do i need?
i currently have 17.7gb freed up just so i can use ubuntu.

and oh yea this com has only abt 40 gb of hd. lame right?

---

### Post by Pumalite on 2007-12-03
That will do. But Ubuntu does not install in unallocated space, Needs to be a partition.

---

### Post by bazil270 on 2007-12-03
it is a partition. In windows it looks like:

C:/ 
D:/

I freed up D completely and it has 17.7gb of memory. I just cant access them or look into any hd for any files in dapper. Cant Mount Drive

---

### Post by Pumalite on 2007-12-03
In Vista, you have to allocate space for Ubuntu WITH the Vista partitioner. In XP, get Gparted Live CD and resize your XP partition. Then install Ubuntu.

---

### Post by bazil270 on 2007-12-03
will that solve my problem of not being able to access the hda?

I'm really concerned if i mess up during the partitioning since i have never done repartioning before.

and another thing, gparted can be used in linux right? but my linux cant access the internet yet. and if i download t to windows, i cant access the file i downloaded.

---

### Post by foxmulder881 on 2007-12-03
Once installed Ubuntu, then install **ntfs-3g** package. This will allow you to access your Windows mounts.

---

### Post by bazil270 on 2007-12-03
but the problem is that i **cant** install it. not even can i access the files in my computer in linux.

---

### Post by Pumalite on 2007-12-03
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by bazil270 on 2007-12-03
still cant access the drive. i did as u said. and still the same problem. 

what do u suggest.

---

### Post by gaylapdancer on 2007-12-03
You say you can see it from your Windows? That indicated that it is already partitioned and **formatted** to ntfs or fat. If it is XP or Vista you use then it is likely to be ntfs, and Ubuntu can't install to it.

I recommend using the GParted live CD to delete the partition where you want Ubuntu to be, in this case the 17.7GB partition.
Then when installing Ubuntu, when it gets to partition options, use "Largest Continuous Free Space" option, and it will do it's thing with the newly freed space.

---

### Post by bazil270 on 2007-12-04
that sounds good. i'll try it out. thx a lot! ^^

one question tho. even if it is ntfs, ubuntu shd be able to **see** whats inside right? or access it? it's like sumthing is blocking access to it. Keeps saying, Could Not Mount Drive, when i double click the hd icon in "Computer". That shdnt happen right?

---

### Post by bazil270 on 2007-12-04
vm thx guys. i just got it right. all i did was download the newest version of ubuntu and ho and belo, i'm running mozilla in ubuntu now. Yay! :popcorn::popcorn::popcorn::popcorn::guitar::):KS

---

