---
title: "Dapper ==&gt; Edgy -- Broken if you have RAID"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by theosib on 2006-10-27
I had started a thread in the Edgy development forum about issues with upgrading and software RAID.  It appears that I'm not alone in my concerns about breakages when upgrading from Dapper to Edgy.  There are reports from others about issues with Ubuntu having broken support for software RAID, and reports from others about breakage when upgrading if your system has RAID.

Here are a few references:

[http://www.ubuntuforums.org/showthread.php?p=1664050](http://www.ubuntuforums.org/showthread.php?p=1664050)
[https://launchpad.net/distros/ubuntu/+bug/68308](https://launchpad.net/distros/ubuntu/+bug/68308)

I would like to open up a discussion with other people here to share their experiences with software RAID, problems they encountered during initial install, fixes for that, problems with upgrading to Edgy, and suggestions for dealing with that.

I strongly suggest checking out the launchpad link above, which links to a number of other bug reports involving software RAID.  The more discussion here and submissions to launchpad, the sooner we'll see these issues addressed.  We need people who are willing to back up their files, take the risk of upgrading, report their results, and work with developers on identifying and fixing the problems.  

If you have problems, please discuss them here, but always remember that the launchpad bug tracker is your friend.  It helps developers organize, track, and make sense of the specific problems that people are having.

---

### Post by theosib on 2006-10-27
Ok, here's a dumb question:  Does anyone on this forum actually use software RAID?

I suppose it makes sense that Ubuntu developers would spend more time on more commonly-used features.  But in that case, it might be good to remove those features from the installer.  Ubuntu software RAID is broken, so it's unwise to mislead the user into thinking it's going to work and then having them disappointed later because it wasn't done correctly.

---

### Post by badboybrody on 2006-10-28
Well I am not sure if this is the right spot or not, but here goes. First I am fairly new to Ubuntu. I tried to upgrade to Ubuntu 6.10 and I had enough problems with that, but I think they were all my own doing. But I finally found a link that was supposed to be fairly automatic. It was just about done downloading when the whole system froze up solid. When I attempted to reboot apparently some of the 6.10 were installed and others weren't. The only two error messages I was able to catch said Hardware Drivers failed and Raid Arrays Failed. I can't get into Ubuntu at all, no safe mode or anything. I have no experience as to what commands I need to type. And so far I haven't been able to find the right help pages. Any suggestions? Because of right now the Ubuntu side of my computer is pretty much useless. Thanks for any help.

---

### Post by bay-bee on 2006-10-28
I use a LVM on my server with 3 disks @ 720GB and during my upgrade to edgy the machine totaly broke and wont boot anymore, me being in california and the machine in sweden doesnt help me troubleshooting it either :(.. GO EDGY

---

### Post by karaluh on 2006-10-31
I've got software raid on two scsi disk. Non raid ext3 partition for /boot, 5 partitions in raid 0. Eft and grub install fine. After reboot the only thing i've got is:

STARTING UP... 

Then, after about 1 min.

mdadm /dev/md0 has been started with 2 drives
mdadm /dev/md1 has been started with 2 drives
mdadm /dev/md2 has been started with 2 drives
mdadm /dev/md3 has been started with 2 drives
mdadm /dev/md4 has been started with 2 drives

---

### Post by wkulecz on 2006-10-31
I had a software raid only system working fine:

/ on /dev/md0 raid1 2 drives
swap on /dev/md1 raid1 2 drives
/home on /dev/md2 raid 1 2 drives.

I then added /data on /dev/md3 raid5 with three drives.

Everything seemed to work ok, but I was using picasa when picasa quit with an error dialog and basically locked up the X-server. I did a reboot from the gnome menu and it hung with "no init process" because the md drive assignments had changed!

Now I get:
mdadm /dev/md0 has been started with 3 drives
mdadm /dev/md1 has been started with 2 drives
mdadm /dev/md2 has been started with 2 drives
mdadm /dev/md3 has been started with 2 drives

meaning it made my newly added raid5 be md0 which kills bootup :(

Any suggestions on how to fix?  I tried to boot Knoppic but it wouldn't come up on this display,  I'll try again later when I have time to move in an older, 1024x768 display.

I suspect if I can edit grub's menu.1st and /etc/fstab I'll be OK, but what's to prevent it from changing again since I've no idea what went wrong!

--wally.

---

### Post by ZagiFlyer on 2006-11-09
I found this to be the opposite actually. 

I have three RAID devices:
/dev/md0 - RAID1 - /boot
/dev/md1 - RAID0 - /
/dev/md2 - RAID0 - /home

When I upgraded from Dapper to Edgy, it was seamless and perfect -- excellent work Ubunteros!

However, at a later date, I wanted to go from i386 to amd64 (too see if the 64-bit AMD dual-core would be any faster that way). I backed up my data and reinstalled using the alternate CD.

The installation had no trouble creating the RAID devices and installing to them and appeared to go perfectly. That is until I rebooted the system. When the system came up, grub errored out with "Error 15: File not found" (or some such. I know it was error 15). 

I compared the grub menu.lst and fstabs from the working Dapper installation and they were the same (except that Edgy had changed the swap partitions to this new format).

So, I had to REinstall Dapper (i386 again, since that's the CD I had) and then upgrade to Edgy. That went without a hitch.

---

### Post by wkulecz on 2006-11-09
As a followup, I removed power from the raid5 array and rebooted.  Everything was as before.  I edited /boot/grub/menu.lst to change the kernel option root=/dev/md0 to root=/md1 and edited /etc/fstab to reflect what the device assigments would be after booting with the raid5 array active.

Works fine for now.  It sure seems the /etc/mdadm/mdadm.conf file which is supposed to map arrays to md devices is ignored.

--wally.

---

### Post by GSMD on 2006-11-12
I do subscribe to the fact that software RAID (aka md) layer is broken & messed up in Edgy. I've actually faced this issue on both of the servers that have been upgraded to Edgy.
Here are the configurations and descriptions of what had happened.
1. A server with raid1 on 2 ide drives and raid5 on the other 5 ide drives was upgraded to Edgy via apt-get. It wouldn't boot and partition table on one of the drives of raid5 has been destroyed. Fresh install didn't help. Rolled back to Dapper with raid 5 reconstructed from scratch.
2. A server with 2 scsi drives in raid 1. After a fresh installation of Edgy this one was able to boot only once, completely going down on reboot. Rolled back to Dapper.

Conclusion: something is terribly wrong with md in Edgy and this is obvious in any install.

---

### Post by draconius on 2006-12-07
I just did a fresh install of xubuntu 6.10 on a machine that was previously running ubuntu 6.06.1.

The installation went great...until I installed mdadm...now my system will not boot.

I'm going to try messing around from the live-cd and see what I can break...

If I figure anything out, I'll post here.

---

### Post by draconius on 2006-12-07
Looks like I just had to wait for about 10 minutes for mdadm to automatically re-assemble the array.

Everything is working now, sorry for the false alarm.

---

