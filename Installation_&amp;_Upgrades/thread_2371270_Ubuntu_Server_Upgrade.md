---
title: "Ubuntu Server Upgrade"
date: 2017-09-12
forum: Installation &amp; Upgrades
---

### Post by hellotyler on 2017-09-12
[FONT=Helvetica][COLOR=#000000][FONT=Lucida Grande]I&#8217;ve got a few hard drives other then my OS drive (an SSD) and I&#8217;m trying to do is keep the data on these other internal drives &#8230;. I want to install a new OS and SSD drive -  I can rebuild everything related to non admin user access. How do I make sure I don&#8217;t lose access to any of my files on the other internal drives ? Modify permissions somehow ?[/FONT][/COLOR][/FONT]

---

### Post by HankB on 2017-09-13
Best bet is to disconnect the SATA cable to the drives you don't want disturbed. Then there is no possibility that drive contents will be altered. Just plug them in when the new OS is up and running, add mount points for them and add to /etc/fstab. (If that's not clear, ask!)

If there is data on the drive you need to install the OS on, the only way to guarantee that it is not touched is to back it up (to a drive you can disconnect.) As part of the installation you can repartition the drive and that will wipe out any data regardless of file permissions. If you are careful you can install to an OS partition and leave the other data there. I've done that many times. But there are no guarantees.

HTH,
hank

---

