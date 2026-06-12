---
title: "Actvate serial ATA Raid devices FAIL!"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by Fenlig on 2012-01-16
Hey Guys,
 
OS: Ubuntu server 11.10
 
Okay i have 4 hdd and raided through an intel raid controler in RAID 1 and im trying to install Ubuntu on them, but its not picking up my devices.
 
I get to the "[!] Detect disks" prompt where it stats its found SATA raid devices and asks if I want to activate them so I click "Yes" and in the next window where I am to see all my devices I see nothing but "Configure ISCSI volumes", "Undo changes to partitions" or "Finish partitioning and write changes to disk" :(
 
What do I do :(

---

### Post by MAFoElffen on 2012-01-17
> **Fenlig said:**
> Hey Guys,
 
OS: Ubuntu server 11.10
 
Okay i have 4 hdd and raided through an intel raid controler in RAID 1 and im trying to install Ubuntu on them, but its not picking up my devices.
 
I get to the "[!] Detect disks" prompt where it stats its found SATA raid devices and asks if I want to activate them so I click "Yes" and in the next window where I am to see all my devices I see nothing but "Configure ISCSI volumes", "Undo changes to partitions" or "Finish partitioning and write changes to disk" :(
 
What do I do :(
Intel RAID Controller? Which RAID Controller?  An actual Server RAID controller such as an LSI MegaRAID or equivalent? Or a desktop motherboard "RAID" addition?

Anyways. On my server that has an Intel server board with true hardware RAID, I have to build the Array in the Controller BIOS. All I see in partman is a named RAID Array that shows up just like a single drive. I can partition it, spec how to format it as and how to mount it.  On my 4 other servers that have hardware RAID, the same.  That sounds a bit different than what you have going on.

Now on software RAID on those servers (mdadm), I see the individual drives and partition them before building the Array, set the type, set the drives and spares, Finish... Then partition the Array, the filesystem, mounting... And the Array is listed At the top of the list of drives.

If I have drives that have been in RAID previously and have a Superblock.... Or those that are or where in Software RAID (also have a superblock)... Then those drives do show up in partman as "RAID" as it's file type.

Neither way sounds completely like what you have going on... Does it? What "do" you have and what are you trying to do?

---

### Post by Guilden_NL on 2012-01-17
I am smelling in bug in 11.10 with this issue.  

Was able to detect and install to my system that has a 10,000RPM drive for dual boot with WIN and two drives set up as RAID 1 from Hardy through 11.04.  Now it's puking, just as Fenlig is experiencing.

My raid is set up via NVidia RAID utility w/ two 75GB HDs mirrored.

Yet using the alternate version it does exactly what Fenlig is experiencing.  

It appears that this is a new bug introduced with .10 release.  I've worked on it for 7 hours and there is no workaround, other than going back to 11.04.

---

### Post by ccropper on 2012-04-19
I am having the same issues with an Intel Z68 based motherboard from Gigabyte. The RAID is provided by the Intel chipset and is seen but it can't find the driver. Disabling the RAID and setting the BIOS to AHCI and the drives are seen. I am trying to install 12.04 Beta2 in preparation for LTS in a week. I need a fix quickly as these are a high priority for completion. Any help would be great.

---

### Post by tentimes on 2012-08-26
Same issue here on a Z68 board. It says it sees Raid, I click yes to activate, then I get a blank screen. Purple with grey text spaced line at the bottom. I can type in this line, but nothing happens until I click on CTRL+C, then it exits to the menu.

Can Anyone help please? I have spent 4 days on this now and it is driving me insane.

---

