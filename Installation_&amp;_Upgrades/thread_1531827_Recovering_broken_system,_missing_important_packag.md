---
title: "Recovering broken system, missing important packages"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by E-P on 2010-07-15
Well I did a real fool mistake. I deleted some packages that I knew I won't need and was stupid enough to choose the "complete removal". Now, it deleted some important packages and the OS doesn't start any more. I have 10.04 which I updated few days ago from the previously newest version.

When I start the computer it does not go automatically to the Ubuntu graphic interface but "stucks" to the logging logo and there opens the little terminal window on the upper left-hand side corner. I tried "sudo startx" but it said "Fatal Server Error" etc. etc. etc.

How can I recover the system back as I do not wanna lose the files I have there? I tried to install ubuntu again, from the working one recover the files and then completely format and reinstall everything. Anyway, the installation didn't work. Not sure why, maybe I have to try another cd and try again. Also, if I am not wrong there might be a problem trying to copy files from the other part (due to limit rights), is there anything to do about that?

Anyway, I think easiest would be just to get the system recovered and last option, stick my hard drive to a computer in my working place and copy the files to a DVD by that and then format and reintall everything.

Advices and help MUCH appreciated.

Cheers,
E-P

---

### Post by nothingspecial on 2010-07-15
Try mounting the stuffed installation from the live cd and copying the files to some removable media.

Youknow, you should have backups of any important stuff.

But anyway, if you boot from the live cd, you should be able to mount the partition from the places menu, you may have to type gksudo nautilus to copy the files.

---

### Post by pastalavista on 2010-07-15
You can also do a re-istallation from the live CD and at the partition editor (in manual mode) uncheck the 'format' boxes,use all the Ubuntu partitions and instal with the same username. You'll need to do updates again. You won't lose any files but always back-up anyway just in case.

---

