---
title: "Adding a FAT 32 Partition to My Dual Boot System Win10 / 14.04.3"
date: 2015-10-23
forum: Installation &amp; Upgrades
---

### Post by coljohnhannibalsmith on 2015-10-23
Hello,

I've recently become informed that the conventional wisdom, when it comes to transferring files between NTFS and EXT4, is to set up a third partition that both OSs can push and pull files to/from. I've already set up up my dual boot system with NTFS and EXT4 partitions. What I'm considering doing is decreasing the size of the EXT4 partition by about 10GB; and then reformatting this space as FAT32. Both Ubuntu and Windows will be able to read/write to this partition. Trouble arose when I tried to use GParted to shrink the EXT4 partition. I was warned that changing the partition size may render the EXT4 partition unbootable. The operating word here is "may" not "will;" so I'm not sure what to do at this point. I have to assume that shrinking the front portion of the EXT4 partition, where the boot info must be, will be the most dangerous and should be avoided. But, what about the rear portion? Can I take space from this area with little risk, or will it be just as dangerous? I do have a fully cloned and operational backup in case of a catastrophic failure as previously described; but can someone give me an opinion apriori of whether this will work or not?

Thanks Hannibal

---

### Post by sudodus on 2015-10-23
Editing partitions is always risky. What you intend to do *should* work, and with a *backup* of 'everything', it should be OK to continue.

---

### Post by oldfred on 2015-10-23
The suggestion for a shared partition is NTFS, not FAT32.

FAT32 is ok for small partitions, like the ESP or flash drives. 
But it has no journal. So chkdsk can take longer and may not work. 
And it cannot store files over 4GB. I was originally backing up my system to a FAT32 partition and wondered why the image was always 4GB even though I was backing up more data?

---

### Post by ubfan1 on 2015-10-23
You can take the "thrill" out of reducing partition size by shrinking the filesystem on it first with resize2fs.  Of course, you can cross your fingers, and do resize2fs after the partition shrink, and let it automatically fit itself to the new partition without having to give it a size.  All "backup first" advice still applies of course.

---

