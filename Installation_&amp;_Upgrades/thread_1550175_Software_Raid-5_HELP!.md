---
title: "Software Raid-5 HELP!"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by fattyl on 2010-08-10
I have an HTPC that was giving me insane amount of problems after 3 months of good use. 

1x 250gig Samsung Drive (OS Drive)
3x 1TB Western Digital Caviar Green (Raid-5)

In 9.10, the raid was working fine. I decided to fresh install Ubuntu 10.04 and I can't seem to start the raid array. In Disk Utility, the array shows up but when I try to start it I get the error "Not enough components to start the array"

I've tried to assemble the array using mdadm and the following

mdadm --assemble /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdd1

This returns the following error mdadm: failed to create /dev/md0

I have no idea what to do now, and unfortunately I don't have any backups :(

Any help is appreciated.

---

### Post by fattyl on 2010-08-10
Alright I solved this, thank god. Here is how for future reference.

When trying to find the uuid of the drives, I typed blkid and nothing would show up.

sudo blkid 

showed the uuid then i used

sudo mdadm --assemble --uuid=enteridhere

then I managed to mount it and get it working.

thanks!

---

