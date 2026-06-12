---
title: "How to remove an MDADM Raid Array, Once and For All!"
date: 2008-08-09
forum: Installation &amp; Upgrades
---

### Post by NickZA on 2008-08-09
Hi Folks

This is a short howto using mainly some info I found in the forum archives  on how to completely resolve issues with not being able to kill mdadm RAID arrays, particularly when having issues with "resource/device busy" messages.
Note full kudos to the two people who made 90% of this possible, again I would have added to the original thread but sadly it was too old.

<[author: slackwarejosh]>

Alright,

I had the exact same problem today and finally figured out how to solve this.
I'll write up a n00b from the beginning in case I have to go back and find my solution later

How to remove an MDADM Raid Array

1. Find out your arrays (md0, md1, etc..) using

```
sudo fdisk -l
```

2. Query your arrays to find out what disks are contained using

```
sudo mdadm --detail /dev/md0
 (or md1 or whatever)
```

3. Shut down the array using

```
sudo mdadm --stop /dev/md0
```

4. And here's the magic key ...... zero the superblock FOR EACH drive
```

sudo mdadm --zero-superblock /dev/sda (or hda)
sudo mdadm --zero-superblock /dev/sdX...
```

I hope I helped..I am pretty new to linux and software RAID, and I never join forums, but I just started using Ubuntu and it's so darn community-centric I just had to sign up and give back.

Keep Rockin! :guitar:

<[author: zaziork]>

3. Shut down the array using

```
sudo mdadm --stop /dev/md0
```

Before the above step, I needed to unmount the array first, otherwise I got the "device is busy" failure.

```
sudo umount /dev/md0
```

<[end. see original thread here [http://ubuntuforums.org/showthread.php?t=394281]](http://ubuntuforums.org/showthread.php?t=394281])>

"Ok, back over to you, Nick."

One thing I just discovered in addition to the above, instead of
```
sudo umount /dev/md0
```
do
```
sudo umount -l /dev/md0
```
...This will do a lazy unmount, see man umount:
```
       -l     Lazy unmount. Detach the filesystem from the filesystem  hierar&#8208;
              chy now, and cleanup all references to the filesystem as soon as
              it is not busy anymore.  (Requires kernel 2.4.11 or later.)

```

My circumstances were particularly troublesome due to the way I tried to delete the array with no regard for configs as though I were a Windows user or something :) My first disk in the array simply refused to be used in the creation of a new array although I'd cleaned up all the RAID config stuff. It claimed the resource was busy. umount -l did the trick.

Any further issues you are having with unmounting you may want to try these steps as well:

[http://ubuntuforums.org/showthread.php?t=122743](http://ubuntuforums.org/showthread.php?t=122743)

Happy raiding!

-Nick

---

### Post by cncook001 on 2010-08-12
To actually finish the removal of the array you also need this command     ```
sudo mdadm --remove /dev/md0
```

---

### Post by mikiemorales on 2011-09-18
Thanks guys. This actually helped me a lot!

---

### Post by masuch on 2012-02-23
thanks, helped me as well.

---

### Post by oldos2er on 2012-02-23
Closed, necromancy.

---

