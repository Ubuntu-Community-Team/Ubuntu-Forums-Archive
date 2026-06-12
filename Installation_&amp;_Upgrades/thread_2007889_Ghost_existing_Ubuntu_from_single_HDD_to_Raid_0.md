---
title: "Ghost existing Ubuntu from single HDD to Raid 0"
date: 2012-06-21
forum: Installation &amp; Upgrades
---

### Post by BFG on 2012-06-21
I have a 11.04 setup I'm happy with.  I'm playing with the idea of moving the OS from a single boot HDD to a RAID 0 setup.  The hardware all check out and I'm thinking I can use clonezilla, acronis trueimage or norton ghost to build an image, swap out the hardware get RAID 0 set up and then put the ghost image back on.

Any experiences?  Straightforward or are there pitfalls?
Thanks.

---

### Post by darkod on 2012-06-21
Yeah, clonezilla should do it. Not sure if it carries over the UUID of the partitions too, so you might need to edit the /etc/fstab after the restore.
In any case you would need to install grub2 on the MBR again.

You can also look into FS Archiver for the backup/restore.

But I'm not sure this operation is worth while. The non-LTS desktop versions are supported only 18 months which means 11.04 will be out of support in October.

You might be better off starting to plan a migration to 12.04 LTS. Something like, backup all data and important config files, create the raid0 on the system, install clean 12.04 LTS. Copy back the data and config files where applicable.

The 12.04 LTS is supported 5yrs for the desktop system too, so once you tune it up, you can forget it for 5 yrs. You will want to change it before that probably anyway.

---

### Post by oldfred on 2012-06-21
While Wikipedia does not always have the best info it says this. RAID is not for backup and if you really want speed a SSD is usually a better choice.

[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)

---

### Post by ronparent on 2012-06-21
The system installed on a single boot HDD does not have dmraid installed and will not automatically run when migrated intact to a RAID. To run on the RAID you need to chroot install dmraid to it - then it should run fine.

I have done this a few time whens not otherwise able to install a distro directly to a RAID0 as recently with Mint 13 which is not currently installable directly to any fakeRAID. The same problem may exist with Ubuntu 12.04. Good luck.

---

### Post by BFG on 2012-06-25
Good info - Thanks.  I found info that clonezilla does support RAID but not RAID 0, because RAID 0 is software. Though Acronis does.

In my case my BIOS has firmware RAID 0 support so it might be OK, but if not - ronparent that's the sort of info I was after :)

Thanks oldfred, I've been using RAID 0 for a while, but never used cloning tools with it.  If I went to SSD it would be 2x SSDs in a RAID 0 ;)
I know RAID 0 is fragile, but there's nothing on the boot drive I can't live without as home directories autoFS from the server.

I have 2x 10,000rpm velociraptor drives, predicted increase in speed on RAID 0 is 30% and running virtual machines should give me a useable improvement.

---

