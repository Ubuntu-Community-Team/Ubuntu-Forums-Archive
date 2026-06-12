---
title: "Upgrade Problems - dpkg: error processing"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by kipmoravec on 2005-11-05
I tried to upgrade from Warty to Breezy.  It took 3 days to get back to a gnome window where I am now.

I still have a problem with Synaptic Package Manager. Here is the terminal results:

Preconfigureing packages ...
(reading database ... 89407 files and directories currently installed.)
Unpacking libopenh323-1.15.3c2
(from .../libopenh323-1.5.3c2_1.15.6-1_i386.deb ...
dpkg: error
processing /var/cache/apt/archives/libopenh323-1.5.3c2_1.15.6-1_i386.deb
(--unpack)
trying to overwrite '/usr/lib/libopenh323.so.1', which is also in
package libopenh323-1.13.2
Unpacking ubuntu-docs (from .../ubuntu-docs_5.10.6_all.deb) ...
dpkg: error
processing /var/cache/apt/archives/ubuntu-docs_5.10.6_all.deb
(--unpack):
trying to overwrite '/usr/share/ubuntu-artwork/home/index.html', which
is also in package ubuntu-artwork
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
/var/cache/apt/archives/libopenh323-1.5.3c2_1.15.6-1_i386.deb
/var/cache/apt/archives/ubuntu-docs_5.10.6_all.deb

Failed to apply all changes! Scroll in the terminal buffer to see what
went wrong.


I have no idea how to fix this. 

I do know it is not a good idea to go into the file system and just delete these two files. I have already made that mistake. :???: 

Kip

---

### Post by Kyral on 2005-11-05
```
cd /var/cache/apt/archives/
```

This gets you to the package directory

```
sudo dpkg --force-install ubuntu-docs_5.10.6_all.deb
```

This SOULD force dpkg to overwrite those files...but I'm not sure of the syntax

---

### Post by kipmoravec on 2005-11-06
So I did the cd /var/cache/apt/archives

and your command did not work.  So I looked it up and believe you meant 
sudo dpkg -i --force-overwrite ubuntu-docs_5.10.6_all.deb

But that still did not work :(  It could not find the file.

But wait the file Synaptic was using was 
/var/cache/apt/archives/ubuntu-docs_5.10.6_all.deb 

the directory had 
/var/cache/apt/archives/ubuntu-docs_5.10-6_all.deb

(note the difference between the 10 and the 6)

Somebody somewhere has a typo.

sudo dpkg -i --force-overwrite ubuntu-docs_5.10-6_all.deb

Worked!

Thanks for the point in the right direction.
Kip

---

