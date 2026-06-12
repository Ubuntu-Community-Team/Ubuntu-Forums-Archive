---
title: "Ubuntu 12.04 server - can't find guided partitioning?"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by ericmachine on 2012-09-11
Hi everyone,

I am really stuck here. When I installed Ubuntu 10.04.4 LTS 64 bits server, I was able to see the guided partitioning, etc. But when I was trying to install Ubuntu 12.04 LTS 64 bits server, I can't seem to find any option for guided.

Either I chose active RAID1 or not, when comes to the partitioning screen, I could only see these options.

Configure iSCSI volumes (no idea, ask to put in IP and port)
Undo changes to partition (if click, purple screen forever)
Finish partitioning and write changes to disk (can't click on this, as it will prompt some root issue)

But in Ubuntu 10.04.4 LTS, I could see more options. Any idea why I am seeing this?

I download 2 different ubuntu 12.04 (latest) ISO to ensure the files were not corrupted. But the results were the same. Please help!

Note: I managed to install ubuntu 10.04.4 LTS on this server successfully. Can login. But I am stuck at the ubuntu 12.04 LTS (latest version as of today), stuck at the partition window. I want to remove the earlier installation and install the new one. I also managed to install Centos 6 successfully here. 

Basically, my plan is this:-

60GB SSD - ubuntu 12.04 LTS base install (stuck here)
RAID 1 HDD - install open stack, kvm and all virtual machines reside here.

Below are my specs:-

I just purchased 1 server with these specs:-
              - NEW Intel "Romley" platform with dual processor capable in
1U 4-bay rackmountable HPC server system
              - 2 x Intel Xeon SIX-Core E5-2620 2.0Ghz processors
- 7.2GT/s Intel QPI speed, 2 QPI Links, 15Mb Intel Smart Cache,
              Intel Turbo Boost 2.0 & Intel Virtualization (VT-x)
  - Intel C606 chipset
  - Dual QPI Links
  - 48GB ECC DDR3 1333Mhz RDIMM memory
  - 4 memory channels per CPU
  - 1 x 60GB 2.5" SATA3 SSD (for OS/Apps Rapid Startup)
  - 2 x 3TB 3.5", 6Gb/s, 7.2K rpm NL-SAS HDDs(SET AS RAID 1)
  - Support 4 x 3.5" Hot-swappable Drive Bays
- 2 x 1GbE Intel Gigabit Ethernet LAN ports
- Intel C606 SAS RAID Controller supporting RAID level 0,1 & 10
- Integrated Onboard Graphic Controller with VGA port

Thanks so much.

---

