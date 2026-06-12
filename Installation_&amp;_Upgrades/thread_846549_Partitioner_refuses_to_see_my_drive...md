---
title: "Partitioner refuses to see my drive.."
date: 2008-07-01
forum: Installation &amp; Upgrades
---

### Post by Zigosity on 2008-07-01
Hey there,

Trying to install 8.04 on my new machine, running a 300gig WD SATA Raptor drive. I have a 250gig NTFS windows XP partition already set up, and 50gigs of un-partitioned space for use with Ubuntu. During the installation, when I reach the partitioner, nothing comes up in the box, as if it's not detecting that my HDD is there, which is obviously a problem and I can't proceed with the install. 

Is this a known issue with my drive? Or am I just doing something horribly wrong here...

---

### Post by ibutho on 2008-07-01
Hi. When you run the livecd, go to Applications -> Accessories -> Terminal and enter
```
sudo fdisk -l
```
Post back the output.

---

### Post by avtolle on 2008-07-01
I'm going to suggest using all_generic_ide as a boot option when you boot from the Live CD. See [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) for general information on how you add this to the boot string.

---

### Post by Zigosity on 2008-07-01
fdisk doesn't return anything at all, which is very odd.

I'll try the boot option now, thanks.

---

### Post by Zigosity on 2008-07-01
The boot option fixed it, thanks =D.

---

### Post by Licurgo on 2008-07-01
Zigosity:
I suggest you to mark this post as **Solved**
Good luck into Ubuntu

---

