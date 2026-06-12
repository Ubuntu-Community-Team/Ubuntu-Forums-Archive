---
title: "problem with partitions, ubuntu 14.04 won't load again"
date: 2015-03-25
forum: Installation &amp; Upgrades
---

### Post by pheadweb on 2015-03-25
Hello,
I upgraded from windows 8 to windows 10 technical preview and this caused ubuntu 14.04 to won't load again. I had win 8 alongide with ubuntu 14.04 with grub menu and now I can only login to windows.
I tried several methods but nothing changed.. I'm afraid that windows broke my ubuntu partition because I can't see it and when i open gparted from a live cd it says "unallocated space".
I tried from windows easybcd in order to install something like grub and still nothing.
Also, from a live cd, I installed boot-repair and choose the reccomended way and it didn't work. However, here is the link from boot repair attempt:
[URL="http://paste.ubuntu.com/10680563"]
http://paste.ubuntu.com/10680563[/URL]

I had ubuntu and win in one drive and i also had another drive (1tb) for my files etc..
if you know anything or you see any error from the link above please let me know.. I really want to keep my ubuntu partition, I don't care for win even if i need to delete it
Thanks

---

### Post by oldfred on 2015-03-25
Windows does not correctly see Linux partitions especially inside an extended partition.

You show a large extended partition sdb3, but only swap sdb5 inside it. Swap probably was sdb6 and Linux sdb5 inside the extended partition.

Some have used testdisk to restore missing partition, keeping all other partitions and when booting from grub system just worked.

Testdisk is in repository, so you can boot from live installer and add it to your live install. Or most Linux based repairCDs include testdisk.
 Testdisk Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

When you installed Windows was sda set as default in BIOS? But you installed Windows to sdb?
Windows installs its boot files to the drive set as default in BIOS where grub always installs to sda unless you use Something Else and choose a different drive.

Usually best to have all of Windows on one drive and all of Ubuntu on another drive. Then when one drive fails, you can switch and boot other drive from BIOS. But if parts are on both drives then both drives have to work to boot either system.

---

