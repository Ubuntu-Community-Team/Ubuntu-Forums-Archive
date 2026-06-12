---
title: "Hard RAID config for fresh install"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2012-09-21
Hey All, 

I'm going setup my first box with a hard RIAD controller. What I don't know is how/when/where to configure this. I'm a RAID noob.

Will I get a prompt from the install CD? IS there a good guide on this. I simply want to do a straight mirror, RAID 1 right?

Am I correct in understanding that the OS will simply treat this as 1 drive?


THANKS

---

### Post by darkod on 2012-09-21
If you will use only ubuntu (not dual boot) it's much better to use software raid.

But the choice is up to you. Depending on the controller, there will be a combination of buttons you need to press at boot to enter the controller bios. In there you will set up the raid array. The manual of the controller should have more details of the process.

After that the OS sees one disk. It might be better to use the alternate cd since it offers better raid support, but in some cases the live cd might work too.

---

### Post by wlraider70 on 2012-09-21
Ok that mkes since on the raid config. 

I've never heard that soft was better could you Elaborate on why?


Thanks for the info.

---

### Post by darkod on 2012-09-21
When using bios raid or fakeraid (without dedicated controller) it's actually using the CPU and memory for the raid too, so linux software raid is said to work better compared to motherboard raid.

In your case with dedicated controller, the cpu and memory on the controller will do the job, so that should be OK. But many people find problematic if the controller dies. Don't think only about the option of a disk dying on you. You replace it, the array syncs, and that's it. But what if the controller dies? The array is created in a way that only the same or very similar model of a controller can make it run correctly again, possibly losing all your data if you can't make it run again.

With linux software raid, simply connect the disks on any linux machine and the mdadm package is still running the array. If you use RAID1 you can even connect only one of the disks to another ubuntu machine and all data is there untouched and accessible.

---

