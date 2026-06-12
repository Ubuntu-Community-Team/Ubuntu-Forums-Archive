---
title: "Yet another noob partitioning problem"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by corblimey on 2008-06-25
I was just installing v8.04 and am confused by the partitioning. I understand the concept and all that, but the LiveCD partitioner gives me the following:
```
/dev/sda
  /dev/sda1  fat32  7845MB
  /dev/sda2  ntfs   242562MB
  free space        7MB

/dev/sdb
  /dev/sdb1  fat32  41159MB

```Now I have a 300gig h/d which was partitioned when I bought it. C is where I do my work and D is a restore drive or something - to be honest, I've never paid it much attention. So that explains the /dev/sda and dev/sdb but the contents of dev/sda confuses me. What is the 7gig FAT32 partition? What is 'free space'?

I assume I need to create a new partition for my installation, but I'm only allowed to edit the /sda2 partition and add a new one on the 'free space', with a max of 7MB, which is obviously no good. Can I delete the 'free space' partition, and this will open up /sda2 to be added to?

(Note: I use Win XP and want to create a dual boot loader, so I'm planning on leaving 30gig for Win XP, using 120 FAT32 for shared files and the rest is Ext3 for Ubuntu, so my first step will be to create I guess about 190g partition hanging of /sda2)

---

### Post by Pumalite on 2008-06-25
If you have a Live Ubuntu CD; post a screenshot of your partitions with the Partition Editor. sda1 is probably your 'recovery partition'. In the meantime, here is a link for dual boot an another for partitioning:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by corblimey on 2008-06-25
Actually that makes more sense, the 7gig is my restore partition (D) and sdb is an external h/d I have connected to my PC.  Okay, but I still need to be able to add a new partition to sda1 and I can't do that while 'free space' is there.  Win XP is reporting that I have 210gig free space.

ETA: Thanks for the links, I had previously found them through Google and was following the howtoforge one, but their gParted screenshots are different to mine.  I can't get a screenshot because it's a different machine from the one I'm posting on, but the code section above is an exact facsimile.

---

### Post by Pumalite on 2008-06-25
Are you using Vista or XP?

---

### Post by corblimey on 2008-06-25
XP (SP2 if that makes any diff).

I'm guessing that my problem is that XP is reporting 210gig free but gParted is only 'seeing' 7MB of it?

---

### Post by Pumalite on 2008-06-25
Use Gparted Live CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.
Shrink XP. Right click on the partition, then choose 'resize' from the menu. Shrink it to the left and let it merge with the rest of the free space.

---

### Post by corblimey on 2008-06-26
I couldn't get gParted LiveCD to work, it would perpetually hang on  the keymap selection part.  I tried a couple of different versions with different boot options from GRUB to no avail.  I found out that gParted is available on the LiveCD I'd already got working for Ubuntu 8.04, so I went ahead and started using that.  

My problem now is that I can't shrink the sda2 partition.  I can increase it to take in the 7MB 'free space' (showing as unallocated), but not decrease it (I've tried both using the slider and just typing in a new number below - the slider is locked and when I tab out of the field, it reverts to the old number)

I see that sda2 has an exclamation mark against it - I've googled it but there doesn't seem to be solid reason for this.

ETA: Okay, I followed the instructions in gParted about chkdsk (duh!) and this is now fixed.  Resizing appears to have worked.  So I'm just testing Win XP now and will try the install again last today.

---

### Post by corblimey on 2008-06-26
All sorted, cheers

---

### Post by Pumalite on 2008-06-26
Good luck.

---

