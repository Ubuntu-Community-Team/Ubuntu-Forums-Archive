---
title: "Installing Ubuntu 11.04 64bit Server Softward Raid, Can not set Bootable Flag"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by Mad Professor on 2011-05-28
Good Day All.

As per the title I am trying to install Ubuntu 11.04 64bit Server, in Raid-1 using the details found here: [https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html)

I 1st tried the above guide in VirtualBox, and had no problems. 

I then tried it again on my server, but I get as far as trying to set Bootable Flag from off to on.

Each time I try it just stays off.

Can you please advice me?

Thanks for your time. 
 
Best Regards.

---

### Post by DanglingPointer on 2011-10-06
I'm having the exact same problem but with RAID0 of 8TB total and installation failed.  Spent friggin hours trying to get my head around it.

What I find weird is I remember doing it 2 weeks ago for an old Pentium 4 PC with 2 80GB disks and it worked.

Is there a size limit to what mdadm RAID0 can handle?  What is your software RAID size?

Mine is 4x2TB.
4GB on each for total of 16GB --> swap area in RAID0
2TB on each for total of 8TB --> ext4 journaling RAID0

---

