---
title: "Ntfs resizing error...why?"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Gargamella on 2007-04-23
I was trying to set a dual boot install with my school mate pc.
Its hd is 200GB and it is ntfs partitioned with windows installed...I tried to resize it with gparted tool but it gives us an error related to the fact (i think) it was not mounted...is it possible?

Then I saw it was unmounted (i am talking while we were in live cd) and I right-clicked and then mounted...but when I mounted the volume then I wasn't able to edit partitions (as the hd was locked) 


any ideas?

it seems to me too silly to not be able to install ;D

waiting for replies

---

### Post by Gargamella on 2007-04-23
the hd is a matrox one...

---

### Post by pepsi_max2k on 2007-04-23
locked or just listed as unformatted?

---

### Post by Gargamella on 2007-04-23
it was ntfs but with a locket next to it, and no actions available

---

### Post by Gargamella on 2007-04-24
bump

---

### Post by dcstar on 2007-04-24
> **Gargamella said:**
> I was trying to set a dual boot install with my school mate pc.
Its hd is 200GB and it is ntfs partitioned with windows installed...I tried to resize it with gparted tool but it gives us an error related to the fact (i think) it was not mounted...is it possible?

Then I saw it was unmounted (i am talking while we were in live cd) and I right-clicked and then mounted...but when I mounted the volume then I wasn't able to edit partitions (as the hd was locked) 


any ideas?

it seems to me too silly to not be able to install ;D

waiting for replies

You can only resize unmounted partitions, and for NTFS I would recommend a defrag before trying to resize.

---

### Post by Gargamella on 2007-04-24
yes I reccomended also by myself it to my friend but I also found this on the matrox site:

Use the NTFS file system
Your A/V drives must be formatted using NTFS for use with Matrox RT.X100 Xtreme Pro because NTFS overcomes FAT32 file size limitations. When a hard drive is formatted using FAT32, files saved to this drive cannot exceed 4 gigabytes in size. This translates to approximately 20 minutes of DV video, which poses a serious limitation to a nonlinear editing platform like your Matrox RT.X100 Xtreme Pro system.

I hope this is not for all their hds anyway will try again

---

### Post by pxwpxw on 2007-04-24
Have you checked bios settings for anti-virus or other protection which might be locking the boot sector?

---

### Post by Gargamella on 2007-04-26
> **pxwpxw said:**
> Have you checked bios settings for anti-virus or other protection which might be locking the boot sector?

yes, and that solved everything...my friend had installed norton goback on windows...that was the problem

thank you

---

