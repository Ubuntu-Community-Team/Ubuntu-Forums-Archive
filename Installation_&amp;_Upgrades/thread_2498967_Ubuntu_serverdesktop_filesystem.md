---
title: "Ubuntu server/desktop filesystem"
date: 2024-07-05
forum: Installation &amp; Upgrades
---

### Post by graaulv on 2024-07-05
I am currently playing with installing ubuntu desktop 22.04.2 on a spare machine I have after I went M.2 on my Unraid server

It is right now giving me the choice of the filesystem I have on the m.2 drive, LVM or ZFS
which one do I choose for ease of putting new/bigger disks in the server ?

I am debating with my self if I should run the desktop version of Ubuntu, or the dedicated server version
It will purely be a backup server

Hardware:
Asus Rog Strix B550 Gaming (2.5 gb netcard)
AMD Ryzen 5 5600G
Corsair Vengeance LPX 3200 32 Gb (2x16 Gb)
Samsung 960 Evo 250 Gb

Delock 89384 10 port Sata controller
Seagate Barracuda 2Tb x 5
Seagate Barracuda 4Tb x 4
Seagate Barracuda 8Tb x 1

Seagate Constallation ES.2 3Tb x 8 (6Gb SAS)
Inspur SAS controller

Corsair RM1000 PSU

Alternative / extra hardware if nessecerry
Gainward GTX970 GPU
Corsair Vengeance LPX 3200 32 Gb (2x16 Gb)

---

### Post by TheFu on 2024-07-05
> **graaulv said:**
> I am currently playing with installing ubuntu desktop 22.04.2 on a spare machine I have after I went M.2 on my Unraid server

It is right now giving me the choice of the filesystem I have on the m.2 drive, LVM or ZFS
which one do I choose for ease of putting new/bigger disks in the server ?

LVM isn't a file system. It is a Logical Volume Manager.  ZFS is both a Logical Volume Manager AND a file system.  For disk storage today, I don't think either choice jumps out as "better", though if you don't already know LVM, then skipping over that and going directly to ZFS could save some effort.  Just beware that ZFS has specific disk layouts that it prefers and most ZFS purists would strongly suggest using it only with ECC RAM (which most desktops do not support).


> **graaulv said:**
> 
I am debating with my self if I should run the desktop version of Ubuntu, or the dedicated server version
It will purely be a backup server

Hardware: ...


Either the desktop or the server version are fine.  Both can run all the programs from the other release.  If you need a GUI, then you want a desktop release.  Ubuntu Server doesn't come with any GUI and if a GUI is added, the commonly expected integrations to the GUI don't happen. So you shouldn't expect to manage networking using a GUI tool. There isn't one.  OTOH, server networking is a setup once thing and forget it for years, so it is unlikely you'll need to screw with it post install.

I would caution you  .... LVM isn't included in Ubuntu Desktop 24.04.  The new installer doesn't have the back end stuff to deal with LVM.  22.04 and earlier desktops all supported LVM, so it is purely a Canonical decided to have a new installer, but didn't get the core functions working.  I will not install 24.04 desktop version until LVM is supported.

ZFS on the boot disk seems to still be experimental to me.  I've been running it on a desktop for about 18 months now, but it has very limited storage and I haven't done much with it.  If I were setting up a new system today to be a backup server, I'd use LVM+ext4 for the OS stuff and for HOME directories, but I'd make all other storage (effectively data storage) ZFS.  The ZFS learning curve is steep, so be prepared.  BTW, ZFS has some great backup capabilities, but only between 2 systems both running ZFS.   Sanoid is one of the tools to make ZFS snapstop transmission to another ZFS system for backups: [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid).  Of course, you can do it all manually too.

As for upgrading an OS with ZFS to the next release, I don't know how easy or hard that might be.  I suspect you'll want to research that.   I've been using LVM for nearly 25 yrs now and upgrades were all seamless ... er ... until 24.04.  I can't imagine that data storage managed with LVM would have issues due to an OS upgrade, but I tend to do fresh OS installs with each migration to a new LTS release.  

Sorry for rambling.  Hope my perspective is useful and I really hope that people with more experience using ZFS will correct anything I wrote that is wrong and add their own information.

---

### Post by #&amp;thj^% on 2024-07-05
> **TheFu said:**
> LVM isn't a file system. It is a Logical Volume Manager.  ZFS is both a Logical Volume Manager AND a file system.  For disk storage today, I don't think either choice jumps out as "better", though if you don't already know LVM, then skipping over that and going directly to ZFS could save some effort.  Just beware that ZFS has specific disk layouts that it prefers and most ZFS purists would strongly suggest using it only with ECC RAM (which most desktops do not support).




