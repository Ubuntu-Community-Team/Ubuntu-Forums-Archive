---
title: "Dual boot xp and karmic with 2 drives"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by danwooden on 2009-11-20
Recently installed Ubuntu on a 150 of a 500 Win XP NTFS partition.  Ubuntu is now A1 and xp A2.  So I am really hating XP now and want to transition further away, but I probably will need to keep it around...

I go buy a new 1 TB harddrive.

My question: what is the best way to set up a dual boot with 2 hd's XP and Karmic?

I was thinking 1 drive (500) XP NTFS and 1 drive (1TB) Ubuntu (Ext3 or Ext4)
BUT my grub already lists about 6 choices and not sure how to do this... (ideas?)

Advantages of one OS on each drive?  One goes down the other lives on.  
I have about 300 GB of data right now.

Q = SHould I do both OS's on the 500 and data on 1 TB or split and keep XP on 500 and Ubuntu (split out) on 1 TB? 

Curious about advantages / disadvantages of both scenarios.  Right now I am just keeping the 500 split and 1TB will be NTFS data but I want max performance and security.  Have contemplated ghost backups to a partition on 1TB.  Any advice?  THANKS!

---

### Post by Mark Phelps on 2009-11-20
Everyone's response is going to be different but ...

Since you're wanting to move away from XP, there's really no value in retaining NTFS for a shared/data partition.

I would leave the 500 the way it is for now and use the 1TB just for data -- but reformat it as Ext3 or Ext4 for maximum use by Linux.

Later, when you finally decide to rid yourself of XP, I would remove the XP partition and expand the Ubuntu partition into that space.

But, as I said, everyone's response is going to be different ...

---

### Post by danwooden on 2009-11-20
Thanks Mark.  Is Ext3 or Ext4 going to be faster or more efficient for data storage? If I do that then I will have to install (its F-something) in XP to read my data from that side right?

I know this isnt much of a real 'problem' but I just really want to optimize my performance and security (peace of mind).  Any other input would be appreciated even if its splitting hairs or just opinion!

---

