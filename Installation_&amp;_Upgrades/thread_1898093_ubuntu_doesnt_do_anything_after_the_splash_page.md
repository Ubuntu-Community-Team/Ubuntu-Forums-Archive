---
title: "ubuntu doesnt do anything after the splash page"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by shmirty on 2011-12-20
i just installed ubuntu 11.10 and it worked fine until i restarted my computer (toshiba satellite C650 series). i tried booting from the liveCD and that didnt help. i have 4 options on my GRUB page (i have GRUB 2), normal boot, recovery mode, and two types of memory tests. my recovery menu is the limited read-only menu (resume normal boot, check all file systems, remount, and drop to root shell prompt). ive fiddled around with it i came across two things that could be the issue( but im not sure i have no idea considering im new to linux), one said 'fake initcle called, doing nothing' and 'fsck from util-linux 2.19.1 /dev/sda1: clean, 141153/15147008 files, 1699810/60558848 blocks [ 14.348313] EXT4-fs (sda1) : re-mounted. Opts: errors=remount-ro'.and below it it says:
*starting configure network device [ok]
*starting configure network device security [ok]
*starting configure network device security [ok]
*starting configure network device [ok]
*starting configure network device security [ok]
*starting configure network device [ok]
*stopping cold plug devices [ok]
*stopping initial device creation [ok]
*starting enable remaining  boot-time encrypted block devices [ok]
*starting configure network device security [ok]
*starting enable remaining  boot-time encrypted block devices [ok]
*stopping mount filesystems on boot
*starting CUPS printing spooler/server

---

