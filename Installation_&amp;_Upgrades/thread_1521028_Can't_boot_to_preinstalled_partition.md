---
title: "Can't boot to preinstalled partition"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by roof_top_eagle on 2010-06-30
Okay here's my conundrum.

I just got a new Toshiba Satellite 64bit laptop with 4bg of ram and a 640gb hard drive, I want to dual boot windows 7 and Ubuntu 10.04 Lucid Links and I had the guys at Best Buy make me a partition so that if something went wrong with the partition it would possibly be on them.  the issue I'm running into is that I can't seem to figure out how to boot to the "S" partition on my hard drive when installing Lucid Links via a USB key. 

Any help?

---

### Post by darkod on 2010-06-30
You want to boot from usb stick and install onto existing partition?

---

### Post by roof_top_eagle on 2010-06-30
That's right :-)

---

### Post by darkod on 2010-06-30
If they created the partition as ntfs it's worthless for linux. Also, ubuntu by default takes two partitions, root and swap, so only one won't cut it.
Boot with the usb stick but don't start the installer, boot into Try Ubuntu live mode. Open Gparted in System-Administration and take a look at the partitions/disk.

If the partition where you want to install is ntfs, delete it. BE CAREFUL to delete the correct one. Hit the green button to apply the changes. Leave the space as unallocated.

Then start the installer (you can simply click the Install icon on the live desktop) and use the Use Largest Available Free space option. That will install it into the unallocated space you left using the standard root+swap setup.

---

### Post by roof_top_eagle on 2010-06-30
Okay I feel dumb, It's Ubuntu Lucid Lynx 10.04 LOL not Lucid Links BAHAHA I crack myself up...

---

### Post by roof_top_eagle on 2010-06-30
> **darkod said:**
> If they created the partition as ntfs it's worthless for linux. Also, ubuntu by default takes two partitions, root and swap, so only one won't cut it.
Boot with the usb stick but don't start the installer, boot into Try Ubuntu live mode. Open Gparted in System-Administration and take a look at the partitions/disk.

If the partition where you want to install is ntfs, delete it. BE CAREFUL to delete the correct one. Hit the green button to apply the changes. Leave the space as unallocated.

Then start the installer (you can simply click the Install icon on the live desktop) and use the Use Largest Available Free space option. That will install it into the unallocated space you left using the standard root+swap setup.

Thanks Darko!!!

---

