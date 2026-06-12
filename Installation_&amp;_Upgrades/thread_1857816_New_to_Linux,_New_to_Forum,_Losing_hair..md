---
title: "New to Linux, New to Forum, Losing hair."
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by Chronomega on 2011-10-11
Good evening all and thanks in advance for looking at my thread.

I have been reading for about the last 10 hours and testing and frustratedly cursing at my new computer I just built this evening.

I am not entirely new to Linux, however I am very new to installing Linux server to a new computer using RAID.

Here is what I have:
[COLOR=Black][SIZE=2][FONT=Arial]MSI H67MS-E23 Intel H67 Mobo
i5-2500k
4x 2TB Hitachi Deskstar 7K3000 HDDs (SATA)

I have tried everything. Raid 1, Raid 5, Raid 6. I would be extremely happy to run at Raid 1. Here is my issue. I see it all over the internet but have not found a solution that has worked.

I manually partition my 4 drives to each have a swap partition and a partition for the rest of the data. I then RAID the swap and the remaining partitions (Swap and Main partitions separate) which gives me 2 RAID drives. Installation goes beautiful. No issues. Until Grub2 starts to install.

Grub2 detects that the last fresh install is my only bootable OS. So it tries to install and fails (instantly) at 50% with a Fatal error. When I try to manually input the install path, it defaults to /dev/sda[/FONT][/SIZE][/COLOR][COLOR=Black][SIZE=2][FONT=Arial] /dev/sdb[/FONT][/SIZE][/COLOR][COLOR=Black][SIZE=2][FONT=Arial] /dev/sdc[/FONT][/SIZE][/COLOR][COLOR=Black][SIZE=2][FONT=Arial] /dev/sdd

I have tried even creating a seperate RAID partition and setting it as the /boot. Still no dice. I am trying to get this setup on a very small timeline and it is pretty stressful.

Once again I really appreciate any and all help in advance. As for now, I'm going to bed. It's been a long day.
[/FONT][/SIZE][/COLOR]

---

### Post by mastablasta on 2011-10-11
have you already looked at this: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by Chronomega on 2011-10-11
I have gone through that guide multiple times hoping to find something I'm missing. That guide is primarily why I decided to go the route of RAID 1 because of it supposed compatibility with installing the /boot to a RAID 1 and also the fact that RAID 1 is an option that allows disk replacement if there is degradation. Plus it would seem that this guide shows a slightly older view of the installer GUI that seems to partition slightly different than 11.04. Unless it is just Server edition that is different.

---

