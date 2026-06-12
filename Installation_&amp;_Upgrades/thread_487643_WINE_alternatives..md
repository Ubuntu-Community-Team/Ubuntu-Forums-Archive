---
title: "WINE alternatives."
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Roo-Kun on 2007-06-29
Hi,

I'm trying to find an alternative program to WINE and one that is free. As the moment I have it installed but I cannot access my other hard drive. (Linux is on my slave and windows on my master).

I was hoping that there was another program that I could use in replacement to wine that allows me to run programs off my OTHER HDD.

Thanks.

---

### Post by iamplasma on 2007-06-29
WINE has nothing to do with the ability to access other hard drives.  Your windows drives "should" be mounted by the OS.  That said, to get things fully working, you may need to do the following:

- If you need read/write ability for an NTFS-based windows install (which is what most windows installs are now), you may need to set up ntfs-3g.  However, that is an OS issue, not WINE.
- You'll need to tell wine's config to make your window mount point appear as a drive, so you can actually get at it.  While WINE doesn't handle the mounting of partitions, it doesn't use linux's filesystem directly either, but rather mounts specific directories as if they were drives, just like in windows.

So you'll probably want to mount your windows partition in /mnt/windows, then tell WINE to set /mnt/windows to be your, say, E:.

Unfortunately, I honestly can't give you a complete guide to how to do the above off the top of my head, but those two things are at least what you're going to have to do.

---

