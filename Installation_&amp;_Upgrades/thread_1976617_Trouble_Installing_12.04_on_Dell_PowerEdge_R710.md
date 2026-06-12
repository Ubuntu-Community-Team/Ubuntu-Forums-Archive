---
title: "Trouble Installing 12.04 on Dell PowerEdge R710"
date: 2012-05-09
forum: Installation &amp; Upgrades
---

### Post by Nizpiz on 2012-05-09
I am attempting to install 12.04 64 on a Dell PowerEdge R710 with the goal of configuring a network traffic analyzer. The server has the SAS6IR RAID controller with four 146G SAS drives. The controller only supports RAID 0 and 1, so I configured the four drives as two RAID 1 Virtual Disks.
 
I downloaded the server .ISO and burned it to a DVD. The first time I installed it, I used guided partitioning with LVM. Everything seemed to install properly, but after the reboot and a brief flash of GRUB, the screen went blank. I left it there for a few hours while I was off doing other things, but it remained in that state so I power-cycled the server by holding the power button. When it finished booting again, I was presented with GRUB and selected the 12.04 installation to boot; however, it did not boot and instead spammed the screen with errors. I can't recall the specific errors just now, but they were something like 'wrong page' and 'unknown partition'.
 
At first I thought maybe the firmware was too old, so I downloaded the Dell SUU .ISOs and upgraded to the latest. This dod not work. Next, I thought it might be the DVD, so I ran the integrity check after booting from the DVD. The DVD is fine though. Then I thought maybe it was the automagic partitioning, so I set up the partitions manually using only one RAID 1 Disk as using the first 300M for boot using EXT4, and the rest for LVM. In LVM I made a single group with three volumes; 2G swap, 30G root as EXT4, and the rest home as EXT4. This still had the same results as above; one reboot hangs with no putput for several hours, then another reboot gives the above errors.
 
Right now, I think it may be LVM, so I am reinstalling once more and plan to manually partition without LVM. At the same time, I am downloading 10.04.3.
 
If anyone has any pointers, I'd greatly appreciate some assistance.

---

### Post by dochong on 2012-05-10
1,
Type on keyboard:  exit, the system should boot in.

2,
sudo vim /etc/default/grub
  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
  GRUB_CMDLINE_LINUX="rootdelay=60"

3,
sudo update-grub

4,
Reboot, wait at least 60s after grub boot,  and then system boot on automatically.

---

### Post by dochong on 2012-05-10
Do not forget this:
After change /etc/default/grub, must run:
   **sudo update-grub**

---

### Post by Nizpiz on 2012-05-15
This did not work initially, but then I changed rootdelay to 90 and it worked after that.
 
Thanks!

---

### Post by me01273 on 2012-08-17
I had the same problem and I had to use rootdelay=90 as well, although I didn't use "quiet splash" as I didn't see the point of this on a production server and thought it more important to be able to see boot information.

---

