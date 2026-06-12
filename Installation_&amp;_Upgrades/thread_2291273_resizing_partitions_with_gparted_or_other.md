---
title: "resizing partitions with gparted or other"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by richard130 on 2015-08-19
Hi,

So I recently set up a dual boot windows 7 and ubuntu 15.04 wherein I had a best guess at the volumes I would need on my hard drive, supposedly safe in the knowledge I could just resize them later. However, I have more of an idea of what I will need now and I can't seem to resize my ubuntu partition(s) (swap/ext4) because, for some reason, the installer put the swap inbetween the windows and ext4 partitions viz.
[ATTACH=CONFIG]263938[/ATTACH]

Explicitly the move/extend/shrink options are greyed out for the swap space/extended partition even after I've shrunk the windows partition (sda3) (I'm trying to extend sda6). Does anyone have any idea how I can manage this?

Thanks,

Rich.

---

### Post by dino99 on 2015-08-19
note about tweaking partitions:
- always do with unmounted partitions; so boot with 'gparted live' first
- shrink windows with its tool, and ubuntu with its app
- let windows at the beginning of the device

note2: making change(s) to linux (ubuntu) partition(s) will also change its uuid; so grub needs to be updated to pick up the neew uuid(s)

---

### Post by grahammechanical on 2015-08-19
As Dino99 says, the Extended partition and the two logical partitions inside it are mounted (the icon of a key tells us this).

But do not forget that the partitioner is showing us a graphical representation (an image) of a circular disc. Actually several discs stacked on top of each other. So, the position of a partition in a linear drawing does not accurately repesent the actual positioning of the data on the hard disk. But it is useful for resizing and moving partitions. 

By the way, that screen shot is not showing any unallocated space between sda3 and sda4. The Extended partition (sda4) cannot be expanded to the left at the moment. Once sda4 has been expanded to the left, you can move sda5 (swap) also to the left and that will leave unallocated space in front of sda6 which can now be expanded to take up the unallocated space.

When I move and resize partitions not only do I do it from a Live session but I also do it one action at a time. We can queue up actions but it will then take a long time for all the actions to be finished. I like to see each action finished before I start the next. That is just my way of working.

Regards

---

### Post by Bucky Ball on 2015-08-19
If you have resized your Windows partition using Gparted I suggest you reboot immediately and check Windows is still booting. Win for Win partition manipulation should be rule of thumb. Using Gparted can seriously screw things.

As for the extended partition, you need to shrink sda3, boot from live ubuntu install media and grow the extended partition then switch off and delete the /swap. grow the EXT partition inside the extended to the limit of the extended, shrink it from the other end and recreate the /swap there.

Hope that makes sense. If not:

Shrink sda3 with Win
Boot from live media and 'Try Ubuntu'
Grow sda4
Delete sda5 /swap
Grow sda6
Shrink sda6 by 2Gb at the other end
Create /swap at the end of the drive (after sda6).

Good luck. :)

---

### Post by oldfred on 2015-08-19
Becuase swap has no data, it is one of the easier partitions to just delete and recreate. You can shrink your / (root) and create new swap at end of drive. Then it is out of the way. When you reboot it will give an error that it cannot boot old swap as UUID now does not exist, but easy to edit fstab with new UUID.
       # Find your UUID:
sudo blkid -c /dev/null -o list

   sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a

I might also shrink / partition and create a shared NTFS data partition. Then that partition can have data for both Windows & Ubuntu and make it easy to share data. Best not to mount Windows system partition in Ubuntu (or just read only) but just the shared NTFS data partition.

---

### Post by richard130 on 2015-08-20
Thanks! For reference, I did:

```
sudo swapoff -a
```

Then did as Bucky Ball said (both from live cd), then (because grub's account of the hard drive was knackered)

did


```
sudo mount /dev/sda5 /mnt

sudo grub-install --root-directory=/mnt /dev/sda
```

again from livecd, 

then did as oldfred said (from sda5). 

When I first deleted swap it spat a load of errors at me, and then wouldn't let me resize sda5, but after a reboot it seemed fine.

Thanks,

Rich.

---

### Post by Bucky Ball on 2015-08-20
Good news! Enjoy. :)

---

