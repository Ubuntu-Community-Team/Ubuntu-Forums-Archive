---
title: "Missing PV on volgroup after replacement of failed hard drive"
date: 2015-07-12
forum: Installation &amp; Upgrades
---

### Post by Howard_Perceval on 2015-07-12
Hi - the disk I had my os installed on failed (I couldn't even run a live CD as the bios would always give a Master Disk failure message). So, I replaced the drive and re-installed Ubuntu Server [COLOR=#393939][FONT=arial]14.04.2. This created a new volgroup (called [/FONT][/COLOR][ServerMain-vg]("https://servermain.home:10000/lvm/edit_vg.cgi?vg=ServerMain%2Dvg")) but my old volgroup remained (called volgroup). This contains 3 physical volumes (and the old drive). I've managed to mount etc but when I try and resize one of the LVMs it I get an error 

[B]Couldn't find device with uuid JOFPpy-3bKL-aOh4-NhpF-q9rA-pxfi-6i5o6e.
  Cannot change VG volgroup while PVs are missing.
  Consider vgreduce --removemissing.


[/B]I'm assuming this is the physical volume I removed. How can I repair it so the system knows that this volume no longer exists? All my data is in this volgroup so I'm nervous about doing anything with it. 

Any help would be much appreciated

---

### Post by Howard_Perceval on 2015-07-16
Fixed using vgreduce

---

