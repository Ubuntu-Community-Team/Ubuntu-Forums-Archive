---
title: "free disk space by symlink system directories?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by perstromgren on 2010-04-30
I cannot upgrade to 10.4, because my EEE 901 has a too small "system disk", 4GB. However, I do have enough space on my slower 16GB SSD disk. Can I move some recommended system directory there temporarily and symlink from the root disk? Would the upgrade data itself be a good candidate, perhaps?

The work around would be to do a clean install of the new version, but I rather not, as I have some tweaking to do afterwards in that case.

As it is now, I have 700MB of free space, and need about 1.4GB, if I'm not mistaken.

Per.

SOLVED: I downloaded the alternate CD image to my bigger disk and upgraded from ther. Works nicely. / Per

---

### Post by ssam on 2010-04-30
if you symlink the /var/cache/apt/archives/ directory to another disk that will help, but its had to know if it will be enough.

see if you can clear any space by deleting things like the gnome thumbnail cache ~/.thumbnails/ and maybe your browser caches as well.

or try uninstalling some large packages, and put them back after the upgrade. in synaptic you can set it to show the installed packages, and then sort by install size.

---

### Post by rositak on 2010-04-30
Hi,
 
I'm running into the same issue. Lack of disk space. I did run sudo apt-get clean and removed packages. So far no luck.
 
Unfortunately installion with USB-boot fails as well.

---

### Post by perstromgren on 2010-04-30
> **ssam said:**
> if you symlink the /var/cache/apt/archives/ directory to another disk that will help, but its had to know if it will be enough.

see if you can clear any space by deleting things like the gnome thumbnail cache ~/.thumbnails/ and maybe your browser caches as well.

or try uninstalling some large packages, and put them back after the upgrade. in synaptic you can set it to show the installed packages, and then sort by install size.

Thanks, these seems to be good ideas, all of them! 

I will try them over the next few days and report back here for the benefit of other readers.

Per.

---

