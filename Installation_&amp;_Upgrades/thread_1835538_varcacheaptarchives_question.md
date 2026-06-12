---
title: "var/cache/apt/archives question"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by tpprynn on 2011-08-29
After a couple of years of long-winded fussy distro-hopping and repeated Updates I recently started to saved the contents of var/cache/apt/archives when using Ubuntu, Debian or Mint. Seems to work to paste the contents back in to a fresh install and minimises the amount of updating and fresh downloading of programs. The last time I've done this with Ubuntu 11.04 it seems Synaptic won't fetch the .deb files from this folder and tries to download them afresh. When I looked the files all had the locked symbol on them. I don't remember if it was like this before or if I've got one step of this wrong or forgotten it. It's easier with Debian as the pasted in files just seem to get used by Synaptic and the Update Manager when I start reinstalling stuff.

I imagine someone here is fluent with doing this or has a better method or will know what I need to do to make these files useable - some permissions issue that's a bit muddy in my understanding at a guess.

Thanks.

(Ubuntu 11.04 64 bit/ Amd 3 ghz/ Debian 6.01)

---

### Post by ajgreeny on 2011-08-29
I still do exactly what you are talking about by copying and pasting all the contents of /var/cache/apt/archives (except for the **partial** folder and **lock** file) from one to the other of my old laptop and my netbook, both of which run Lubuntu 11.04.  It works perfectly, so I don't know what is happening in your case to give you the problem.

How did you copy the files; did you use a CD or a USB flash drive?

Now those .deb files are in the cache please navigate to the folder in terminal and use command```
ls -lh
```to check the permissions, which should be something like 
```
-rw-r--r-- 1 root root 8.8K 2011-08-16 16:14 firefox-branding_6.0+build1+nobinonly-0ubuntu0.10.04.1~mfs1_i386.deb
```

PS:  I used to use aptoncd for the same thing, but it is much quicker and easier to copy the .deb files to a flash drive and paste them with terminal.

---

### Post by tpprynn on 2011-08-29
I paste the files in a probably cackhanded manual way from a memory stick, opening nautilus as root with gksu nautilus. What do you write in the terminal? 

I may have copied the lock file too last time, maybe that's a mistake.

Thanks.

---

### Post by ajgreeny on 2011-08-30
> **tpprynn said:**
> I paste the files in a probably cackhanded manual way from a memory stick, opening nautilus as root with gksu nautilus. What do you write in the terminal? 

I may have copied the lock file too last time, maybe that's a mistake.

Thanks.
Maybe the lock file is the problem, so try removing it with **gksu nautilus** if you want to.  I have no idea what it actually does, but presumably it does what it says in its name.

The command I use is to get the .deb files on USB is ```
cp /var/cache/apt/archives/*.deb /media/integral/packages/
```my flash drive always mounting at **/media/integral **as I have labeled the partition on it "intrgral", and I have made a folder on that called "packages" just to save too much confusion.

To get those files on to the system of the second machine it is ```
sudo cp /media/integral/packages/*.deb /var/cache/apt/archives/
```It needs sudo as the /var folder is a root system folder.

---

