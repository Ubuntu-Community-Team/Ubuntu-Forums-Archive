---
title: "&quot;Just Looking&quot; at 12.04.1 messed up current installation ?!?!"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by michaelveloz on 2013-02-02
Hi there
I have 10.04 installed with raid support via mdadm ..and everything was running fine.
 
I'm considering installing 12.04.01 but wanted to first know if the installer was going to give me lvm options like I have with 10.04 - 
 
So I downloaded the alternate installer and ran it just far enough too see the partition editor come up. At that point I rebooted, without moving ahead with any partition options or installation options. I was "just looking"..
 
But now when I try to reboot back to my 10.04 installation I get "error fd0 and get dumped to a grub rescue prompt. Does the installer whack the MBR or something before the point you even instruct it to do anything???
 
I had not yet backed up important data on my 10.04 installation and am not sure what to do at this point??
 
Any suggestions would be very much appreciated!
Michael

---

### Post by debodas on 2013-02-02
I would reinstall grub following the steps here: [http://www.noobslab.com/2012/10/installrecover-grub-from-linux-live-cd.html](http://www.noobslab.com/2012/10/installrecover-grub-from-linux-live-cd.html)

Make sure to install onto the correct partition. Does this fix your problem?

---

### Post by michaelveloz on 2013-02-02
When I execute the first command there "sudo mount /dev/sda2 /mnt" it says "mount: unknown filesystem type 'Linux_raid_member'
 
Guess these instructions assume you don't have a software raid??

---

### Post by darkod on 2013-02-02
With mdadm the devices are /dev/mdX, not /dev/sdaX. Always have that in mind before running commands no matter what any tutorial tells you.

Also, the live cd doesn't include the mdadm package so you would need to add it, assemble the arrays, and try reinstalling grub2.
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That should assemble all found md devices. Mount at /mnt the correct one and run grub-install to the correct disk devices like /dev/sda, /dev/sdb, etc.

But you are right, without continuing the install it should usually leave things alone. And the alternate cd will recognize mdadm and lvm and it will offer reusing those devices. You didn't need to start an install process just to check that.

Also note that the above commands are if you have only mdadm. If you also have lvm on top of it, you need to add lvm package too and activate the LVs, so you actually mount the root LV for the grub2 reinstall.
```
sudo apt-get install lvm2
sudo vgchange -ay
```

---

### Post by michaelveloz on 2013-02-04
Well I assembled the instructions from the two posters above into this:
 
1. sudo apt-get install --no-install-recommends mdadm
2. sudo mdadm --assemble --scan
3. sudo mount /dev/md126 /mnt
4. sudo mount /dev/md126 /mnt/boot
5. sudo mount --bind /dev /mnt/dev/
6. sudo chroot /mnt
7. grub-install /dev/md126
 
The final messages I got from grub-install are: Attempting to install GRUB to a partition instead of the MBR. This is a bad idea, and embedding is not possible, but this is required when the root device is on a RAID arrary or LVM.
 
notes:
- In step 2, mdamd's assemble command created the device /dev/md126, which I used for the remainder of the commands
- I understand that in step 7 you should not specify a partition but instead, a disk, which is why I probably got the error message I did. But in the case of my raid, I'm not sure what the disk device name is..  is it just "/dev/md"?   If I specify /dev/md to grub-install I get "Unknown kind of RAID Device'.
 
So I feel like I'm really close, but the final right step is evading me.
 
(Also, after executing the above steps I can no longer do an 'fdisk -l' .. which I had hoped to do to possibly get a clue as to how to specify my raid device to grub-install.)
 
Thanks for any ideas!!!

---

### Post by darkod on 2013-02-04
Look more carefully in my previous post. I mentioned that grub-install should be run on /dev/sda, /dev/sdb, etc, the disks, not partitions. With SW raid grub2 doesn't go to the mdX raid devices, it goes to the actual physical disk. The mdX devcies in SW raid are assembled on OS level, so grub2 is not on them.
So, if the md126 is made of partitions/disks on /dev/sda and /dev/sdb for example, step 7 would be:
grub-install /dev/sda /dev/sdb

In your steps you posted, you can't run both 3 and 4. /dev/md126 is either the root partition, in that case you mount it at /mnt, or it's your separate /boot partition if you have one, in that case you mount it at /mnt/boot. But not both.

If you don't have separate /boot partition when you installed, you don't need step 4, forget it. Without separate /boot partition boot is only a folder inside /.

---

