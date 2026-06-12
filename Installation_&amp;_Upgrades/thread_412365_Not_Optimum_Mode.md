---
title: "Not Optimum Mode"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by isamudysan on 2007-04-18
hey all,  i've a got problem that i can't seem to resolved.  i solved it while installing fc6; but, fc6 was too much of a hassle every time i wanted to do something.  so, i thought i try out ubuntu.  this is my second re-installation of ubuntu.  the first went well but i screwed up something when i tried to install the new nvidia drivers via the envy program.

anyways, i want to try and follow the instructions from this post, [http://ubuntuforums.org/showthread.php?t=336412](http://ubuntuforums.org/showthread.php?t=336412), but when i do try and execute the installation nvidia tells me that i'm in runlevel 1, and that i should be in runlevel 3 to install nvidia drivers.  oh, yeah, since i couldn't get into x server, i had to choose to boot into recovery.

right now i'm stuck at figuring out how to get pass the "not optimum mode" when starting x server. when i fought passed it in fc6 it was thru the installation of the new nvidia driver.  i hope that's the same resolution with ubuntu.  please help.

thanks!!

---

### Post by BoneKracker on 2007-04-18
Why don't you just install the normal way and then add the drivers?  There is no reason you shouldn't be able to get into the default runlevel. Fix that before you worry about getting the latest and greatest nvidia drivers.

---

### Post by isamudysan on 2007-04-18
i've installed it the "normal way" already.  when it boots into x server, i see nothing but garble junk --  lines all over the place -- and my monitor pops up a "not optimum mode" error message.  basically, i'm stuck can't get into x server, can't log in, can't do jack!

by booting into recovery is the only way i can do command lines for now.  again this is runlevel 1 - single user mode.  i need to be in runlevel 3 multi-user mode to install this new nvidia driver.  there's gotta be an easier way to get passed this.

---

### Post by isamudysan on 2007-04-18
thanks for those of you who dropped by and took your time to look at my problem....however, i solved the problem....using "vesa" isntead of the "nv" driver....:guitar:

---

