---
title: "dual boot ubuntu 7.04 and XP: XP works, ubuntu doesn't!"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by NielsMRS on 2007-04-24
I have a Dell Optiplex320, with XP installed.

Before installing Ubuntu there were two partitions: One tiny one by Dell (some rescue utilities), and one 80GB one for XP. Both are primary. 

There was also 80GB unallocated (free) space. 

My idea was to put Ubuntu in the 80GB free space. During the partition manager part during installation, I chose manual partition. The guided partitioner wanted to first resize my harddisk into one 160GB, and then make linux partitions. I though it would be easier not to touch the XP partition, and so decided for a manual partition.

I put a 1GB swap partition, followed by a 79GB 'ex3' linux patrition, for which I put mountpoint "/". Everything else I left as is.

Installation went smoothly and reboot brings me into the grub dual boot screen from which I can pick linux or XP. 

XP boots normally, but when I pick linux it just gives me a blinking cursor in the top left and nothing happens. It seems as if the grub program cannot find linux for some reason. 

Anyone have some ideas???

---