Either the desktop or the server version are fine.  Both can run all the programs from the other release.  If you need a GUI, then you want a desktop release.  Ubuntu Server doesn't come with any GUI and if a GUI is added, the commonly expected integrations to the GUI don't happen. So you shouldn't expect to manage networking using a GUI tool. There isn't one.  OTOH, server networking is a setup once thing and forget it for years, so it is unlikely you'll need to screw with it post install.

I would caution you  .... LVM isn't included in Ubuntu Desktop 24.04.  The new installer doesn't have the back end stuff to deal with LVM.  22.04 and earlier desktops all supported LVM, so it is purely a Canonical decided to have a new installer, but didn't get the core functions working.  I will not install 24.04 desktop version until LVM is supported.

ZFS on the boot disk seems to still be experimental to me.  I've been running it on a desktop for about 18 months now, but it has very limited storage and I haven't done much with it.  If I were setting up a new system today to be a backup server, I'd use LVM+ext4 for the OS stuff and for HOME directories, but I'd make all other storage (effectively data storage) ZFS.  The ZFS learning curve is steep, so be prepared.  BTW, ZFS has some great backup capabilities, but only between 2 systems both running ZFS.   Sanoid is one of the tools to make ZFS snapstop transmission to another ZFS system for backups: [https://github.com/jimsalterjrs/sanoid](https://github.com/jimsalterjrs/sanoid).  Of course, you can do it all manually too.

As for upgrading an OS with ZFS to the next release, I don't know how easy or hard that might be.  I suspect you'll want to research that.   I've been using LVM for nearly 25 yrs now and upgrades were all seamless ... er ... until 24.04.  I can't imagine that data storage managed with LVM would have issues due to an OS upgrade, but I tend to do fresh OS installs with each migration to a new LTS release.  

Sorry for rambling.  Hope my perspective is useful and I really hope that people with more experience using ZFS will correct anything I wrote that is wrong and add their own information.
+1 to all the above,
We have not so long ago where zfs was less than trustworthy, manual snapshots on your bpool would break the system and that currently has been addressed now, but once bitten trust becomes shaky/ experimental .   

As far as upgrading to the next LTS is pretty much the same as any other system works

---

### Post by graaulv on 2024-07-05
You actually made sense in a non-sense way.

Ubunto 22.04.2 desktop version gave me a choice of [COLOR=#000000]LVM+ext4 or ZFS, 
If I understand it right (which is not nesseserry true) then ZFS HAVE to have all disks in a volume ? pool ? to be the same size, 
I am used to Winslow and Unraid where it doesn't matter how big the disks are (except unraid need the parity disk to be at least as big as the biggest data disk)

If there are no difference between desktop and server version (other than the GUI and maybe a small amount of resource use in use) I will use the desktop version, it is easier for me now after not have used CLI since MS-Dos 3.2[/COLOR]

---

### Post by graaulv on 2024-07-05
I need to see if I get you right.
LVM are easily upgradable, i.e. disconnect all the datadrives, upgrade to the next version, reconnect the data drives or ???

---

### Post by TheFu on 2024-07-05
> **graaulv said:**
> I need to see if I get you right.
LVM are easily upgradable, i.e. disconnect all the datadrives, upgrade to the next version, reconnect the data drives or ???

You need to have backups before any OS upgrade.  I don't bother physically disconnecting LVM storage during upgrades, but I'm not confused by which disks hold what ... well, any more than anyone else with 10 HDDs connected to a computer might be confused.

There are some things that I do with LVM to prevent hassles when a drive dies.  As you can imagine, of the decades, I've had my share of HDD failures.  Sometimes a single drive failure made me lose everything else in that same LVM LV because I was striping all the data across multiple disks and didn't have backup religion.  That taught me some things and I've never spanned a single LV across multiple disks unless it was for a RAID1 or RAID10 setup.  I also have backup religion and never allow any LV to be larger than I can fit onto a single backup volume.  This has made me effectively standardize on 4TB volumes, regardless of the actual underlying disk size.

For the ZFS questions, someone else is better able to make up answers than I can. ;)

---

### Post by graaulv on 2024-07-05
Real men never makes backup, real men cry a lot :(
I learned that 1 week before I bought my tape backup way back in the 386/387 days :lolflag:

So raid 1 or 10 (mirror/strip+mirror) each volume then ? sounds like a good idea, and I have the disks to do that (18 in all) ;)

---

### Post by TheFu on 2024-07-05
Is there a reason you need to merge all the disks into a single file system?  For most home users, that would be for media and all current media servers will happily merge many disks into a single view for the different types of media.

I really think you should do some more research on ZFS.  Again, if I didn't have 20+ yrs of LVM experience, I'd skip it completely and use ZFS today, even with the learning curve it needs.

---

