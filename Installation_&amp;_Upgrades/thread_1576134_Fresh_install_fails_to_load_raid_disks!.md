---
title: "Fresh install fails to load raid disks!"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by andymcca on 2010-09-16
Hello,

I'm trying to install 10.04.1 from the alternate installation CD onto a 2-disk raid array using mdadm. I can set up all of my partitions, create the raid devices, and install the OS to them. However, when I reboot after completing the installation:
* Grub loads
* initramfs loads
* initramfs fails to load /dev/md0 (my /) and /dev/md2 (my /home), complaining about degraded status
* I get dumped to an initramfs prompt.

At this point I can run
```
mdadm -S /dev/md*
mdadm -A /dev/md0
mdadm -A /dev/md2
exit
```and the OS boots fine. However, the problem comes right back after a restart. The mdadm.conf UUIDs seem to match the mdadm -Ds results. Any clues as to why the initial assembly attempt is failing? Let me know what information I can provide.

Thanks in advance!

***UPDATE***
It appears if I add devices by hand to mdadm.conf, the partition is assembled automatically at bootup? I did this with device names like /dev/sda5, etc. I will try to use by-uuid names next, and post back. It appears perhaps the line
```
DEVICE partitions
```which appears in mdadm.conf by default is not working? In any case this seems like something which should be worked around automatically during an install.

***UPDATE 2***
After a few hours of testing I have determined that my raid assembly fails any time I attempt to define devices in mdadm.conf with wildcards. That is,
```
DEVICE partitions
DEVICE sd*
```etc all fail.
In fact,
```
DEVICE /dev/sda5 /dev/sdb5 /dev/sda7 /dev/sdb7 /dev/sda8 /dev/sdb8 /dev/sd*
```fails, so even if I explicitly state the devices but then throw in a wildcard nothing gets assembled. My final working copy (in full) is:
```
# mdadm.conf
#the following was automatically generated and I did not mess with it:
CREATE owner=root group=disk mode=0660 auto=yes
HOMEHOST <system>
MAILADDR root

#my stuff:
DEVICE /dev/sda5 /dev/sdb5 /dev/sda7 /dev/sdb7 /dev/sda8 /dev/sdb8
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=4384d20c:66616f4e:7995638d:58efe975
ARRAY /dev/md1 level=raid0 num-devices=2 UUID=91b479e3:e89be956:aec481ba:c6bfe0a7
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=42bae81d:71b13219:1ff44cfa:0ee06a66
```Sadly, this is not very general. If my device names change (which will happen in about 10 minutes when I add the rest of my hard drives), I will have to do the whole initramfs manually assembly dance again.

Any thoughts? Where should I take this for a possible bug report?

***PS***
Anyone reading this and having a similar problem:
after to edit mdadm.conf, you need to run
```
update-initramfs -u
``` to update the copy that gets loaded before your root partition is loaded (ie the one that is used to assemble your drives). At least, this is definitely the case when / is on a RAID array.
If you have to boot off a livecd to rescue your install, you can:
install mdadm (sudo apt-get install mdadm), 
then assemble whatever your partitions are (sudo mdadm -A /dev/md? /dev/sd?? /dev/sd??), 
mount your root device (sudo mkdir /media/tmp; sudo mount /dev/md? /media/tmp), 
mount your boot device (if it is seperate from root) (sudo mkdir /media/tmp1; sudo mount /dev/md? /media/tmp1), 
bind the livecd proc directory over your root's /proc (sudo mount --bind /proc/ /media/tmp/proc/),
bind your boot over your root's /boot (sudo mount --bind /media/tmp1/ /media/tmp/boot/),
chroot into your installation (sudo chroot /media/tmp/)
and finally update your initramfs (sudo update-initramfs -u)
ctrl+d to leave the chroot, restart, and your mdadm.conf will be updated!
Phew! Good luck!

---

### Post by andymcca on 2010-09-16
updated main post :D

---

### Post by TopicMapper333 on 2010-09-17
Thanks for the tip about update-initramfs.

I have been having LOTS of problems interestingly similar to yours, and as a result I have learned something that is perhaps of value to you.  It's kind of convoluted, so bear with me, please.

