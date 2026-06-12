---
title: "Mis-match between Gparted display and mounted partition"
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by Richard_Brockie on 2013-08-28
Hi,

I have inherited an production system that was running (9.10). I have backed up and rolled forward to 12.04.3 LTS.

I've run into a Gparted warning for an ext4 partition on one of the HDDs - the information on the partition has the following:

e2label: No such file of directory while trying to open /dev/sdc1
Couldn't find valid filesystem superblock. [plus further dumpe2fs lines]

This partition was created with karmic (9.10) at the very latest and the fstab mounts /dev/sdc as /data.

Gparted does not see the /dev/sdc partition, it only finds /dev/dsc1 as the partition on device /dev/sdc. Is there any way to cleanly make Gparted happy with the existing partition?

Thanks,
R.

---

### Post by oldfred on 2013-08-28
The sdc is the entire drive not a partition.

Does gparted show a red or yellow warning icon on the sdc1 partition. And right click does it give any more info?

Often mounting issues may need a fsck.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdc1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdc1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdc1

---

### Post by Richard_Brockie on 2013-08-28
Hi,

Thanks for the reply.

I'm aware that /dev/sdc is the drive and /dev/sdc is the partition. What is confusing me is that it is /dev/sdc that is mounted as /data in the system. Here is the appropriate line in fstab:

```
/dev/sdc        /data           auto  
```

Here is what gparted shows:

[IMG]http://i538.photobucket.com/albums/ff342/richard_brockie/gyre/Screenshotfrom2013-08-28141504.png[/IMG]

Here is the right-click info:

[IMG]http://i538.photobucket.com/albums/ff342/richard_brockie/gyre/Screenshotfrom2013-08-28141936.png[/IMG]


e2fsprogs 1.42-1ubuntu2 is installed on the system. /dev/sdc is a h/w RAID volume on an LSI controller, hence the large size.

Assuming the file system checks you suggest fix the problem, will I need to alter the fstab entry?

Thanks,
R.

---

### Post by oldfred on 2013-08-28
I do not know servers nor RAID. But fstab entries all use UUIDs now to avoid issues of mounting by device. Devices change if drive order comes up differently or flash drives may change, etc.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Because of the errors your blkid did not show the UUID, but normally it should.


 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by Richard_Brockie on 2013-08-28
Thank you very much for the pointers. I have some further reading to do.

---

