---
title: "Questions before install"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by DRF on 2005-06-17
Hi, not sure exactly where in this forum this belongs but this sounds like the right category roughly.
I currently Dual boot Debian and Windows 2k using Lilo. However after getting a little fed up of some of the technical side of things with debian and looking for something thats a bit more user friendly (but retaining the good points of debian) I came across Ubuntu and I've used the live CD and quite impressed. Seems like it could save me a lot of effort and be a lot more friendly to use. However there are a few things I liked on debian and would like to know how easy they would be to setup in ubuntu.

1. Is the dual boot installation easy and what program does ubuntu use for dual booting? (With debian it was an option from the install menu to install LILO and LILO itself detected the other partitions and OS's to add to the boot menu)

2. I liked to occasionally change window managers and have almost allways had 2 or more windows managers installed and used gdm/kdm login prompts which allowed you to choose which window manager to loadup. Is this easy to do in ubuntu? (I doubt I will use it much looking at the nice ubuntu setup but it's comforting to know that if I get fedup of gnome I can mess around with kde for a month without much hassle)

3. The package database didn't seem as large as debians and there were a few packages that I would of liked to use, again I could probably get the packages from the websites but I was wondering because of the ties ubuntu has with debian if there are many problems with installing debian packages, or indeed if it's common place (or advised against) to link in with the debian package database as well as ubuntu's own. (Any advice here most welcome as would love to keep the ease of use that comes with such a large package database)

4. I have an AMD64 CPU and would like to install the AMD64 version of ubuntu but I'm curious as to how easy or hard it is to run 32bit programs on that version when needed. (Don't want to recompile a load of apps or have to find new apps because there is no AMD64 binary/package etc)

I think thats most of my questions (though I'll probably think of more this should be enough to put my mind at ease and know what to expect within the install)

Thank you for any help and re-assurance/advice.

Daniel

---

### Post by blind0wl on 2005-06-18
> 1. Is the dual boot installation easy and what program does ubuntu use for dual booting? (With debian it was an option from the install menu to install LILO and LILO itself detected the other partitions and OS's to add to the boot menu)

I installed recently and it picked everything up with no problems, Ubuntu uses GRUB (which in my opinion is better than LILO)

> 2. I liked to occasionally change window managers and have almost allways had 2 or more windows managers installed and used gdm/kdm login prompts which allowed you to choose which window manager to loadup. Is this easy to do in ubuntu? (I doubt I will use it much looking at the nice ubuntu setup but it's comforting to know that if I get fedup of gnome I can mess around with kde for a month without much hassle)

There is a release called kubuntu, which is kde orientated, but that doesnt stop you from installing Ubuntu and apt-get kde.  GDM will pick up the extra WM, no problems if you set it up correctly....alternatively, theres no stopping you installing kdm and making it the default.

> 3. The package database didn't seem as large as debians and there were a few packages that I would of liked to use, again I could probably get the packages from the websites but I was wondering because of the ties ubuntu has with debian if there are many problems with installing debian packages, or indeed if it's common place (or advised against) to link in with the debian package database as well as ubuntu's own. (Any advice here most welcome as would love to keep the ease of use that comes with such a large package database)

Ubuntu does have a variance of the debian repositories, but there are ports of debian released software available, however its the usual, do it at your own risk.

> 4. I have an AMD64 CPU and would like to install the AMD64 version of ubuntu but I'm curious as to how easy or hard it is to run 32bit programs on that version when needed. (Don't want to recompile a load of apps or have to find new apps because there is no AMD64 binary/package etc)

I dont have much experience with the 64bit version, however in general 32bit is backward compatible with 64bit architectures.

HTH

Cheers

Blindy

---

### Post by DRF on 2005-06-18
Thanks, I'll give it a go then. (If it doesn't work out can allways go back to debian).

Hopefully I'll figure out the differences as I go along.

Daniel

---

### Post by irusun on 2005-06-18
[QUOTE=DRF]4. I have an AMD64 CPU and would like to install the AMD64 version of ubuntu but I'm curious as to how easy or hard it is to run 32bit programs on that version when needed. (Don't want to recompile a load of apps or have to find new apps because there is no AMD64 binary/package etc)[/QUOTE]

I don't have any personal experience with AMD64, but from what I gather, unless you're trying to break the 3-4GB RAM barrier, or just like to be on the bleeding edge, there's really not much to be gained by going with the 64bit version.  It seems like many people use the 32bit Ubuntu even if they have an AMD64 because package support is still better on 32bit at this time.  Something to consider.

---

### Post by DRF on 2005-06-19
Well I went for the plunge and so far everything seems to be working ok. I opted for 64bit in the end. The reasons being that I checked the package reposities to ensure that the packages I really wanted were available for the 64bit version and as I'm dual booting I can afford to switch OS's for anything that ubuntu 64bit has trouble with. (Shame to have a 64bit CPU and not use it)

Getting ubuntu to work on my computer is a lot easier than debian has been in the past  :smile: 

Thanks for your help, only comment I've got is that it would of been nice for a graphical app to modify the fstab file for the other partitions or some auto-detect feature for them. I'm used to modifying fstab in debian so wasn't a big issue for me but someone new to linux and dual booting might find it a bit harder.

Daniel

---

### Post by blind0wl on 2005-06-19
Your welcome...I dont remember having to edit any fstab files, or grub entries with my laptop after install.  :? 

Have fun playing.

---

