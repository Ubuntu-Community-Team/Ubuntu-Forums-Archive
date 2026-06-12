---
title: "Can I have RAID1 and RAID5 with 3 HDDs?"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by Akhran on 2006-10-12
I have partitioned my 3 harddisks into the following configuration:

/boot 100MB with RAID1 on sda1, sdb1, sdc1
swap  1GB with RAID5 on sda2, sdb2, sdc2
/     the rest of the harddisk space with RAID5 on sda3, sdb3, sdc3

After reboot, I installed GRUB on sdb and sdc:

# grub
# > device (hd0) /dev/sdb
# > root (hd0,0)
# > setup (hd0)
# > device (hd0) /dev/sdc
# > root (hd0,0)
# > setup (hd0)
# > quit
#

To simulate a harddisk failure, I unplugged sda. During bootup, I have the following error output:

```

Assembling RAID array md2...done (already running).
Assembling RAID array md0...failed (no devices found).
Assembling RAID array md1...failed (no devices found).
Assembling RAID array md2...done (already running).
Will now check all file systems.
fsck 1.39 (29-May-2006)
Checking all file systems.
[/sbin/fsck.ext2 (1) -- /boot] fsck.ext2 -a -C0 /dev/md0
fsck.ext2: Invalid argument while trying to open /dev/md0
/dev/md0:
The superblock could not be read or does not describe a correct ext2 file system. 
If the device is valid and it really contains an ext2 filesystem (and not swap or 
ufs or something else), then the superblock is corrupt, and you might try running 
e2fsck with an alternate superblock:

e2fsck - b 8193 <device>

fsck died with exit status 8

File system check failed.

A maintenance shell will now be started.

```

Is it because RAID1 and RAID5 don't play nice together on the same system?

Appreciate any help on this.

Thanks !

---

### Post by kidders on 2006-10-12
Hi there,

I'm not quite sure why that happened ... there's no reason you can't use two RAID versions on the same PC afaik. Which arrays failed?

It all seems a little unnecessary though, in that putting swap on RAID at all (not to mind RAID 5) will *drastically* slow down your paging performance. In addition, I can't think of a single reason to put /boot on RAID.

Perhaps the best idea would be to try again, with a simpler setup, and see what happens.

**Edit:** It would be hard to overstate the danger of spreading more than one RAID array over the same set of physical disks. Are you really sure you want to do that?

---

### Post by Akhran on 2006-10-12
Hi,

1) Assuming I have swap on 3 harddisks and if they are not on RAID, will that crash the system if the harddisk that is currently doing the swapping fails?

2) How would you partition or configure the RAID(s) to have a high availability system with 3 harddisks?

Thanks !



> **kidders said:**
> Hi there,

I'm not quite sure why that happened ... there's no reason you can't use two RAID versions on the same PC afaik. Which arrays failed?

It all seems a little unnecessary though, in that putting swap on RAID at all (not to mind RAID 5) will *drastically* slow down your paging performance. In addition, I can't think of a single reason to put /boot on RAID.

Perhaps the best idea would be to try again, with a simpler setup, and see what happens.

**Edit:** It would be hard to overstate the danger of spreading more than one RAID array over the same set of physical disks. Are you really sure you want to do that?

---

### Post by kidders on 2006-10-12
Hey again,

Unfortunately you are correct. If you *really* need reliable swap space, you may have to resort to RAID. I'm curious though ... what kind of a system are you running that requires that level of reliability?

I'm uncertain of how to pitch my response to your question :-( Chances are that if you are experienced in high-reliability systems, none of this will be of any use to you, but here goes ...

If you consider the possible points of failure on a Ubuntu box with a single swap partition (and appropriate power management), the most obvious are not really storage-related. Thus, keeping swap space alive in the event of a disk failure is usually a relatively low priority, given that the only side-effect would be a brief service interruption. You would still be exposed to other hardware failures (CPU, PSU, RAM, northbridge, etc...), that would have a more damaging effect. RAID is used primarily where a physical disk failure would lead to disasterous data loss, rather than a few minutes' of loss of service.

You could consider making a distinction between irreplaceable data and "dispensable" data. In other words, you would create two identical Ubuntu boxes, where the only difference between them was a single RAID array, containing critical information you simply can't afford to lose. In the event of some kind of problem that crashes or kills one box, you would simply plug the array into the other and carry on. If such an interruption was unacceptable, using ATA over ethernet to keep a replica array in sync might be an option. You could perhaps use a failover system (Heartbeat?) to manage the switch.

I guess my point is that if the level of reliability you require is so high that you are considering putting /boot on RAID, you should consider an approach that involves more than one machine. At any rate, in practice, there are often techniques you can use to minimise the effect the loss of active swap space will have on a system, giving you the opportunity to deal with the problem.

I'm very conscious that this post doesn't address **anything** in your original question ... sorry for that ... but I couldn't help wondering, when I read it, whether you weren't doing something odd! Can I ask what kind of computer you're using, and whether the RAID array is physical or logical. You see, the other issue that concerns me is whether 3 disks is really enough -- knowing a little about your hardware would help me get an idea of the probability of *two* disk failures in close succession.

---

