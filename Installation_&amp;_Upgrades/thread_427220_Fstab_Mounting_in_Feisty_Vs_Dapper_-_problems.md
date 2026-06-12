---
title: "Fstab Mounting in Feisty Vs Dapper - problems"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by undecidable on 2007-04-29
Did a clean install of Feisty a few days ago, and generally a very nice experience - works well, and went well.
Two issues on which I am racking my brains:

1.  On a laptop with Dapper, fstab line:
	/dev/hda5  /D  vfat  user,noauto  0  0 
      results as expected in the partition being not mounted, but mountable.

BUT on Feisty the line
	UUID=...    /D vfat  user,noauto,rw,async,utf8,umask=007,gid=46  0,0
	results in the partition being automatically mounted!
Replacing the uuid with /dev/hda5  makes no difference - still automounts.
What am I doing wrong?

2.  I have Disk Mounter in the panel.
On Dapper, partitions with no entry in fstab do not appear in the panel.
However on Feisty, even partitions with no entry in fstab appear in the panel as mountable,
and in fact I can mount them.
(the partitions have no entry in fstab either because I commented out the entries
to try and stop them appearing,
or because they are on a disk I added after installation and they have no entries in fstab.)
Grateful if anyone can make any sense of this - if there are no fstab entries,
why do they appear and can be mounted?

Have attached my fstab if it is helpful.

---

