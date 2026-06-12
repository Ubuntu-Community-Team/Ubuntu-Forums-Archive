---
title: "larger than 32gig"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by StolenNomenclature on 2010-11-09
I would like to do a Wubi install of Ubuntu on both Windows 7 and Windows Vista using a pseudo-partition larger than the maximum 32gigs listed in the drop down box. Can someone show me the easiest way this can be accomplished?

Let me preempt some of the anticipated replies by stating for the record that:

1. I really do need to do it.
2. I am not interested in alternatives or anyone who wants to tell me that partitions are better.
3. I'm all growed up and can handle the possible repercussions like my hard disk exploding or the PC catching fire.
4. I don't give a monkeys whether anyone dislikes the idea or approve of it - its me that is going to do it, not them.
5. Free software is all about choice.
6. I swear that no one will die as a result of this, nor will the Earth drop out of orbit and crash into the Sun.
7. I will be eternally grateful.

Thanks.

:P

---

### Post by bcbc on 2010-11-09
Install Ubuntu - choose a 4GB installation.

DISCLAIMER... some of the commands shown (dd, mkfs) can cause a lot of damage if used incorrectly. I typed this in 5 minutes or less, so... consider that.

Boot it, then go to a command line:
```
# make yourself root
sudo -i
cd /host/ubuntu/disks
# create new virtual disk
# if you want 100GB, that's 100000
dd if=/dev/zero of=new.disk bs=1MB count=100000
#format
mkfs.ext4 -F new.disk  
#mount and copy files
mkdir -p /media/newdisk
mount -o loop,sync /host/ubuntu/disks/new.disk /media/newdisk
rsync -av --exclude '/sys/*' --exclude '/proc/*' --exclude '/host/*' --exclude '/mnt/*' --exclude '/media/*/*' --exclude '/tmp/*' --exclude '/home/*/.gvfs' --exclude '/root/.gvfs' / /media/newdisk
umount /media/newdisk
rmdir /media/newdisk
exit
```

Boot back into windows, rename new.disk to root.disk (after dispatching current root.disk.

---

