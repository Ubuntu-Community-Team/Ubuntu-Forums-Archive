---
title: "Problem updating from CD using a CD-ROM connected via a PCMCIA interface (w/ fix)"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by Chuckaluphagus on 2005-10-27
I ran into a problem when updating from Hoary to Breezy on my father's ancient Sony Viao notebook.  The model he has, a Viao z505SX, has an external CD-ROM drive that connects to the notebook using a PCMCIA (PC Card) adapter.  

When using Synaptic to conduct the upgrade off the Breezy install CD, I found that, about a quarter of the way through the process, Synaptic would terminate the upgrade and say that an error had been involved.  When I opened the terminal section of the error message to see whether there was some clue as to what had gone wrong, it showed that the upgrade had failed when it got to the package "pcmcia-cs_3.2.5-11ubuntu8_i386.deb".  This is apparently the package for the PCMCIA slot control software.  The error message indicated that, in preparation for the installation of the new PCMCIA software, the existing software had first been shut down.  This immediately disconnected the CD-ROM drive from the system, leaving Synaptic with nowhere to get the new PCMCIA software from (no Internet connection).   Hence the error.

The simple fix for this is  to simply update the PCMCIA software by hand: copy the file "/pool/main/p/pcmcia-cs/pcmcia-cs_3.2.5-11ubuntu8_i386.deb" from the CD to your desktop, then open a terminal and run the command "sudo dpkg -i ./Desktop/pcmcia-cs_3.2.5-11ubuntu8_i386.deb" from the command line.  Once this was done, I restarted the update process from Synaptic and everything else installed flawlessly.  

I realize this isn't rocket science, but it's certainly something my father wouldn't have been able to figure out on his own.  I also realize that CD-ROM drives that run through a PCMCIA interface are not common anymore, but one of the great things about Linux is that it can still be a viable operating system on a much older machine, extending the useful lifespan and saving some cash.  This is a simple bug that hopefully will get fixed (ok, circumvented) for Dapper Drake so as to not make my father fear he's done something horrible. (And yes, I did check to see whether it was in the bug list, it is.)

Hopefully this will be of some help to someone else.

---

