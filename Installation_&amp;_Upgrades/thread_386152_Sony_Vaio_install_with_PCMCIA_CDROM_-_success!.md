---
title: "Sony Vaio install with PCMCIA CDROM - success!"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by maybethisllwork on 2007-03-16
After trawling this forum and other Linux forums for help with installing from a PCMCIA CDROM, and countless install atempts, I finally got it working! :) 

So for the benefit of anyone else trying something similar, here's what worked - but also what didn't!

Machine spec for the record is:
Sony Vaio PCG-N505X laptop (Celeron 333 cpu), 128mb RAM
USB floppy & mouse, PCMCIA CDROM
Netgear EA101 usb ethernet

I had tried Ubuntu 6.10 desktop and 6.06 desktop, even tried Feisty Herd 4 as suggested in one posting - in all cases, and no matter what boot options I added, the installation stalled completely at some point soon after checking the CD was mounted. I had tried with debian-installer/probe/pcmcia=false, hw-detect/start_pcmcia=false (which worked for Debian) and all the noapic, noapci or apci=false that were suggested in various posts. All had failed at some point during install.

I knew it *should* be possible because I had previously installed Debian on this laptop - but I was disappointed at its hardware detection (it wouldn't use the touchpad on the Vaio).  I also tried installing Mepis, PCLinux, Knoppix and OpenSuse on this laptop as well - only OpenSuse installed straight off the cd without any special options but its performance on this old machine was hopeless, and Knoppix worked but the hard-disk install is not advised. Besides I really wanted to get Ubuntu working, after installing it on another pc and liking it.

What led to final success was using the 'Alternate' ISO image of Ubuntu 6.10 instead - it took a couple of hours to complete (it is a slow machine) but now I have a nice working system, touchpad and all, with pretty decent response/performance
 :guitar: 

What I did:
- downloaded and burned ubuntu-6.10-alternate-i386.iso 
- booted to the installer from the CDROM
- hit F6 key to add boot options to the default install
- removed the option quiet (to see all the messages)
- added debian-installer/probe/pcmcia=false (prevent PCMCIA being probed - can be the cause of 'losing' the cd during install) and priority=medium (gives extra prompts and does the installation stepwise)
- worked through each of the installation steps in turn responding to the prompts
- sometimes waited patiently while nothing seemed to be happening

That's it ! after the other troubles I couldn't beleive it just ran.

If anyone can shed light on why Alternate worked when Desktop didn't I'd love to know (academic interest only - I'm not about to reinstall just yet!)

Next step: try to get my D-Link 650+ wireless PCMCIA card working (the Vaio only has one PCMCIA slot, and that had the CD drive in it, so the wireless card could not be in place while installing and hence not detected!)

Good luck to others trying the same

- Steve

---

### Post by steve_vmwx on 2007-06-09
Thanks Steve, good stuff. I'm using a C1VG picturebook and this trick works fine with Kubuntu 6.10.

By coincidence I've also got a DLink 650 card. I'm working on the idea of going through the install menu then going back to the network setup before exiting. I'll let you know how it goes.

Stevo

---

### Post by draggett on 2007-06-22
The instructions also worked perfectly with an ancient Vaio PCG-Z505HS and Feisty Fawn (7.04 alternate).

---

### Post by coolparty on 2007-07-10
YES! Thanx! VX7/BD works! Only on alternate 7.04.

---

### Post by orangeSock on 2008-01-03
Thank you very much for the hint to use a CD-ROM drive used via PCMCIA

The option
debian-installer/probe/pcmcia=false
with the alternate installation CD solved my installation issues on a
SONY PCG-Z600LEK after tries without any success with the boot option
ide2=0x180 

Now I'm using 7.10 and are happy with it.

Claus

---

