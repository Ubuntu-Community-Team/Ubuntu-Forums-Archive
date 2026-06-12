---
title: "Mounting a nVidia RAID disk"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by Sakshale on 2011-07-24
I have a pair of disks that were part of a mirror on a motherboard with a nVidia nForce 590 SLI chip set, which decided to stop booting one day.

When I attempt to mount them, using a SATA to USB adapter, I am prompted, as expected, for the encryption password, which it does seem to accept iwithout problem.  Unfortunately, however, it does not seem to recognize the formate of the decrypted disk.

A gnome-disk-utility screen shot can be viewed here;
[http://www.flickr.com/photos/13732178@N07/5971911688/in/photostream](http://www.flickr.com/photos/13732178@N07/5971911688/in/photostream)
As you can see, the only option it gives me is to reformat.

I found the following in **syslog **

> Jul 24 13:17:06 Neptune kernel: [  760.826161] scsi 11:0:0:0: Direct-Access     WDC WD50 00YS-01MPB0      0041 PQ: 0 ANSI: 0
Jul 24 13:17:06 Neptune kernel: [  760.833524] sd 11:0:0:0: Attached scsi generic sg4 type 0
Jul 24 13:17:06 Neptune kernel: [  760.834089] sd 11:0:0:0: [sdd] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Jul 24 13:17:06 Neptune kernel: [  760.835458] sd 11:0:0:0: [sdd] Write Protect is off
Jul 24 13:17:06 Neptune kernel: [  760.835468] sd 11:0:0:0: [sdd] Mode Sense: 03 00 00 00
Jul 24 13:17:06 Neptune kernel: [  760.836350] sd 11:0:0:0: [sdd] No Caching mode page present
Jul 24 13:17:06 Neptune kernel: [  760.836357] sd 11:0:0:0: [sdd] Assuming drive cache: write through
Jul 24 13:17:06 Neptune kernel: [  760.839531] sd 11:0:0:0: [sdd] No Caching mode page present
Jul 24 13:17:06 Neptune kernel: [  760.839539] sd 11:0:0:0: [sdd] Assuming drive cache: write through
Jul 24 13:17:06 Neptune kernel: [  760.840368]  sdd: sdd1 sdd2
Jul 24 13:17:06 Neptune kernel: [  760.842953] sd 11:0:0:0: [sdd] No Caching mode page present
Jul 24 13:17:06 Neptune kernel: [  760.842960] sd 11:0:0:0: [sdd] Assuming drive cache: write through
Jul 24 13:17:06 Neptune kernel: [  760.842967] sd 11:0:0:0: [sdd] Attached SCSI disk
Jul 24 13:17:06 Neptune dmraid-activate: ERROR: Raid set nvidia_bjdchedb is degraded. Not activating
Jul 24 13:17:06 Neptune kernel: [  761.355406] EXT4-fs (sdd1): recovery complete
Jul 24 13:17:06 Neptune kernel: [  761.355411] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)

---

