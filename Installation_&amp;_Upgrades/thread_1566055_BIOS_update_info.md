---
title: "BIOS update info"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by KWLLC on 2010-09-01
My head is still spinning from trying to track down this information!! What I want to know is where I can find out if an update of my Phoenix bios would get me past my problem.
I have an older p4 on a FIC motherboard. It support neither booting from my SATA drives nor from USB jump drives. Since I lost my job in '08, I can't afford to replace any hardware so I'm using 2 old IDE drives for my Ubuntu and XP distros. They are not only slow, but they are starting to show signs of old age. The SATA drive I have on board can't be used, though. If there isn't any good alternative, I was wondering if I could get advise on how to structure my HDs to best effect. Can I use the IDE drive as root (/) and insert the SATA drive into the filesystem as /home? Would it then concatenate them as one larger filesystem? My issue arose because the IDE drive I'm using filled up and all hell broke loose in trying to fix it. Anyone feel like helping a newbie out?

---

### Post by tommcd on 2010-09-01
You can choose manual partitioning when you install Ubuntu. You can then choose to use the IDE drive for the root and swap partitions. You can create a separate home partition on the sata drive that will be used for all your data and configuration files. 
Write back if you need more help.

Have you checked the motherboard manufacturer's website for a BIOS update that may allow booting from the sata drive?

---

### Post by Mark Phelps on 2010-09-02
I wish you luck, but it's unlikely that a P4-era mobo will have a BIOS that supports booting from USB.

Are you trying to boot from an internal SATA drive, or an external (eSATA) drive?  I'm surprised the former isn't supported; not surprised the latter isn't.

You could boot from the IDE drive and have the remainder of your filesystem on the SATA drive.  That's not using the IDE drive as root; it's using it as a boot drive.  You would only have the boot folder and other such stuff on it.

---

### Post by KWLLC on 2010-09-02
> **tommcd said:**
> You can choose manual partitioning when you install Ubuntu. You can then choose to use the IDE drive for the root and swap partitions. You can create a separate home partition on the sata drive that will be used for all your data and configuration files. 
Write back if you need more help.

Have you checked the motherboard manufacturer's website for a BIOS update that may allow booting from the sata drive?
I don't want you to think I didn't appreciate your reply to my post. Life is what happens after your plans are made and I was unavoidably restrained.
The mommyboard mfg doesn't even acknowledge that they made the board! I guess that means that it's too old to support. The internal SATA drive isn't supported.
My next question would be how to set up the IDE drive as a boot drive without making it the filesystem root. I can only figure out that solution if it involves formatting and loading the drives from the manual config panels during install. Is there some other utility that I could use to set the boot device, the root filesystem on a SATA and the /home filesystem on my other SATA drive?

Would I be able to do something like this?
SDA (IDE) drive gets GRUB2 (or should it be SDA1?)
SDB1 (SATA) drive gets / root
SDD1 (SATA) drive gets /home

SDC still has my XP SP3 layout on it so I want to leave it alone until I learn more about WINE use and config.

---

### Post by tommcd on 2010-09-02
Is this a computer you built yourself? Or was it a OEN manufacturer's computer? If you did not build the system yourself, perhaps the manufacturer has a BIOS update then.

Anyway, if you choose manual partitioning you can create a separate /boot partition on the IDE drive. Then put root, swap and home on the sata drive(s). Just be sure to install grub2 to the IDE drive. Set the IDE drive as the first boot hard drive in the BIOS. I assume that since you can't boot from the sata drives that the IDE drive is alrady set as the first boot drive.

---