Briefly: to avoid one horrible problem I've been having, I've learned that I must never put a RAID volume partition at the high end of the disk.  This is because /proc/partitions lists raw disks as well as partitions thereof, and because by default mdadm RAIDs have their superblocks at the high ends of their partitions.  If the high end of the disk is also the high end of a RAID volume partition, then mdadm, as, at boot time, it shuffles through all the available partitions, thinks that, for example, /dev/sdd and /dev/sdd3 are two partitions that somehow have identical superblocks, which confuses the situation enough to cause booting to fail.

Now with your clue about update-initramfs, I'm suspecting that editing /etc/mdadm/mdadm.conf so that it doesn't say "DEVICE partitions" and instead is explicit about what's what, and then running update-initramfs, the confusion I described above wouldn't occur.  HOWEVER, that solution won't solve another little problem.  When using the alternative installer on disks that already had a RAID on them with volumes at their high ends, the installer, too, checks /proc/partitions and it thinks it has RAIDs that don't exist and that it can't delete, even if you have zeroed the low ends of the disks in order wipe out their partition tables!  In order to make it possible to re-install Ubuntu 10.04, I've had to  zero whole disks, which is pretty tedious.  (Just zeroing the first and last 2% of each disk seems to work, but that too is pretty tedious.)

I also have another problem -- unreliable booting, which I have reported in launchpad at [https://answers.launchpad.net/ubuntu/+question/125823](https://answers.launchpad.net/ubuntu/+question/125823)  You might be interested in that one, too, Andy.

I still have no clue about the latter!

---

### Post by andymcca on 2010-09-17
> **TopicMapper333 said:**
>  In order to make it possible to re-install Ubuntu 10.04, I've had to  zero whole disksInteresting. I think I have also had this problem. I found that a "mdadm -S /dev/md*" seemed to clear it up though. It seemed like some zombie partial raid setup had been left alive (undead?) and I had to blow it up before I could assemble the full array. May be an entirely unrelated issue, though!

Edit: Oh yeah, and I know you mentioned the alt disk, but when I tried on the standard livecd and installed mdadm, I found that using gparted to reformat partitions which had been part of mdadm arrays always failed. Creating the partition I wanted, and then running mkfs.ext4 worked fine though. Wierd.

> **TopicMapper333 said:**
>  I also have another problem -- unreliable booting, which I have reported in launchpad at [https://answers.launchpad.net/ubuntu/+question/125823](https://answers.launchpad.net/ubuntu/+question/125823) I have been having startup problems also! Mostly my home directory (which is the final partition on both disks! related to your earlier observation?). Usually it boots, but sometimes I have to do a manual assemble. In particular, this has been happening when /dev/sdc and /dev/sdd are present. I even noticed that blkid is listing the last few /dev/sda and /dev/sdb partitions last... Was thinking this might have something to do with the order they were initialized. I had suspected a delay in assembling the RAID, and added a rootdelay=25 to /etc/default/grub and ran update-grub. The last few boots have been fine, but of course it is taking longer than I wish it would.

Anyway, I will try rebooting a few times right now, and will post back if I see the problem resurface. I agree with your bug post, though, that I am not seeing my 25 second delay (which I thought was forced? perhaps it works like rootwait and starts up once it sees / ?). Did you run update-grub? :D

***EDIT***
OK, so I realized 1) you don't need to run update-grub if you edited /boot/grub/grub.cfg, although this will get blown away whenever you update the kernel or add new drives I think.
2) I forgot that with my pathetic 4 sata ports on this motherboard that I had switched my 2 old hdds out for two optical drives. This seems to correlate with no boot problems.

Upon putting the other two hard drives in, I received an error message on my first cold boot that /dev/sda8 did not exist (this is part of my /home array), but it booted anyway. 4-5 restarts booted fine. Then another cold start failed to load /home entirely. I got to do the mdadm assembly dance at the rescue prompt. This worked fine. Typed exit and it continued to boot and launched X, gnome, etc just fine. Obviously not ideal, though. And since you said you have RAID 5, I'm assuming you can't get down to two drives :D

---

