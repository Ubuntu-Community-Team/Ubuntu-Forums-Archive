---
title: "Ubuntu server on IBM x3400 server with RAID"
date: 2015-01-22
forum: Installation &amp; Upgrades
---

### Post by md_saadh on 2015-01-22
Help me to install ubuntu server on my ibm x3400 server with raid, i have two hard disks and i want to make mirroring option in cmos please give me the solution

---

### Post by MAFoElffen on 2015-01-22
Boot with the IBM ServRAID Disk or IBM Server Setup Disk. IBM RAID controllers- You have to have one of those two disks to set up their RAID config. You can only do basic lookup from BIOS itself. At least on the older XSeries servers I have, that is the way it is on mine. You should be able to download those from IBM. (I did.)

Once you get it set up, and powered down, then boot up from the Server Install disk and it will be viewed as one volume. Because it does not have those capabilites from bios (Like LSI controllers do), 

After the install, I copy over the ServRAID ISO somewhere and set it up as a custom menu option in the Grub Menu.That way, if I do need to do something RAID related, I don't have to have that disk in hand = I can just boot it straight from ISO.

I also converted the IBM's rhel ServRAID Management Utility (from rpm to deb)... and it runs fine on mine under 14.04 LTS. I can run that as ssh X-forwarded from my console. (It's a graphical application.)

---

