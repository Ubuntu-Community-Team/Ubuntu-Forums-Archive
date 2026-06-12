---
title: "Concern with partitions after Ubuntu re-install"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by fatsam on 2012-10-24
I have a dual-boot of Windows 7 (/dev/sda2) and Ubuntu 12.10 (/dev/sda1). I have recently completed a clean install of Ubuntu 12.10 after failing to do an Upgrade from 12.04 to 12.10. Before I did the clean install of Ubuntu 12.10 I deleted the Ubunter 12,04 partitions in Gparted via Live-CD which left me with my Windows 7 partition (sda2) and an unallocated space of 100mb.  Everything seems to be working fine but I have a few concerns about the partition layout shown in Gparted and was seeing if anyone could help me.

Here is a screenshot of my current partition layout in Gparted:

[IMG]http://i50.tinypic.com/suu83a.png[/IMG]

1. When it was only Windows 7 installed (and the unallocated space of 100mb) it showed the partition path was sda2...is this normal? There were no other paths on the HDD so shouldn't it have changed to sda1? Or isn't that possible.
2. After trying to merge the unallocated space to my Windows 7 partition I got this error:

[IMG]http://i48.tinypic.com/2cgn7eh.png[/IMG]

What is happening here?

3. Before I completely deleted the Ubuntu 12.04 partition and did a clean install next to Windows 7 there were no unallocated spaces shown on Gparted. In fact I remember seeing a 'boot' label which is in the same place as the unallocated space and the same size.

4. Is it possible to allocate the space without harming the boot process? And if so, how come I can't completely merge the unallocated space to my ntsf partition (leaving 1mb behind).

Thank you in advance.

Regards

Jay

---

