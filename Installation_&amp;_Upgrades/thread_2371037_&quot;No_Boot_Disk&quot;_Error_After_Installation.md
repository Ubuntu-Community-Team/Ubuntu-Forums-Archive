---
title: "&quot;No Boot Disk&quot; Error After Installation"
date: 2017-09-10
forum: Installation &amp; Upgrades
---

### Post by foxtrot1014 on 2017-09-10
I downloaded Ubuntu Server 17.04, put it on a flash drive, then installed it to a computer. Installation appears to go successfully, but when I remove the install media and reboot, the computer tells me that no boot device can be found or it is damaged. When I boot into BIOS, a disk labeled "ubuntu" appears under the boot order list.

I completed the installation using guided partitioning and think this might be a problem. I followed a [tutorial ]("https://www.htpcbeginner.com/ubuntu-server-partition-scheme-guide/")to manually setup partitions for a home server, but when I get to the step to select the "bootable flag" I can't enable the option.

I've installed opensuse to this system and it worked.

Any suggestions?

---

### Post by foxtrot1014 on 2017-09-10
I tried installing the LTS version of server, no luck.

I found an answer under ask ubuntu that might work, but not for me. Even if I enable a BIOS password (as another Ask Ubuntu answer suggested), I can't access the efi files for booting.

---

