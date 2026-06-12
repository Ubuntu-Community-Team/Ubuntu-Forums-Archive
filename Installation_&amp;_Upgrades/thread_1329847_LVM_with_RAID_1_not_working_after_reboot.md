---
title: "LVM with RAID 1 not working after reboot"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by AMuze on 2009-11-17
Hello,

I built a new pc and decided to run a software raid 1 with LVM with 9.10 64bit. I found a nice how to on the forums: 
[https://help.ubuntu.com/community/Installation/RAID1%2BLVM]("https://help.ubuntu.com/community/Installation/RAID1%2BLVM") 
and followed it exactly except for the places where the author sets up for the raid 0 aspect.

#Edit: I should note that I am only setting this RAID 1 with LVM as a data storage volume, it's NOT my boot directory, or / etc... it's just a data space I want to get running, once it's stable I will move my /home space to it. 

After going through the tutorial it worked, I had the LVM volume under /dev/mapper/<name>. I was able to mount the volume and all looked good. I added the volume to my fstab file and rebooted the system. Upon reboot the LVM was no longer there, it was not under the mapper directory either. I ended up finding a post somewhere about needing to run some some script (maybe pvscan, can't remember), it that worked once for me. After the second reboot I could not get the LVM back.

Does anyone know where I might have gone wrong? Was I supposed to add something to a config file to have the LVMs probed automatically or the raid probed, something?

Any help will be appreciated, I'd really like to get this running, it's the last part of my new system. All-in-all the 64bit 9.10 is running great on my hardware, just need a little help to finish.

many thank,
--A

Edit: it was suggested that I check my rc.# file to ensure the servic is being started at boot time, any suggestions form the folks here?

---

### Post by AMuze on 2009-11-18
I have found that dm-mod is not being loaded, and it is actually not even in my kernel modules directory. I search on line for this and found a few others saying this is a bug. Is this in fact a module that should be present in my kernel modules dir and be able to be modprobed?

---

