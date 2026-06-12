---
title: "Missing Operating System  Ubuntu Server 12.04"
date: 2014-10-15
forum: Installation &amp; Upgrades
---

### Post by RezaPradipta on 2014-10-15
Hello.

I have problem with linux ubuntu server 12.04, I got error message "operating System Missing" at boot process, here is my disk looks like

Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  499GB  extended
 5      257MB   500GB  499GB  logical                lvm


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/dev01-swap_1: 4291MB
Sector size (logical/physical): 512B/512B


Please help me recover my ubuntu. if you need more information i'd be happy to provide,

sorry for bad English


Thanks

---

### Post by TheFu on 2014-10-15
That's a start for the information. Please run boot-info or boot-repair and post the URL provided by either of those tools. My signature has links.

---

