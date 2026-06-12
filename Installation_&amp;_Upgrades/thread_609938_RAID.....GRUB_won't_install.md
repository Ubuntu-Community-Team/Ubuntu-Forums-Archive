---
title: "RAID.....GRUB won't install"
date: 2007-11-11
forum: Installation &amp; Upgrades
---

### Post by rkillcrazy on 2007-11-11
I recently built a new PC as the older one was getting...well...old.  I do this for a living so this is just another walk in the park for me.  However, I was running Windows Vista and, frankly, the more I use it the more I hate it!  I really only installed it so I could "learn" it as I'm an IT Tech for Windows-base machines and their networks and I need to be able to support it.  Having given you the background, I'll go on to describe the issue...

Windows Was set up using the "hardware" RAID controller on the ASUS board.  Windows had no issues installing it.  I know it's not a true "hardware" RAID setup and I tried to install Ubuntu as a second boot option but that failed.  I broke the array and started from scratch.  I set up the RAID array in the ubuntu setup as outlined in several wiki and forum posts I'd read before.  It goes through the setup just fine and fails on the GRUB install.  Then it gives me the following error:

```

You will need to boot manually with the /vmlinuz kernel on partition /dev/md0 and root=/dev/md0 passed as a kernel argument.

```

Does anyone know how to fix this?  I figured since the OS installed just fine that GRUB will follow suit.  Obviously I was wrong.

11-11-07
1406 EST
RKillcrazy

---

### Post by rkillcrazy on 2007-11-12
Bump.

I'm so used to getting a response within hours or even minutes.  What happened to you guys? :)  Tell me I'm the first one with this issue!

11-12-07
1333 EST

---

### Post by rkillcrazy on 2007-11-13
I think I may have figured it out.  I've tested this out on a VM-machine and I'll test further once I get home tonight.  For now, I'm pretty damn confident it'll work.

Again, I'm not using the "fake" hardware raid (some call it a hybrid raid) and I'm setting up the raid set as a RAID-0 via the ALTERNATE install disk.

**How I did it:**
Without looking at the screens I can't give accurate names and descriptions of the screens but I can still rough it out.  Anyone else who is looking for a *HOWTO* should do some searching as I found several out there that were good enough to get me started.  Anyway, once the screens got to the partitioning area of the setup, the first thing I did was make a 256MB partition on the first drive.  I placed the partition at the "front" of the disk but I'm sure it can be placed anywhere.  I left it set to be used as ext3 but set the mount-point as **/boot**.  Then, I set up 2 large partitions (one on each physical disk, about 140GB each) and set them up to be used as a RAID volume.  I then got into the RAID configuration screens and set them up as a RAID volume.  After that was done, I got back into the partitioning screens and set up 2 more small partitions (one on each physical disk, about 1.5GB each) and set them to be used as a RAID volume.  Then I got into the  RAID configuration screens and set them up as a RAID volume.  I went back into the partitioning screens and set the large RAID volume as the root partition and the smaller RAID volume as the swap area.  Because I only had 2 physical drives, I had a very small amount of the disk left due to the various partitions and the odd one being the /boot partition.  In short, DISK-0 had 3 partitions; one for the boot and the other 2 were the root and swap partitions.  DISK-1 had 2 partitions; one for the root and the other was the swap.  Obviously, for it to work in a RAID, the root and swap partitions were set up with the exact same sizes on both of the physical disks and that's why you have a couple MB left over on the second disk which doesn't get used.

I hope this helps the next person who tries to set up a RAID-0.

11-13-07
1029 EST

---

### Post by rkillcrazy on 2007-11-13
Well, I was able to test on a real machine and I'm currently typing this out using the machine I was having trouble with.  SO, it looks like it works fine if you create a **/boot** partition to install GRUB to.

11-13-07
1841 EST

---

