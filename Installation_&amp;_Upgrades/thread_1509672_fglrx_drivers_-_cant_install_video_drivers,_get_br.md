---
title: "fglrx drivers - cant install video drivers, get broken filters errors"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by surrealillusions on 2010-06-14
Hi all,

Have just upgraded from 9.10 to 10.04 and have got a problem with video  drivers.

In the update manager, theres an option to install fglrx drivers, but it  wont install.

First message I get is:

You have 3 broken packages on your system!
Use the "Broken" filter to locate them.

Then I click 'close'. Then I get an error occured:

E: /var/cache/apt/archives/fglrx_2%3a8.723.1-0ubuntu3_i386.deb:  subprocess new pre-installation script returned error exit status 1

click close, not all updates have been completed.

How do I use the "broken" filter? And will that help fix the problem of  been unable to install the video drivers. I'm running basic visual  effects (i.e none), but would like to use the full wizardry effect  stuff.

---

### Post by surrealillusions on 2010-06-15
Anyone know anything?

I've found the Broken Filter in the Synaptic Package Manager. Tried complete uninstallation of the broken filters/packages, but it still wont install afterwards.

Tried the solution in this topic: [http://ubuntuforums.org/showthread.php?p=9460932](http://ubuntuforums.org/showthread.php?p=9460932)

But as I've said there, theres still some problems.

:)

---

### Post by surrealillusions on 2010-06-15
Tried numerous things. Installing, reinstalling, purging, reconfiguring, but its not doing anything. Still refuses to recognise the ATI drivers.

There was a problem initializing Catalyst Control Center Linux edition.  It could be caused by the following.
 No ATI graphics driver is installed, or the ATI driver is not functioning properly.
 Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig.




This is driving me insane ](*,)

---

### Post by donc786 on 2010-06-15
I know this post will be of little help in solving the problem. I have the same problem with the radeon 9200. I had it running well in 9.10, but now I have the same problem with the driver install. I once followed a thread that involved running xorg and setting up an X11 config file, or something to that effect. That seemed to work. I think that is an old way of doing things though.

---

