---
title: "Installing 24.04 to New machine, copy HOME directory from older 22.04 ??"
date: 2024-05-09
forum: Installation &amp; Upgrades
---

### Post by BrassCat on 2024-05-09
Hello the forum. Well, I read to not upgrade 22.04 to 24.04. Only do new install for now.
Fine.  I have a new hardware build running ubuntu 23. just experimenting with it and
getting all hardware running correctly. I will reformat and perform clean install 24.04

I would like to bring as much of my work (and installed programs) as I can from my
older 22.04 system as I can. It would appear most all is in and under the HOME directory.
 What are the dangers in doing this. Obviously I wont change anything on my existing 
22.04 system. My guess I will have to reload extra programs like bottles and others.

Stating more clearly, copy HOME directory from 22.04 to HOME on 24.04 system

Thanks, Stan

---

### Post by TheFu on 2024-05-10
I'd copy the HOME over and perhaps some system configs from /etc/ would be selectively merged, then I'd use a list of installed 22.04 packaged software (this can be created lots of different ways) and feed that list of applications into the new system for install. 

Just be certain that data is where it needs to be, with the correct owner/group/permissions BEFORE you install the packages.  Also, if there are any system config files, I'd merge/copy those BEFORE installing.  Be careful copying, since overwriting new system-wide config files created by the 24.04 installation will likely lead to a system that won't boot or specific programs that won't run.

And be 100% certain that you can try this a few times, so have excellent backups on both sides.  There's something about having backups which almost assures you won't need them. I don't know why it works that way.  The opposite is also true.  If you don't have backups, you will almost certainly need them.

---

### Post by MAFoElffen on 2024-05-12
+1 -- 

Except... I would further recommend, that since you are already adding a new install, to create a separate /home partition or LV (if using LVM2) on it's own pv/vg. That way, next time you go to migrate to a newer release or do a release upgrade, the separate home is already setup to just be shared or moved to the newer system.

That isn't something that is in the "default install" without some manual partitioning, but that makes things so much easier, and more secure down the road. With the new installer, you can do that easily for a normal partition with ext4... But for LVM2, is easier to move the home to a new home lv later, after the first boot. The newer installer's partitioner  doesn't see LVM storage containers, so has to be done manually from the commandline.

---

