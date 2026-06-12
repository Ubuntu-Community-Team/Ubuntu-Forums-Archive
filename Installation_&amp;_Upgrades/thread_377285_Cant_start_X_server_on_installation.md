---
title: "Cant start X server on installation"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by saron2 on 2007-03-05
To start off ive never even tried to instal ubuntu till this point. I am using 6.10 and am going to use a second hard drive to isntall/dual boot

once i start from the disk and go to start or install it goes through the loading screen the i get a weird blue screen sayingsomthing about X server not being able to start then i have to disable GMD or somthing like that

i read that it might have to do with my graphics card or drivers.

if it helps im using an ATI Raedon X600 and i have a tv tuner (ATI tv wonder elite but that shouldnt affect it)

any help :confused:

---

### Post by taurus on 2007-03-05
You should try the alternate CD then.

[http://ubuntu-releases.cs.umn.edu/edgy/](http://ubuntu-releases.cs.umn.edu/edgy/)

---

### Post by beast.dk on 2007-03-06
Have the same problem - but have also found a solution (not a good one)

I installed it to my PC and to be one the safe side I took the SATA cable away from the 2 disk that I use for MS Windows as a security meassure. Installed ubunto and every thing worked. Then I mounted the 2 missing disk and had the same problems. When I uninstall the disks it works again. Have looked into it from the terminal and the log says that it is missing fonts from /usr/share/x11/fonts (fonts folder does not exist with all disk mounted).

What can be wrong?

---

### Post by beast.dk on 2007-03-07
Nobody have seen this before ?

---

### Post by frozinfire on 2007-05-29
You probably already solved the problem, but maybe someone else can use this info. 

On the command line, type: 
sudo dpkg-reconfigure xserver-xorg

When you're asked about an auto detection for the video, select "no" and choose "vesa" on the list.
Go through the rest of the options, and choose to save the configs. When you're returned to the command line, type:
sudo killall -9 Xorg

Then, when you type "startx" and hit enter, everything should be okay.

I hope that's helpful!

---

