---
title: "Migrating existing LVM to Ubuntu"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by ac1115 on 2010-03-28
Hello all, I want to upgrade from another distro to ubuntu server for a few reasons.  The only problem is I have a lot of data that needs to survive.  here is how my computer is setup.

I've 5 drives on the computer, 

A-  10gb drive for OS and swap only, no data

B,C,D,E -  4x 500 GB drives in a LVM.  they make up one large drive with xfs and this volume has about 1.2 TB of data.  there is nothing fancy on it, no encryption and no software raid

of course the little 10gb drive can be formatted no problem, but the LVM needs to be migrated over intact.

Is this possible?  I'm trying to get a complete grasp before I do this ;)

Thanks ahead of time!

---

### Post by stlsaint on 2010-03-28
If your lvm setup is strictly DATA and holds not boot files, root files or anything required from the os than simply installing ubuntu to the os and ubuntu should mount those drives as is. Again i sugggest doing further research before making this move as i have never done this specific procedure before...just giving insight on what i know of ubuntu. Just ensure to NOT touch those hdd during install. Make sure that you do a manual install and TELL ubuntu where to install to. again do research for better more solid answers.

---

### Post by ac1115 on 2010-03-28
the LVM volume is strictly data, 100%.   

everything related to the OS, boot, and swap is on the little 10gb drive

---

### Post by ac1115 on 2010-03-29
so I looked it up a little more, it seems I want the vgexport and vgimport commands.

export it,  install ubuntu on the 10gig, then import it

can anyone with a bit more knowledge on this confirm before I move on?  

Thanks :D

---

### Post by Nirami on 2010-03-29
I'm in the same boat, about to transfer a LVM on pair 500GB+1TB pure data disks to a new system. I also came across the [export and import commands]("http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html"). I'd still like a few more data points before going through with it though.

---

### Post by ac1115 on 2010-04-05
well I should update this since I did it.  incase anyone else wanted to know.

the vgexport and vgimport did the trick fine.

I first exported them , 
then I reinstalled the system,  *taking extra care not to overwrite the LVM partitions!*, 
and then finally I imported the vg into the new OS.  

Very easy

---

