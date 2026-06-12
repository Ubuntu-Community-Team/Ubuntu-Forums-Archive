---
title: "Successful install with Raid 1 with no extra software, sorta... sata 3gb/s also"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by geedew on 2007-06-09
My setup
gigabyte m59sli-s5 f7
2 gig of ram (1X1gb)
AMD am2 5200+ dual core 64 bit (2.6ghz)
gigabyte G-Raid config with dual 160gb Seagate Sata II 3g/s
dual booting windows xp pro... already setup on the raid

Ok, so I really really like ubuntu and running ubuntu... and this is a task that I think many have failed before.. but somehow it is working for me, with minimal issues.

So I googled some thing and started with loading the cd... which failed at the:
Kernel alive -> direct mappint tables blah blah blah..

Figured out to get around this is to alter the boot command so it has the option acpi=off...this also will recur in grub, so the option must be there too.

So now that I can boot into ubuntu off the livecd... I went to synaptic package manager (System->administration->synaptic package manager).
Opened up the universe repository (Settings->Repositories->::check:: community maintained open source software).
Then I installed dmraid (thank you [http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)).
Opened up the gParted program (System->Administration->Gnome Partition Editor).
At this point the installer noticed the drives as one drive. So I opened up some open space and stopped there.

Restarted the computer, booted off the live cd.. did the acpi=off to get past the installer failure and went into the installer.  This time I did not have to install dmraid.. or partition anything as I had already freed up space.  

I ran the install.. it notices both drives (they are mirrored).  The first one had free space... that opened up, the second one still looked full.  So I created a swap, a root and a home partition on the free space and continued.When It finished... I restarted.

Grub loads and notices two installs of Windows :P and a Linux.   the G-Raid config still says that the mirror is in fact intact.  grub needs to be edidted to have the acpi=off feature.  but so far, nothing else has thrown any fits.

:P

---

