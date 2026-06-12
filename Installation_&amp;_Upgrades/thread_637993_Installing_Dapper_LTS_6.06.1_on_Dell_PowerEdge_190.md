---
title: "Installing Dapper LTS 6.06.1 on Dell PowerEdge 1900/2950 servers"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by KennedyM on 2007-12-11
Just a summary of some recent experiences, in case they're of any benefit to others, or in case anyone has further ideas...

The servers are hot off the assembly line - Nov/Dec 2007. Presumably the same issues arise on similar servers - 1950, 2900, etc...

I wanted to use RAID-1 (preferably software/OS/Linux RAID), so each server has 2 x HDDs - certainly SAS/SCSI in the 2950, and I think the 1900 also has SAS.

Other threads here deal with the issue of the Gb NICs not being detected - just edit /etc/network/interfaces later.

Re RAID-1 on the 1900:
The 1900 was shipped with the RAID-1 array defined in the BIOS. LTS 6.06.1 could not see any drive, and, visually, the install "hangs" at the disk-detection stage - Ctrl-C goes to the Partitioning step, which ain't much use! When I deleted the BIOS Array, but left the controller enabled, Dapper then saw the 2 x HDDs just fine. I set up OS RAID-1, installed, etc, and Dapper booted OK.

Re RAID-1 on the 2950:
The 2950 is also shipped with the RAID-1 array (Virtual Disk) defined. If I delete this array, and disable the controller, LTS 6.06.1 sees nothing, and, visually, "hangs". Enable the controller, and Dapper sees the 2 x HDDs. The Install then goes fine, including RAID-1 setup, etc, but... nada on re-boot. Seems the BIOS is unable to boot, unless RAID is defined in the BIOS (or, perhaps, the controller itself is disabled?). So, back to defining the VD in the BIOS - then Dapper see THREE drives - the 2 x physical ones, and the VD. Many thanks to other contributors here who have covered this mess-up, and who supplied solutions.

I had no problems like these when installing Dapper LTS on older Poweredge servers. Seems these issues are resolved in later Ubuntu releases, later kernels, etc - so, "wouldn't it be loverly" if an updated Dapper were available... 

Overall, quite frustrating... So far...

  - Mike

---

