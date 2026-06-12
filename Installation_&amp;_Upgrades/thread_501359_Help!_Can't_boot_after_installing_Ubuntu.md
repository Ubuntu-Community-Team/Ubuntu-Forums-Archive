---
title: "Help! Can't boot after installing Ubuntu"
date: 2007-07-15
forum: Installation &amp; Upgrades
---

### Post by DeltaZero on 2007-07-15
I knew I should have done a backup before trying to install Linux - and here it is! I am normally running WinXP SP2, and just 30 minutes ago I decided I should install Ubuntu to save me all the walks to PC-farm just for some ANSI-C project. I have used 6.06 LTS installation CD I received by mail long ago.

Now the HD setup on my PC is a bit tricky:
2 80GB WD Caviar SE in RAID0 (Mirroring) via nForce2 PATA RAID
1 160GB Seagate Barracuda via nForce2 SATA channel
the board is ABIT NF7-S2G

On the RAID there is 1 partition with documents (D: under Windows), and on SATA 2 partitions: 10GB Windows boot (C:) and the rest with programs and data (H: as the SATA controller comes after 2 more optical drives on PATA). All partitions were NTFS.
The RAID array was not recognized by Ubuntu correctly (shows up as 2 different drives), but anyway I wanted to install it on the SATA, so I resized the second partition there to make space (please tell me my data will be ok?).

After installing and restarting, the GRUB hangs. All I get is the "GRUB" message and nothing more. Via the LiveCD I can see the partitions, but can't mount any of them. The partition I resized (H:) even shows up as "Unformatted" (while C: is correctly identified as Windows NTFS)!

If I remember correctly, I had a problem with my BIOS only allowing to boot from the first 2 hard disks in the system (no, there is no update), meaning that if the PATA drives weren't in RAID, it would not boot anyway.  I don't know if this might be the problem.

UPD: I have set the Windows partition as boot from the LiveCD, and after disabling/enabling of the RAID in BIOS, I was able to boot into Windows. However the H: disk is totally ruined (shows up as unformatted). That's almost 100Gb programs and data!

---

### Post by Pumalite on 2007-07-15
Check this:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

[http://samokk.is-a-geek.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/](http://samokk.is-a-geek.com/wordpress/2006/01/15/running-ubuntu-gnulinux-on-a-fakeraid1-mirroring-array/)

[http://lists.alioth.debian.org/pipermail/utnubu-discuss/2006-May/000472.html](http://lists.alioth.debian.org/pipermail/utnubu-discuss/2006-May/000472.html)

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

[http://ubuntuforums.org/showthread.php?p=3014452](http://ubuntuforums.org/showthread.php?p=3014452)

Good luck!

---

