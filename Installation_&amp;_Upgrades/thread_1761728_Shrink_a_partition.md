---
title: "Shrink a partition?"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by daniel.cotter on 2011-05-18
I have devoted my entire drive (320 GB) to my Linux (ext4) partition, along with swap space and a small extended partition, but am looking to install FreeBSD in dual boot (I know, that's a whole can of worms getting that set up).

Before I look further, I need to know if it's necessary to shrink the partition to make room for a new BSD partition -- and if so, how -- or if fdisk can cut a slice out of an active partition during the install process.

Thanks in advance,
Daniel

---

### Post by Xiah on 2011-05-18
I'd also like to know this. I've somehow managed to devote my whole 500gig HDD to the boot partition of the HD so now it won't load saying that there isn't enough space. Kind of important I get at the documents saved in the /home folder as well. I can't get access from my second HDD because it says it's locked and I can't unlock it either!

---

### Post by oldfred on 2011-05-18
@Xiah Please start your own thread as your problem in not related to FreeBSD. With a 500GB drive you should not have space issues but may have corruption and need e2fsck or other repairs. 

@daniel.cotter
Is not the issue that Linux does not have ZFS drivers? Or they are beta only. I think you have to shrink Linux partitions first, but have not tried FreeBSD. I think that was a systems others said it was better to just install on a second drive and even then it still had issues.

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-2/index.html)
Command line version
[http://www.howtoforge.com/linux_resizing_ext3_partitions](http://www.howtoforge.com/linux_resizing_ext3_partitions)

---

