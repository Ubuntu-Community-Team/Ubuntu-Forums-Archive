---
title: "NTFS  worrys!!"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by coire on 2010-08-14
Hi people!

Ok, last night I was completely off my head on some strange substances and unable to sleep and since i recently got a new laptop (came with win7...ugh), I decided to install ubuntu on the second partition, which was already there. So off i went in search of a live cd. Found Ubuntu 10.04 and booted it up and installed as per usual. Or so i thought, the install partition was ntfs and I didn't format it. It seems to have installed fine but I'm now wondering if there are any stability issues or anything else i should worry about?

All the info I could find on the subject seemed a little outdated.:o

---

### Post by tommcd on 2010-08-14
> **coire said:**
>  I decided to install ubuntu on the second partition, which was already there. So off i went in search of a live cd. Found Ubuntu 10.04 and booted it up and installed as per usual. Or so i thought, the install partition was ntfs and I didn't format it. It seems to have installed fine but I'm now wondering if there are any stability issues or anything else i should worry about?

Well, does Ubuntu boot up and run ok ... or what ???
If you chose automatic install and partitioning (or what ever it says exactly) the Ubuntu installer would have formatted the partition to ext3/4 or whatever the default was, or whatever file system you chose.
Assuming the system is running OK, post your /etc/fstab file here.

---

### Post by linux18 on 2010-08-14
so you installed ubuntu on  an ntfs partition, and its still ntfs?  you'll need to defrag and it will be slighty slower all the time.

---

### Post by coire on 2010-08-15
My bad. I just panicked when i could still see the partition in my computer in windows. Turns out its a recovery partition for windows. Funny thing is its only 6.6gb and I never even noticed! i never even checked the contents, just seen it and wondered if windows had included support for ext filesystems and panicked when i seen NTFS.
Thanks a lot any people, greatly appreciated!

---

