---
title: "unmounted root partition is accessed through and obscures a 2nd mounted partition"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Anon2 on 2011-01-15
[COLOR=#000000][FONT=DejaVu Sans]Hi, my google skills are pretty good but I found this error difficult to define with a short query.

[/FONT][/COLOR]I[COLOR=#000000][FONT=DejaVu Sans]'ve attached a screen-shot which shows the error at a glance. In words:[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]1. Recently installed a new sata drive which became /dev/sda. Existing device names were shunted by one letter.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]2. After correcting the device name of the swap partition from /dev/sdc2 to /dev/sdd2, ubuntu boots without complaint and my hard drives look like:[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]sda - sata (sda1 (other os) label=newwin ntfs)[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]sdb - sata (sdb1 (other os) label=oldwin ntfs)[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]sdc - ide (sdc1 (ubuntu) label=ubuntu ext3)[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]sdd - ide (sdd3 (data) label=e ext3, sdd1 (data) label=f ext2, sdd2 (linux-swap) label=none linux-swap-partition)[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]3. Gparted shows that sdc1 (ubuntu) is not mounted at all (when it should be mounted on '/' as fstab states), and that sdd3 (data) is instead mounted on both '/' and '/e' (when it should be mounted only on '/e' as fstab states).[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]4. 'ls /' does not however show the contents of sdd3 (data), but the contents of sdc1 (ubuntu).[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]5. 'ls /e' does not show the contents of sdd3 (data), but the contents of sdc1 (ubuntu)[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]6. So although sdc1 (ubuntu) is unmounted, it can somehow still access itself through the fact that sdd3 (data) is mounted on '/', and the system does boot. And although sdd3 (data) is also mounted on '/e', 'ls /e' is equivalent to 'ls /'.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]7. Below is the relevant snippet from my fstab, which is also visible in the attachment:[/FONT][/COLOR]
 
 ```
[COLOR=#000000][FONT=DejaVu Sans]# / was on /dev/sdc3 during installation
[/FONT][/COLOR][COLOR=#000000][FONT=DejaVu Sans] #UUID=2e1992af-cf1a-4ae8-a794-bb17d855ebef /               ext3    relatime,errors=remount-ro 0       1[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]# after adding new hard drives and moving partitions / is currently on /dev/sdc1...[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]#/dev/sdc1                   /   ext3    relatime,errors=remount-ro 0       1[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]#UUID=0b235ad9-522e-46e1-abc0-96d607ffa3ee   /   ext3    relatime,errors=remount-ro 0       1[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]LABEL=ubuntu   /   ext3    relatime,errors=remount-ro 0       1[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]# ...and /dev/sdc3 is now called /dev/sdd3 and contains data...[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]#/dev/sdd3                   /e               ext3   defaults,rw 0 0[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]#UUID=2e1992af-cf1a-4ae8-a794-bb17d855ebef   /e               ext3   defaults,rw 0 0[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]LABEL=e   /e               ext3   defaults,rw 0 0[/FONT][/COLOR]
 [COLOR=#000000][FONT=DejaVu Sans]#...the command above doesn't work. ls /e shows contents of / and gparted shows: [/FONT][/COLOR]
``` [COLOR=#000000][FONT=DejaVu Sans]8. The first line shows that ubuntu was on /dev/sdc3 during installation. I cannot remember why this is, but prior to installing the new hard drive ubuntu was installed on /dev/sdb1 and was booting normally while '/' was mapped UUID=0b235ad9-522e-46e1-abc0-96d607ffa3ee (now /dev/sdc1). In other words a similar problem did not occur with /dev/sdb1 (ubuntu) and /dev/sdc3 (data) before the new hard drive was installed.[/FONT][/COLOR]
 
 [COLOR=#000000][FONT=DejaVu Sans]9. I have tried both uuid and labels in fstab, but this problem still persists. As it is the system is usable but I cannot access my data on drive sdd3. 
[/FONT][/COLOR]

---

