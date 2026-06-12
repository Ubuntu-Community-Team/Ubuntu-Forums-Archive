---
title: "XP/ubuntu dual boot - slow ubuntu?"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by liquidonline on 2010-09-13
Hi all,

Googling has found me tons and tons of people with slow XP partitions post-dual-boot, due to fragmentation.  However, my problem is strangely the opposite.  I've seen this on a dell d610 laptop.  I did a fresh XP pro install, pre-partitioning so I don't have to shrink the disks.  I also have a small 5 gig partition for the windows swap file, and it's already in there, at a defined size of 1.5 gigs.  The ubuntu install remained on its partition, untouched.  

Before reinstalling XP, it booted up quickly.

After installing XP, it still performed the same.

After the last (of what, 340982?) round of update/reboot/update in win XP, suddenly, when I choose ubuntu from grub2, I get a black screen while my disk churns away like mad, for at least 10-15 seconds before the ubuntu splash kicks in and I'm at gdm-login-screen in about 15 seconds.

What I've done:

Unsure if somehow this was related to a winxp update that messed with the MBR somehow, I ran grub-install on the disk.  No effect

I checked for fragmentation - non-issue, it's not fragmented much at all.

Any ideas why this would be happening?

---

### Post by oldfred on 2010-09-13
Is this wubi or a regular install.

I understand that the more partitions you have the slower the boot as it has to find & mount them.

I have a separate drive with XP that was working ok. Then when repartitioning another drive gparted would sit on sda for a long time then not show it. XP still worked but I ran chkdsk and then gparted showed the drive. I did not pay attention if boot was faster or not as it has been pretty good.

Try chkdsk even if drive shows no problems.

XP CHKDSK info:
The chkdsk command checks the specified drive and repairs or recovers the drive if the drive requires it. The command also marks any bad sectors and it recovers readable information.
chkdsk drive: /p /r
chkdsk c: /r
You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

---

### Post by liquidonline on 2010-09-13
Hi oldfred,

Thanks for the chkdisk tips.  I'll try running chkdsk on that laptop next time I boot windows.

Regarding the number of partitions, I've noticed that on my vm server that has many partitions/disks on it, but still nowhere near the delay I'm seeing here with just 4 partitions total.  Also, the weird thing in all this is that it was after the last slew of updates.  Definitely, after a fresh install using a win XP SP2 disk, there was no impact yet on boot time.

also, FYI, it wasn't a WUBI install, I did a full install by shrinking the ntfs partition, but I've since reinstalled winXP, wiping it's partition and essentially starting over (plus splitting off that 5gig partition for windows swap)

---

