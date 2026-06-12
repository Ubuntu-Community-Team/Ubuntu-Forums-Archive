---
title: "Serious problem with installation"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by Fugazii on 2006-08-26
Hi there Guys!
I wanted to check Ubuntu OS. I started to download Ubuntu 6.06. Burned CD, then i booted it. When wanted to install, console gives me something like that:

""Please append a correct "root=" boot option
kernel panic - not syncing : VFS : unable to mount root fs on unknown-block""

First thought . Kernel panic.... uhhhh Not good ^^
Here is my specification of my notebook.
Asus A6rp-AP002H Model

Intel® Celeron® M 1,6 GHz
512 MB DDR2
ATI Xpress 200M
ST 80G 4200 RPM

I tried to run with ' live acpi=off ' becuase with normal start with 'Start or Install' kernel unpack but then my dvdrom stop and hard drive too, i love to see black sreen =D
When i typed in console command ' install ' i got a error with my processor that i got 1465403MH? LoL then installer started to load 'HP'? what is this? then everything stops ehhh =/

In my home PC i got Gentoo . I booted it from cd on my notebook everythink started up, funny it is? =D . Gentoo got better Installation than Ubuntu? i dont belive it!. I wanted to install Ubuntu On notebook to check it preformance. I checked BIOS. Updated it. Hmmm any others idea? OR maybe i run with dma=off ? =oo . Gentoo starts normal, SuSe 10.1 same on my notebook. I won't give up with this!!! =). ANy ideas? =| I will seek for Help =). Now its Your Time to shine......

---

### Post by Fugazii on 2006-08-26
sry i get message like 'hpet' not HP . Sry my mistake

---

### Post by mario_7 on 2006-09-05
I also have this notebook but without H at the end of the model name (without preinstalled Windows :) )

There is one solution: press F6 and to the standard command of Start and Install Ubuntu add acpi=off - it worked for me.

After istallation you will have to run ubuntu's kernels with acpi=off, the only solution for that is to configure kernel by yourself to have acpi and everything else. If you want I could upload my kernel config for you :)

After installation you will notice, that there is no sound... Here is my Alsa bug-report [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2320](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2320) it should help you.

---

### Post by mario_7 on 2006-09-05
hmmm... same post has been sent 3 times :/

---

### Post by mario_7 on 2006-09-05
hmmm... same post has been sent 3 times :/

---

