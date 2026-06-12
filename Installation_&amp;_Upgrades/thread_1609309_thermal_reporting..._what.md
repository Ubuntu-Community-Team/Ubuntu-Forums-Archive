---
title: "thermal reporting... what???"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by nebu1a on 2010-10-30
i have a vaio, with a nvidia geforce 330m.
i upgraded from 10.4 to 10.10, using the same driver i had before (256.44, form the nvidia web site) and following the same instructions i found useful the previous time ([http://ubuntuforums.org/showthread.php?t=1467074](http://ubuntuforums.org/showthread.php?t=1467074)).

my problem: now my login has no graphic interface: i am displayed this error:
> thermal reporting for required devices not enabled, aborting.
and i can log in and use ubuntu only by command line interface, 

i tried also to make a clean install using a live cd, but nothing changes.

have i to go back and use 10.4?

---

### Post by efflandt on 2010-10-30
I am not familiar with nvidia 256.44 driver.  What video card/chip do you have and why do you think you need that version.  Anytime you use a version not in the Ubuntu repositories, you are on your own reinstalling that after any kernel updates (or system upgrde).  One thing my be whether that version is compatible with the new X server 1.9
.
Ubuntu 10.10 beta used 256.53 and sometime during RC into release the current version became 260.19.06.  Some people had trouble with that, but by enabling th x-swat ppa repositories you can get version 260.19.12..

---

### Post by nebu1a on 2010-10-31
> **efflandt said:**
> I am not familiar with nvidia 256.44 driver.  What video card/chip do you have and why do you think you need that version.  Anytime you use a version not in the Ubuntu repositories, you are on your own reinstalling that after any kernel updates (or system upgrde).  One thing my be whether that version is compatible with the new X server 1.9
.
Ubuntu 10.10 beta used 256.53 and sometime during RC into release the current version became 260.19.06.  Some people had trouble with that, but by enabling th x-swat ppa repositories you can get version 260.19.12..

i have an nvidia geforce gt 330m, and i used that driver simply because it had worked well before...
actually i didn't understand what you seggested... what should i do???

EDIT: i found this: [http://www.zobbi.it/2010/10/installare-driver-nvidia-su-ubuntu-10-10-maverick-meerkat-via-ppa/](http://www.zobbi.it/2010/10/installare-driver-nvidia-su-ubuntu-10-10-maverick-meerkat-via-ppa/).
now i have the same error, but only a black screen (not even the login).

---

