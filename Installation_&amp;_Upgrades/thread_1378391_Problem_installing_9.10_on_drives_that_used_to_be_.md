---
title: "Problem installing 9.10 on drives that used to be in RAID"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by nick_mckay on 2010-01-11
Hi all,

I hope the solution to this isn't posted elsewhere, but I've spent a lot of time looking, and it's the first time I haven't found a solution in the forums, or elsewhere.

I was recently given two hard drives that were used as a raid (maybe fakeraid) pair in a windows XP system. My plan was to split them up and install one as a second HD in my desktop, and load 9.10 x64 on it, and use the other for mythbuntu 9.10.

As has been noted elsewhere, the drives aren't recognized by the 9.10 installer, but removing dmraid gets around this, and installation of both ubuntu and mythbuntu went fine.

On both systems after installation however, the systems broke during update, giving an "read-only file system" error and no longer booting.

Running fsck from the live cd gives the error:

fsck: fsck.isw_raid_member: not found
fsck: Error 2 while executing fsck.isw_raid_member for /dev/sdb

and running fsck from 9.04 installed on the other hard drive gives an error like:

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

In both cases I setup the drives with the ext4 filesystem.

There's probably more that I'm forgetting... it seems likely to me that this problem is due to some lingering issue with the RAID setup they were in. I doubt its a hardware issue since I get the same problem with the different drives in different boxes.

Any clues?

Thanks,

---

### Post by darkod on 2010-01-11
I guess you already did this, but first make sure you have no raid settings enabled in your BIOS yourself. Having a setting enabled will put raid info on the drives again even without literary creating a raid array.
The fsck error sounds like it's expecting the drives to be raid members when it shouldn't. You can also try running the remove dmraid command again, it won't destroy data on existing install. Just to make sure to get rid of the settings.

Also you can try running sudo blkid because I think besides the UUID it also shows whether the raid settings are present or not.

All of the above is while booted with the live cd, Try Ubuntu since you can't boot the system it seems.

---

### Post by nick_mckay on 2010-01-11
Yeah the bios is fine, no RAID setup in there. I got fsck to run - on this box I installed 9.10 on a partition, so removing dmraid and running

sudo fsck /dev/sdb3

did the trick, it found errors and fixed them, but the system still wont boot - no errors this time though. It gets through the file check then hangs.

Similar thing happened on the mythbuntu box. It seems like the systems are thinking that drives are still in RAID somehow, and errors develop once the system starts writing, although none during installation.

I didn't remove dmraid after the install... could that be the problem? I could try a fresh install and then immediately remove dmraid before doing anything else.

---

### Post by darkod on 2010-01-11
Usually removing dmraid before install is enough. But if there were still remains of raid settings I wonder if grub2 is installed correctly. Maybe that's why it doesn't boot.
You could try the procedure to reinstall grub2 with the live cd.
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by nick_mckay on 2010-01-11
I don't think its a grub2 problem, as grub2 works great after the install. Everything works fine (well, I havent really tried much since I update pretty quickly, but I was able to boot in several times and use installed software fine) until I try an update.

The update downloads all it needs to, and then starts unpacking packages. It gets through a bunch and then gives an error in dpkg, that the file system is read-only.

I don't think that its the same pkg causing the problem each time, but I'll note it this time. Regardless, after that, fsck finds errors that mention RAID issues, and the system won't boot.

---

### Post by presence1960 on 2010-01-11
Also there is a bug in 9.10 that mounts raid arrays that you have deleted.  To fix it first turn off raid in your bios.  Then load up the 9.10 live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/sdX
```  Note you want the disk name not the partition name.  You can see your disk names in gparted. Example:```
 dmraid -E -r /dev/sda
```

If you have more than one disk showing as RAID then repeat the above with the proper disk designation for all RAID disks.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Once you have verified the raid disk(s) is gone reboot and your OS should boot.

---

