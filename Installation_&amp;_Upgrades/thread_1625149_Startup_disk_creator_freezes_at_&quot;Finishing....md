---
title: "Startup disk creator freezes at &quot;Finishing...&quot; stage"
date: 2010-11-18
forum: Installation &amp; Upgrades
---

### Post by QwUo173Hy on 2010-11-18
1GB Dane-Elec stick is what I'm using. 

The only thing out of the ordinary I noticed is that when I clicked "Erase disk" I ended up with a choice of two: /dev/sdc (with no indication of free space but a capacity of 983.0MB), and /dev/sdc1 which showed 288MB free before I erased it and a capacity of 980.4MB.

This app has never worked on any system I've tried it on, but this particular machine is an LTS (10.04) with recent hardware so I'd like to get it fixed if possible.

Any help is appreciated,
Jarlath

---

### Post by GeoffreyBernardo on 2011-08-13
I have the same problem.

---

### Post by GeoffreyBernardo on 2011-08-13
The KDE version of the program worked. I first removed the gtk version (usb-creator-gtk), then installed the KDE version (usb-creator-kde).

---

### Post by westie457 on 2011-08-13
> **jarlath said:**
> 1GB Dane-Elec stick is what I'm using. 

The only thing out of the ordinary I noticed is that when I clicked "Erase disk" I ended up with a choice of two: /dev/sdc (with no indication of free space but a capacity of 983.0MB), and /dev/sdc1 which showed 288MB free before I erased it and a capacity of 980.4MB.

This app has never worked on any system I've tried it on, but this particular machine is an LTS (10.04) with recent hardware so I'd like to get it fixed if possible.

Any help is appreciated,
Jarlath

Hi, as far as I have been able to work things out when using Star up Disc Creator what happens is this.....

1 Erasing the disc automatically sets a MBR on the stick (/dev/sdc)

2 Creates a partition for the ISO (/dev/sdc1). The differences in the numbers is caused by human-counting and machine-counting. There is a whole topic explaining these somewhere in 'Wikipedia'


As for the 'freezing' that might be caused by a dodgy usb stick or the process of creating a persistence file.

---

### Post by QwUo173Hy on 2011-08-15
Thanks for that Westie. I'm on 11.04 now and I just tried it again. It finishes the process but fails to boot it reports an error to do with a definition of a UI or something but at this point I give up on the app.

Geoffrey, I might try the KDE version since i happen to have it installed.

Thanks for all your help!
Jarlath

---

### Post by GeoffreyBernardo on 2011-08-15
> **westie457 said:**
> 
As for the 'freezing' that might be caused by a dodgy usb stick or the process of creating a persistence file.
  I do not agree on this point, because one of my usb sticks is more than five years old and the other one maybe six months, and they both experienced the same freeze. Also, I did not specify a persistence file. Also, the kde version worked on the old stick.

If one could step through the source code while it executes one could probably see what goes wrong.

---

