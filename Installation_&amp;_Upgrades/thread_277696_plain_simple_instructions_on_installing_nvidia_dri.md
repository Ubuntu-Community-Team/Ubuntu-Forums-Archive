---
title: "plain simple instructions on installing nvidia drivers."
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by franpa on 2006-10-15
can someone provide me with instructions that detail installing nvidia drivers on ubuntu 6.06 lts x86

these instruction should also include all pre-requisites such as packages etc. that the installer depends on.

---

### Post by aysiu on 2006-10-15
**Step 1**:
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

**Step 2**:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by franpa on 2006-10-15
OMG, something that is actually helpful... thank you very much.

---

### Post by aysiu on 2006-10-15
One of the main reasons I switched to Ubuntu from Mepis was the documentation.

---

### Post by franpa on 2006-10-15
how do i test if i have them installed? (i got the nvidia logo...)

---

### Post by aysiu on 2006-10-15
If you got the logo to appear when you get to the login screen, it's definitely installed.

---

### Post by franpa on 2006-10-15
well, when resizing windows its slow and sluggish where as in windows its perfectly fine... is this how its meant to be?

---

### Post by aysiu on 2006-10-15
> **franpa said:**
> well, when resizing windows its slow and sluggish where as in windows its perfectly fine... is this how its meant to be?
If that were how it's meant to be, I doubt anyone would be using Ubuntu.

Can you give your computer's specs?

---

### Post by franpa on 2006-10-15
p4 3.00ghz ht
p5ld2 m/b (standard)
2 gigs ram (ddr2)
20gig hdd for linux partition
1gig hdd for linux-swap
soundblaster xfi xtreme soundcard
nvidia geforce 6600 gt pcie 128mb

if you need anything else just ask :)

---

### Post by aysiu on 2006-10-15
Okay, that baffles me. Ubuntu should fly on a computer like that, especially with the Nvidia drivers installed.

I hope someone else can chime in on what might be wrong.

---

### Post by franpa on 2006-10-15
its not a snail pace or anything... its just that its no where near as smooth at resizing windows like in MS windows...

mmm, im gonna install ut 2004 and see if i can get it to run... if i can then the drivers are installed.

---

### Post by franpa on 2006-10-15
double post -.-'

why does ubuntu lock my cd drive? is it possible to unlock it as i need to put the second disc in.

edit: it locks my first drive but not the second drive... must the disc with the installer remain in during the install?

---

### Post by franpa on 2006-10-15
IT WORKS! or atleast the game runs... at full speed... just how do i unmount the cdrom0?

---

### Post by franpa on 2006-10-15
they work... but i think theres some form of acceleration disabled or something cause ubuntu still is a tad slow... it is a hell of a lot faster then what it was tho...

---

### Post by orb9220 on 2006-10-15
Open a term and enter:
glxinfo
scroll back to top and see if you have this:
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
should be right after the command you executed.

Then in term do a:
glxgears -printfps

and post your fps.

---

### Post by franpa on 2006-10-15
7444fps approx~

and yes what you said does appear at the top and as such i am happy to say that it indeed seems like it is working.

---

