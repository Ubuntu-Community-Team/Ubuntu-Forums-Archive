---
title: "Complete crash and lost (I think) my RAID1 config HHEELLPP"
date: 2011-05-21
forum: Installation &amp; Upgrades
---

### Post by lhuggybear on 2011-05-21
I have been running dual boots for a long time and never had a problem installing Ubuntu.

I now tried to install Ubuntu Studio on my performance machine, a DELL Studio XPS, which has (had?) a RAID1 configaration.

I got stuck in the partitioning and tried to abandon, which left me with maybe nothing... When I tried to reboot, my machine started Windows but then "autochk program not found". And I am lost for what to do... Anyone so kind to give me hints? I am no expert...

---

### Post by tgalati4 on 2011-05-21
It's not clear from your post:  Was Windows running the RAID1 configuration?  If so, then I believe that is a non-starter.  You need a clean partition to install Ubuntu to.  It can be installed onto a RAID1, but that is not really recommended because it makes recovery and booting difficult when the RAID fails--(as you have found).

For recovery, you need to boot with a Windows disk and run fixmbr to repair the master boot record.  This should fix the windows booting portion.  If you don't have a Windows disk, then burn yourself an Ultimate Boot CD.

---

### Post by lhuggybear on 2011-05-21
Can I use an old XP SP1 disk on my Vista 64 system to do the fixmbr?

---

### Post by tgalati4 on 2011-05-21
Wow, if your PM is correct, then Dell is shipping machines with Windows installed on BIOS-controlled RAID?  That would make dual-boot difficult and a clever way to lock in your OS.  Perhaps it's just the performance XPS machines that are set up that way.

No, I don't believe a WinXP disk can fix a 64-bit Vista installation.  WinXP is solidly 32-bit.  You can try it, but it might just make the situation worse.  If you say the RAID1 is configured in BIOS, then there must be (or should be) an option to "integrity check the RAID" and "repair the RAID".

You need to search for some tutorials to repair Vista.  My Windows learning stopped at Windows XP (or was it 3.11?).  I haven't used it in years.

If you want to dual boot, put in a new (2nd) hard drive and partition it with the Ubuntu LiveCD using gparted.  That's the cleanest way to handle your situation.

If gparted rewrote the partition table on a BIOS-controlled Windows RAID1, then recovery will not be easy.

---

