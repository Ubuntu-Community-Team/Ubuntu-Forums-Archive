---
title: "[Solvd]How to make var folder lighter?"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by Ariya243 on 2012-08-10
The var folder is getting full all the time and I haven't installed much at all. the cache in var is now totaling 400MB and all of them are .deb files. Once the applications are already installed and running, why is this var holds them. The total of var folder is 800 MB, a way too much. 

How can I safely delete these files. The .deb files won't be working anyway, after they had been installed, either by me or by updating.

I am in 2 minds to delete as much as I can, but wait for few expert advice.

Thanks!:D

---

### Post by Moif_Murphy on 2012-08-10
I suspect you need to run:
 
apt-get clean
 
:)

---

### Post by Ariya243 on 2012-08-10
I clicked on one .deb file, which pulled in the Software Center to install it, but it is installed, so I cut and pasted the all the .deb files in another partition. Either I have to manually delete all old files or mount /tmp, /var/tmp and /var/log as mount points, so when I reboot, those would be cleaned.

I usually check any file is linked to some other file. It can be seen by reading it in Gedit. If not, I'd delete that. But, only after thoroughly checking any linking or dependency. I find Linux internals quite interesting, though I am not a geek.:) 

I found the proc folder to be 1.1 GB, but all that is only one file inside, which is called kcore and has 1.1 GB in it. I couldn't find a application yet to open and read it, but let's see in the future.

Take care!:)

---

