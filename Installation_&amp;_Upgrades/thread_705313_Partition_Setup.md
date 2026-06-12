---
title: "Partition Setup"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by krezeb on 2008-02-23
Hi
I'm pretty new to Ubuntu but the more I use it, the more I like it. Until recently I was using WinXP.. I read on Digg that GG was released and I got curious.

I also figured it was time to format the HD anyway, so I reformated the primary HD, installed Ubuntu from a live disk (without a hitch) and then set up a dual boot with WinXP.

I have 3 HDs and while I've been using WinXP I've arranged them thusly:
HD1 - 80GB - Boot Disk (ONLY OS INSTALLED) (NTFS + An Ubuntu FS)
HD2 - 160GB - Application Disk (Games and Programs installed here) (NTFS)
HD3 - 500GB - Storage (Installation files/pics/vids stored here) (NTFS)

When I installed Ubuntu I reformated HD1 as a 40GB/40GB split - one partition with Ubuntu installed, and the second with WinXP. As WinXP was my primary OS I decided that 40Gb would have to do for the mean time.

I've now decided to do an 80GB/80GB Split of the Application Disk, but I have no idea how to set it up inside Ubuntu.. I don't know how applications/games are installed in Ubuntu and I haven't been able to find a description of how the Filesystem is set up (what /home, /root, /etc mean).

I understand that *unix is a complicated system, but I want to move away from Microsoft as I'll never buy Vista. Ever.

Any help would be appreciated.

//Lachlan

---

### Post by pebo on 2008-02-23
[This]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") link explains the directory set up in Unix. Most programs get installed into the /usr/bin directory. As for games, look through Synaptic for what's freely available for linux, but you will probably want to install [wine]("http://www.winehq.org/") to run (some) windows games. Also installable through Synaptic.
To set up your partitions on your second disk, use gparted  which works similarly to Partition Magic.
> I understand that *unix is a complicated system, but I want to move away from Microsoft as I'll never buy Vista. Ever.Good luck, and don't throw in the towel when the going gets tough ;)

---

### Post by Pumalite on 2008-02-23
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
Tutorials:
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://www.ubuntugeek.com/tag/ubuntu-hacks/](http://www.ubuntugeek.com/tag/ubuntu-hacks/)

---

