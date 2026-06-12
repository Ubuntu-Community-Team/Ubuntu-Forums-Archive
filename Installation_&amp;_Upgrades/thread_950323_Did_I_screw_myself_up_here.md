---
title: "Did I screw myself up here?"
date: 2008-10-17
forum: Installation &amp; Upgrades
---

### Post by StaticSpaz on 2008-10-17
So when I was choosing partition sizes, Ubuntu wanted 88GB for it's section... is this going to take a while?
thanks :)

Also:
Is there a Ubuntu Partitioning tutorial somewhere?
I want to have partitioned sections for:
Windows Vista
Ubuntu
FAT 32 (All my files and crap that vista and ubuntu will access.)
and this small memory helper thing that i heard about

---

### Post by frankleeee on 2008-10-17
> **StaticSpaz said:**
> So when I was choosing partition sizes, Ubuntu wanted 88GB for it's section... is this going to take a while?
thanks :)

Your question needs more information, are doing a dual boot and what is your total memory. Personally since I am only using 1 distro and have only about 20 gig altogether when I install I let it overwrite the whole thing, I never need to save anything due to having 3 different computers. You might be limited in time by how fast your cpu is what is your computer setup.

---

### Post by StaticSpaz on 2008-10-17
Yes i want to dual boot. 
I want to keep vista on here, but have ubuntu also.
I have 4BG of RAM too

---

### Post by Partyboi2 on 2008-10-17
> **StaticSpaz said:**
> So when I was choosing partition sizes, Ubuntu wanted 88GB for it's section... is this going to take a while?
thanks :)
If you mean is it going to take long to install,shouldn't do., setting up partitions does not take long at all.

Edit: here is a link on how to dual boot vista/ubuntu
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by frankleeee on 2008-10-17
> **StaticSpaz said:**
> Yes i want to dual boot. 
I want to keep vista on here, but have ubuntu also.
I have 4BG of RAM too

I have never used a MS setup, and have only dual booted with Linux distros. I don't know where your at in the process, but if you haven't started to install the Ubuntu distro yet if it was me I would make sure that the 88 gig is not all your memory, with 4 gig of ram it probably isn't in that a system with that much ram would probably have a large hard drive memory. Just make sure you know what your doing.

---

### Post by Pumalite on 2008-10-17
Here is another:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by StaticSpaz on 2008-10-17
Ok, well i went to that link you posted above, and learned all about partitioning, and got a good sense for it. I already knew most about it, but it made things more clear. 
So i guess my question is, how much space should i give Ubuntu on my HDD? 
Also, i read that you can, instead of having a windows, FAT32, and ubuntu partitions, you can have a windows one, and then a giant ubuntu one that has all the files and stuff, but windows can still access files on ubuntu's partition. Is this an easy thing to do, or should i just stick with a windows, FAT32, and ubuntu partitions seperate?

Sorry one more thing!!!
Can i resize and change around partitions in the Ubuntu installer? Or should i do this in vista first, then install ubuntu.

---

### Post by LehFreakshow on 2008-10-17
> **StaticSpaz said:**
> Ok, well i went to that link you posted above, and learned all about partitioning, and got a good sense for it. I already knew most about it, but it made things more clear. 
So i guess my question is, how much space should i give Ubuntu on my HDD? 

I'd say about 8-10 gb for a comfy install. (By comfy, i mean it's fast and you can actually install things)
> **StaticSpaz said:**
> 
Also, i read that you can, instead of having a windows, FAT32, and ubuntu partitions, you can have a windows one, and then a giant ubuntu one that has all the files and stuff, but windows can still access files on ubuntu's partition. Is this an easy thing to do, or should i just stick with a windows, FAT32, and ubuntu partitions seperate?

I have never heard of anything like that. But then again, I'm not good with filesystems.
> **StaticSpaz said:**
> 
Sorry one more thing!!!
Can i resize and change around partitions in the Ubuntu installer? Or should i do this in vista first, then install ubuntu.
You can edit patitions from the live CD, if that's what you mean.
Just open up the Terminal and type gparted

You should get a partiton manager.
However, i have no idea how to use gparted. (But it's there)

---

