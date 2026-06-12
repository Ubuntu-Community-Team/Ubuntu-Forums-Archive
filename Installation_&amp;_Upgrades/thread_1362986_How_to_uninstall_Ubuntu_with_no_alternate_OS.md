---
title: "How to uninstall Ubuntu with no alternate OS"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by eveningsky339 on 2009-12-23
Hello everyone.  I have a bit of a dilemma.  I would like to remove Ubuntu temporarily for two reasons-- one, I've decided to dual-boot with XP, and two, I would prefer to switch from 64-bit to 32-bit.

I allowed Ubuntu to clear off my old Vista installation and have not lost one ounce of sleep over it, but this leaves me in a tight spot now that I want to remove Ubuntu and do an XP-first dual boot configuration.

I've done some searching, but I've yet to find a solid answer to this query.  Any help would be appreciated.  :)

---

### Post by taurus on 2009-12-23
Is XP already on the machine or are you planning to install XP now?

If you want to install XP, just do it since it would wipe out GRUB from MBR anyway.

---

### Post by raymondh on 2009-12-23
> **eveningsky339 said:**
> Hello everyone.  I have a bit of a dilemma.  I would like to remove Ubuntu temporarily for two reasons-- one, I've decided to dual-boot with XP, and two, I would prefer to switch from 64-bit to 32-bit.

I allowed Ubuntu to clear off my old Vista installation and have not lost one ounce of sleep over it, but this leaves me in a tight spot now that I want to remove Ubuntu and do an XP-first dual boot configuration.

I've done some searching, but I've yet to find a solid answer to this query.  Any help would be appreciated.  :)

Ready to install XP and you have the XP install disk?

-  Boot into the Ubuntu liveCD and in live session, access gparted.
-  Use gparted to delete Ubuntu and it's SWAP partitions (as well as any EXTENDED partition you might have.  You can use gparted to create a NTFS formatted PRIMARY partition (for your XP install).  *Leave space for Ubuntu and keep it unallocated for now unless you decide to go ahead an create your Ubuntu partitions and do a manual install.*  
-  Exit gparted and the liveCD.  Boot into your XP install disk.  Since you have created already a NTFS, Primary partition, select that partition and install XP unto it.
* The XP install will take time so have your favorite drink ready :)
-  When XP is installed, boot into it and make sure all is OK.
-  When ok, you can now boot into the Ubuntu LiveCD and install Ubuntu in the
* largest continuous free space (if you left the space unallocated) or;
* in the partitions you created beforehand ... if you did do so.

If you require a more detailed mini-guide, post a screenshot of gparted.  Also, tell us/me whether you want to create ubuntu partitions beforehand, it's preferred size/s,  separate /home from root, and whether you want Ubuntu to be primary or logical.  Also, ext3 or ext4 format.


Or, you can do what TAURUS says ... just install XP and then install Ubuntu :)

Regards,

---

