---
title: "Installing 64 bit"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by tlk2drew on 2007-11-03
I have gutsy up and running (love it by the way) and I havent had any real problems to note using the 32 bit system.  I do however run a 64 bit pc and would like to install the 64 bit software version of 7.10.

When I boot to the image I burned I get to the usual boot/run UBUNTU from cd and when I hit enter my screen just goes black.  I have the 8800gtx and am wondering if that is the problem or if I am missing something.

Any help would be great.

---

### Post by cuby on 2007-11-03
I also have a 64bit cpu, but I use the 32bit version. Some drivers are not available in 64bits. Maybe that's the case of your card.

---

### Post by tlk2drew on 2007-11-03
:guitar: I'm Rockin now :)

If I were a smart man I would have read all the other forums for the 1000 people + that are having the same issue.  My fix:

Boot to live CD, Go to safe mode, F6, delete the splash and Xforce entries then hit enter!

I am on the live desktop now getting ready to install 64bit Gutsy.  Hopefully ENVY will get my NVIDIA up and running just as easy as it did in the 32 bit version.

UBUNTU Rocks.  When windows becomes self aware and takes over the world I will be safe with UBUNTU!

---

### Post by bdamon on 2007-11-03
> **tlk2drew said:**
> 
When I boot to the image I burned I get to the usual boot/run UBUNTU from cd and when I hit enter my screen just goes black.  I have the 8800gtx and am wondering if that is the problem or if I am missing something.

Yep there is a usplash bug or something. Wait long enough and you'll get to the desktop and can perform the install. The problem will still exist after the install, at least it did for me. For now I replaced splash with nosplash in mygrub menu.lst file.

---

