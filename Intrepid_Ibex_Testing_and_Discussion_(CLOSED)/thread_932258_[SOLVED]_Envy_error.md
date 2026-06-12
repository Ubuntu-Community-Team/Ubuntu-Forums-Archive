---
title: "[SOLVED] Envy error"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sandsound on 2008-09-28
Been trying to install Ipex (Alpha 4, 5 and 6) on my computer, and so far I haven't had any luck with the Nvidia driver.
I have tried to reinstall several times with both 173 and 177, so I thought i'd try out Albertos EnvyNG (the one from the Ipex repositories), but here I get a strange message when I try to run the "envyng -t" in a terminal :

TypeError: list indices must be integer

I get the same message if I try to uninstall with "envyng --uninstall-all"

My card is a 7950 X2 and it works fine in Hardy.

btw... I'm a little bit confused about the new Xorg (among other things :) ), does it support the new 177 driver or not ?

---

### Post by ronacc on 2008-09-28
I don't know about envyNG I haven't had to try it , the one from system>administration>hardware drivers works fine for me with my 7600gs , so yes the 177 driver works with intrepid , I think the one direct  from nvidia needs a little editing in the script to compile , I don't know if the latest version corrects that but the one available in system>administration>hardware  works fine .

---

### Post by Sandsound on 2008-09-28
> **ronacc said:**
> the one from system>administration>hardware drivers works fine for me with my 7600gs

I just get a "no screens found" when I try the system>administration>hardware drivers, so I must be doing something wrong, that's why I thought Envy might do the trick.

---

### Post by ronacc on 2008-09-28
check synaptic to see if you have all of the nvidia-177 and nvidia-glx-177 packages installed , if not install them ,if they are already installed or else after you install them reinstall which ever linux-image you are using and that should build the module for you , there are several threads on this use the search this forum box to find them , I don't have time right now to search them for you , read them first before doing what I said, I'm working from memory and may have missed a step .

---

### Post by Sandsound on 2008-09-28
> **ronacc said:**
> check synaptic...

I have been trying everything I have read in other threads (lost count of how many :-) ), so I have more or less accepted that I just can't get it to work, after all... I still have my good "old" 8.04 on a separate disk.

I admit that I'm no expert, but I just thought that the error I got from envyng (TypeError: list indices must be integer) could be related to my failed attempt with installing the nvidia driver ?

---

### Post by ronacc on 2008-09-28
I have no more ideas ,except a completly clean reinstall , you don't say how you installed the alphas you tried . I have done clean installs of 1,2,3 using the alternate installer upgraded to 4 and 5 and a clean install from the desktop livecd of A6 and only had some minor problems back around 3 when the drivers were laging a bit. did you see the post about removing old modules ? [http://ubuntuforums.org/showpost.php?p=5670471&postcount=74](http://ubuntuforums.org/showpost.php?p=5670471&postcount=74)   .

---

### Post by Sandsound on 2008-09-28
> **ronacc said:**
> I have no more ideas ,except a completly clean reinstall , you don't say how you installed the alphas you tried.

I have tried Alpha 4, 5, 6 and also the UbuntuStudio Alpha 6.
Each install was a clean install on a separate disk and with the alternate installer.
Alpha 4 and 5 I only tried once, but I have tried Alpha 6 with different approaches now five times.
The default (free driver) works fine on all installs, but once I install the restricted driver :confused:

I have even tried using a older kernel, (2.6.26), and all thou it got rid of the annoying "EH pending after 5 tries, giving up" message (what's up with that btw?) id did not solve my problem.

That is why I wanted to try EnvyNG, but I keep getting this strange "TypeError" whenever I try run or uninstall it.:(

---

### Post by ronacc on 2008-09-28
I am at a complete loss here , I hope someone chips in with some new Ideas for you to try I know some people have had to adjust their xorg.conf to get things just right but I havent seen anything about the driver not installing at all . one last question just to be through , you do have the build essentials and headders installed don't you ?you shouldnt need those with the repo packages but like I said I'm at a loss .

---

### Post by Sandsound on 2008-09-30
PROBLEM SOLVED ! :D

It seams that Ipex (or one of it's components), can't figure out what to do when you use two cards, at least thats what I understood from another thread in the forum.
My old xorg.conf had no Busid in the Device-Section, and since I have one of those "double" cards (a 7950 X2), I never thought of it as two separate cards :oops:

A simple lspci showed that I had Nvidia on PCI:4:0:0 but also on PCI:5:0:0

So now it works \\:D/

EDIT: actually I never got EnvyNG working, but at least I got the Nvidia driver working.

---

