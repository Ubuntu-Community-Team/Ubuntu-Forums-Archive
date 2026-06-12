---
title: "Ubuntu 15.04, is it safe to migrate /usr to lvm2 volume?"
date: 2015-10-06
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2015-10-06
Hi,

I have an existing Ubuntu 15.04 installation.  I only gave the root filesystem 10g (because who puts more than that on /?) but do not have a separate /usr partition.

I have 539m left on /.  The rest of my drive is an LVM2 partition and it's populated but has plenty of space.

Is it safe to put /usr on lvm2 with Ubuntu 15.04?

I'm comfortable with duplication of /usr to the lvm and all that pertains, but not with setting up an initramfs.

Thanks.

---

### Post by 1clue on 2015-10-06
Solved on my own.  I tried it, it worked.

---

### Post by TheFu on 2015-10-06
If the new /usr appears to be in /usr just after boot, it will be fine. 
The Linux File System Hierarchy Standard explains which top-level directories must be local and available at boot. [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)
specifically [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/usr.html)

---

### Post by 1clue on 2015-10-06
Yes, but systemd is changing things.  I wasn't sure if there were extra hoops to jump through to get it to work.  As well I'm not sure exactly how much systemd is integrated into Ubuntu at this point.

---

### Post by 1clue on 2015-10-06
Whatever the state of systemd and /usr merge, this worked seamlessly on 15.04

---

### Post by TheFu on 2015-10-06
> **1clue said:**
> Yes, but systemd is changing things.  I wasn't sure if there were extra hoops to jump through to get it to work.  As well I'm not sure exactly how much systemd is integrated into Ubuntu at this point.

Doubt that mount order in the fstab will be changed by systemd. Suspect only concurrent mounting might happen - mainly to help large storage servers with hundreds of disks.

I've had to fight with some systemd stuff on a new debian box running a 4.2 kernel. Some of it is really nice. Some of it sucks. BIGTIME. IMHO, it needs 2+ more years to mature before being used in an LTS.

---

### Post by 1clue on 2015-10-06
The thing I was worried about is the /usr merge. At least last time I checked, the systemd guys were trying to combine /usr/bin and /bin, /usr/sbin and /sbin, and so on, on the premise that there was no good reason to have a separate /usr partition anymore, and the parallelism introduced by systemd made it difficult to boot without all the tools being available from the get-go.

I think this is pure horse droppings, but at this point I'm not fighting it on this box.  On  my Gentoo boxes I'm doing things differently...

---

### Post by TheFu on 2015-10-06
pretty soon, there will only be 1 program running on our systems - systemd or was that "MCP?"

---

### Post by 1clue on 2015-10-06
Seriously, let's not go there.  Been through months/years of that BS on Gentoo forums, don't want to draw that kind of crowd.

I'm completely with you on the maturity of systemd, but this is such a political $#!+ storm for some reason and it's just not worth all that angst.

---

