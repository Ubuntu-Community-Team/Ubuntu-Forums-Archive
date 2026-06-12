---
title: "HD fault diagnostic"
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by jalirious on 2012-07-24
Hi, I had a idea and wondered if it could be possible.

I cleverly dropped my netbook on the floor. 12.10 still booted, but there was a problem mounting the /home partition (I suspected the head had knocked into the disc).

Tried reinstalling with new partitions - failed due to a HD fault.

What I would like to do is this:

1) Find out at which point of the 0-160gb disc the physical problem lies.

2) Make a slim partition that includes the bad sectors of the disc which is ignored in the subsequent installation.

I am stuck at 1). Any ideas? The position would need to be found by a bootable disc.

---

### Post by jalirious on 2013-02-01
In the end, I was able to resuscitate, despite the ****** hard drive.

I just halved the disk with the partitioner, ignored the first half and set up the install on the second half.

Runs fine. Your mileage may vary.

---

### Post by tgalati4 on 2013-02-01
You can run badblocks on the first partition:

```
sudo badblocks /dev/sda1 > badblocks.txt
sudo fsck -cc /dev/sda1
```

The first command just lists the bad blocks to the console or a text file, so you can see how many there are.  The second command marks them in the filesystem for that partition so that they are no longer used.  If the bad blocks are in a narrow range, then you can partition around them.

---

### Post by jalirious on 2013-02-06
Sweet! Ta for the heads up.

---

### Post by jalirious on 2013-02-07
NB - you need to unmount the scanned partition, as the -cc can cause data / disc corruption if not.
[http://linux.die.net/man/8/e2fsck]("http://linux.die.net/man/8/e2fsck")

---

