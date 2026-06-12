---
title: "Install on Raid, Sata, NTFS, Windows..etc"
date: 2008-01-14
forum: Installation &amp; Upgrades
---

### Post by banshee28 on 2008-01-14
Ok, well about had enough of Windows :lolflag:

After a simple windows update, my pc will boot and instantly go to a BSOD. No safe mode or lkg works! A windows PE or Knoppix cd works fine, so I dont think its hw. 

Anyway my setup is a Sata raid 0 array formatted ntfs. When trying to install ubunto 7.10, it sees some partitions but it looks like it sees the 2 individual drives separately not as a raid array. The array is configured through the on board MB settings.  

I am not too concerned about booting into Windows if I cant get it back, but I DO want to get my data off from there and onto a external drive for backup.

How can I format\install without loosing ANY data on either HD that ubunto sees? I also have a 3rd non raid NTFS partition that I can install to, but I dont want ubunto to "format the drive" and I loose everything!

Did not find too much searching based on my situation? ..Thanks

---

### Post by Pumalite on 2008-01-14
Check FakeRaid How-To in Google.

---

### Post by banshee28 on 2008-01-14
> **Pumalite said:**
> Check FakeRaid How-To in Google.

Good info, reading it now. 

** After doing some reading, it looks like this is part of my problem. However with the formatting required by the install, will this truly "format" the drive or will I loose any data. Once I can get all my data off, I will be glad to format the entire 2 drives and start fresh!

---

### Post by Pumalite on 2008-01-14
Unless you install Ubuntu IN the RAID, you'll have problems installing Grub TO the Raid.

---

### Post by banshee28 on 2008-01-14
Thanks for your suggestions on FakeRaid How-To.. I am now able to mount my ntfs partitions, but not 100%: I have 3 HD's. 2 using Raid 0 and one no raid. I can see the no raid drive fine..... 

And ONE of the raid partitions (2nd partition on array) is now working fine also, but I CANT seem to get the first partition (C Drive) to show up!! When I tried to reinstall windows with my nlited cd with the raid drivers built it, it seemed to also show the same 2nd partition but not the "C Drive" ...

If the raid array or any drive was "bad" I would not be able to see Any data or partitions, right?

---

