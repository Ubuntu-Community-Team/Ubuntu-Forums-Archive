---
title: "Help with Ubuntu 8.04 and Vista on RAID 0"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by mike29488 on 2008-08-31
Hello all,
I am new to Linux and I'm wanting to Dual Boot Vista and Ubuntu 8.04. (Mainly concentrating only Ubuntu at the moment)  This is what i've got and what i'm trying to do.

- 2 250GB SATA RAID 0
- Using Alternate Disk
- I want to have 100GB total drive space for Ubuntu, the rest for Vista

I have checked the forums and found this site thanks to Taxman415a

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I'm still having some issues though.  I get confused on the "Partitioning the Disk" section, steps 5 - 8.  

This is what I've done:

*First* for main
- I make 2 partitions both 50GB each.
- Next, set them to "Primary".
- Then, choose "Beginning" as location.
- Then, set the "Use as:" to "physical volume for RAID".
- Last, set "Bootable flag:" to "on".

*Then* for swap 
- make 2 more partitions both 3GB each (since i have 2gigs of ram 2x1.5=3 as step 5 stated).
- Next, set them to "Primary".
- Then, choose "Beginning" as location.
- Then, set the "Use as:" to "swap area".
- Last, set "Bootable flag;" to "on".

*Then*
- Select "Configure software RAID"
- Then choose "Create MD device".
- Choose "RAID0"
- Then select both "/dev/sda1" and "/dev/sdb1" then continue.
- Then, choose "Finish"

*Last* 
- Select the 100GB partition 
- Then, set "Use as:" to "Ext3 journaling file system".
- Then, set the "mount point:" to "/" (root i guess)
- Next, select "Done".
- Lastly, select "Finish partitioning and write changes to disk"

Everything installs fine up to the GRUB.
I get an error "Executing 'grub-install (hd0) ' failed" when configuring GRUB.


What am I doing wrong?


Any help is greatly appreciated!!!

---

