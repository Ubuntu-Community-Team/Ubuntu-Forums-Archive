---
title: "Wipe Hard Drive and Clean Install dual-boot Karmic/XP"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by noob555 on 2010-02-02
I recently ran a diagnostic on my Hitachi manufactured hard drive and it recommended running a utility that will wipe the drive clean.  This is due to the number of bad sectors.  Basically, it will reset every point on the hard drive to zero.

I love Ubunutu, but have to run a dual-boot system with XP for various reasons.

My general questions are as follows:

[LIST]
[*]What is the best way to reinstall a dual-boot Karmic/XP system totally from scratch?

[*]Do I start with the Windows install CD or the Karmic CD?

[*]Is there a general guide for this anywhere?

[*]Is there anything I should be particularly worried about?
[/LIST]

Thanks for all help received in advance.  You guys (and girls) are the best!

---

### Post by darkod on 2010-02-02
After the wipe you will have all space as unallocated. For XP you might start with the XP disc and create one ntfs partition as big as you plan, and install it. Then from within XP you could also create another ntfs partition if you plan to hold data on it so both XP and ubuntu can access it. I usually try to avoid accessing the windows system partition from ubuntu regularly, so I prefer another ntfs partition to share.
After this, you still have the part of the hdd unallocated so you can either tell ubuntu to use Largest Available Free space option, or create partitions manually if that's what you want.

For win7 for example, this differs a bit because if you start with win7 dvd and let the installer start creating a partition on an unallocated disk, it will create the small 100MB boot partition which is using up one primary partition and if you have single hdd you might not want to waste it. For win7 I prefer to create one ntfs partition first with Gparted from the ubuntu live desktop, and then win7 installer just installs on it.

---

### Post by noob555 on 2010-02-02
Thank You!

If I understand your post correctly, you recommend starting with the Win XP install and creating partitions for Win XP only.  Then go to Ubuntu live cd and install ubuntu in the unallocated space.

Regarding the shared ntfs partition that you mentioned, I seem to recall reading that Ubuntu could not write onto ntfs, so shared drives should be formatted fat32.  Is that wrong?

---

### Post by darkod on 2010-02-02
> **noob555 said:**
> Thank You!

If I understand your post correctly, you recommend starting with the Win XP install and creating partitions for Win XP only.  Then go to Ubuntu live cd and install ubuntu in the unallocated space.

Regarding the shared ntfs partition that you mentioned, I seem to recall reading that Ubuntu could not write onto ntfs, so shared drives should be formatted fat32.  Is that wrong?

Yes, start with XP disc and create just the system partition first, and install XP. Then boot it and if you're planning a shared ntfs partition, create it as second partition from within XP (you can do it later from ubuntu but it's the same). But do not let that partition take up the rest of the hdd, not entirely. After that you should still have some unallocated space for ubuntu, and you can install into it.
It was long time ago that linux had issues writing on ntfs. As far as I know, it's ok now to create a shared partition as ntfs. And it has benefits over fat32 so I would use ntfs.

---

### Post by noob555 on 2010-02-02
Many thanks Darko!

Your advice has been very useful.  It's something of a big project (among other things I have to create my own Win XP boot disk because I lost the old one) so I'm going to move on it this weekend.  


p.s.  Stay away from time travel.  It's just dangerous.

---

