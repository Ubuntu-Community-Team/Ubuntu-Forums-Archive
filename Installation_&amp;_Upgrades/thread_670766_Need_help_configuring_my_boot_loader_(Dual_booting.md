---
title: "Need help configuring my boot loader (Dual booting XP and Ubuntu)..."
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by nrajlich on 2008-01-17
Well I'm trying to dual boot Ubuntu 7.10 and Windows XP. I'll try to make a diagram of my current partition table below:

/dev/hda1 - ntfs - 100gb (this is the windows install partition)
/dev/hda2 - ext3 - 50gb (the ubuntu partition)
/dev/hda3 - extended - 2gb
---> /dev/hda5 - linux swap - 2gb

windows and linux are both installed to their respecting partitions. GRUB is currently installed to the MBR, however whenever you try to boot normally, it spits out Error 18.

Error 18 has to do with the linux boot partition being outside of the first ~8.5 gb of the disc, and therefore can't be booted.

My problem is fixing the boot loader to work correctly again. I'd rather not have to format my HDD again and reload XP and Ubuntu, and I don't want to move the XP from the beginning of the disc, because then it would not be drive C: when I reloaded it.

I just need to know the best way to somehow fix GRUB, or load LILO or make NTLDR (the windows boot loader) do the dual booting. What would be the best way to do this? Thanks in advance!!

---

### Post by logos34 on 2008-01-18
try [wingrub]("http://users.bigpond.net.au/hermanzone/p9.html")

---

### Post by sandysandy on 2008-01-18
> **nrajlich said:**
> Well I'm trying to dual boot Ubuntu 7.10 and Windows XP. I'll try to make a diagram of my current partition table below:

/dev/hda1 - ntfs - 100gb (this is the windows install partition)
/dev/hda2 - ext3 - 50gb (the ubuntu partition)
/dev/hda3 - extended - 2gb
---> /dev/hda5 - linux swap - 2gb

windows and linux are both installed to their respecting partitions. GRUB is currently installed to the MBR, however whenever you try to boot normally, it spits out Error 18.

Error 18 has to do with the linux boot partition being outside of the first ~8.5 gb of the disc, and therefore can't be booted.

My problem is fixing the boot loader to work correctly again. I'd rather not have to format my HDD again and reload XP and Ubuntu, and I don't want to move the XP from the beginning of the disc, because then it would not be drive C: when I reloaded it.

I just need to know the best way to somehow fix GRUB, or load LILO or make NTLDR (the windows boot loader) do the dual booting. What would be the best way to do this? Thanks in advance!!

have u tried booting ubuntu using super grub disk. 

regards

---

