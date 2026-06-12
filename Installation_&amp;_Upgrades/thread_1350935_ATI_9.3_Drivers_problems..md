---
title: "ATI 9.3 Drivers problems."
date: 2009-12-09
forum: Installation &amp; Upgrades
---

### Post by whoobex on 2009-12-09
Hi, first time poster, first time linux user. Starting to read up on linux, and I've just seen the revolution OS film.

I got the 64bit version of ubuntu, i think, if so, should I write only in the 64bit part of the forum? Shuold I perhaps choose the non 64 bit version of ubuntu for easier beginnerfriendly access? 

and; the version of graphics is: ati-driver-installer-9-3-x86.x86_64

When I'm trying to install with terminal, or with ATI Propreitiy drivers I get an error message that says:
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:2.6.31-16-generic; make sure that 
ng
correctly set by --iscurrentdistro

Some got left out, nothing important, but the terminal insists on closing just now when I want to keep it open to copy paste, pointers? :D Is the driver simply too "new"?
It starts unpacking but at some point it says no.

Well what do you make of it? And if you think I could have found out in some other way, please give pointers on how to find my own "answers" a point in the right direction.

---

### Post by phillw on 2009-12-09
> **whoobex said:**
> Hi, first time poster, first time linux user. Starting to read up on linux, and I've just seen the revolution OS film.

I got the 64bit version of ubuntu, i think, if so, should I write only in the 64bit part of the forum? Shuold I perhaps choose the non 64 bit version of ubuntu for easier beginnerfriendly access? 

and; the version of graphics is: ati-driver-installer-9-3-x86.x86_64

When I'm trying to install with terminal, or with ATI Propreitiy drivers I get an error message that says:
Error: ./default_policy.sh does not support version
default:v2:x86_64:lib::none:2.6.31-16-generic; make sure that 
ng
correctly set by --iscurrentdistro

Some got left out, nothing important, but the terminal insists on closing just now when I want to keep it open to copy paste, pointers? :D Is the driver simply too "new"?
It starts unpacking but at some point it says no.

Well what do you make of it? And if you think I could have found out in some other way, please give pointers on how to find my own "answers" a point in the right direction.

Hello and welcome to the forum

Have a good look though the nvidea & ATI sticky at the top of this forum - most of the gotchas are within that. For a purely graphics problem, I'd stick with that thread - but, there is no harm in checking out the 64 bit area also. It takes a while to 'find your feet' on the various sub-areas.

Regards,

Phill.

---

### Post by whoobex on 2009-12-09
> **phillw said:**
> Hello and welcome to the forum

Have a good look though the nvidea & ATI sticky at the top of this forum - most of the gotchas are within that. For a purely graphics problem, I'd stick with that thread - but, there is no harm in checking out the 64 bit area also. It takes a while to 'find your feet' on the various sub-areas.

Regards,

Phill.

this is a driver that wont install. could it be something other than wrong versions crashing against each other?

ill take a good look as you said, thank you in advance.

---

### Post by ssri on 2009-12-10
9.3 only works with xserver 1.5.x (Intrepid) and kernels 2.6.28 (Jaunty) and below..

---

### Post by Mark Phelps on 2009-12-12
Didn't notice what model ATI card you have, but as ssri indicated, v9.3 drivers don't work with Ubuntu versions newer than 8.10.  The newer drivers DO with with Ubuntu but require the newer HD 3x/4x/5x cards.

---

