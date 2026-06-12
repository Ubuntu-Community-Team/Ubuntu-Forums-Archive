---
title: "Install fails"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by bob1784 on 2007-09-17
Hi - I have no tried to install on 2 sepate machins without sucess.   The last machine was a standard desktop Pentium III 1 M ram 5GB disk AGP generic grapics.  the auto install just looped after the display manager load (I left it over night just in case).  I down loaded the text base installler and it hung so I switched 'quiet' option of on the install.   It now gets tuck on starting the partitioner at 61%.   The machine has two network cards (ONE WIRELESS) and is not connected to the net.

Can anyone help

---

### Post by dixonp on 2007-09-17
Looks like hardware problems. Have you been able to run any other OS on these systems ? When the systems are locked up, does pressing the numlock key turn on and off the numlock led ? Does typing on the keyboards produce any kind of reaction or is the system completely locked up ?

---

### Post by Pumalite on 2007-09-17
What are you trying to install?. And can you clarify this please:Pentium III 1 M ram

---

### Post by bob1784 on 2007-09-18
Windows 2000 runs fine on the system - input is OK - just the install locs up - is there a version which will install on to a clean machine ? format the disk etc ?

---

### Post by oilchangeguy on 2007-09-18
how much ram does the computer have?

---

### Post by Pumalite on 2007-09-18
That what I've been trying to know for a LOOONG time.

---

### Post by oilchangeguy on 2007-09-18
> **Pumalite said:**
> That what I've been trying to know for a LOOONG time.

it must be a hard question.

---

### Post by bob1784 on 2007-09-18
I have just tried a new disk 8GB same as the old one and the same thing happens the 'loading partitioner' hangs at 61%.  This is really frustrating as this is the second machine I had tried to install ubuntu on.  Ye I have done a mem test and tested the CD.   Is there no manual install?  Pre partitioner ?   Any ideas - many thanks for your responses so far.

---

### Post by Pumalite on 2007-09-18
> **oilchangeguy said:**
> it must be a hard question.

What do you think oilchangeguy???

---

### Post by oilchangeguy on 2007-09-18
you've not been asked to do a memory test. we'd like to know how much ram the computer has. is this for some reson, a difficult request?

---

### Post by rsambuca on 2007-09-18
bob, how much ram does your machine have?

---

### Post by oilchangeguy on 2007-09-18
> **Pumalite said:**
> What do you think oilchangeguy???

given what we know. 5gb hd, pent 3. i'd say it's an early pent 3 (300-500mhz) and has less than 128mb of ram.

---

### Post by Pumalite on 2007-09-18
Maybe peer pressure will do it.

---

### Post by bob1784 on 2007-09-18
The machine has 750Mb RAM

However you will be pleasewd to know that I have managed to install (no without problems) -  You have to select 'Configure the network later' on the network set up of the text based instsaller - this stops the partitioner from hanging - I guess if it thinks there is a network and you are nmot connected it tried to down load something - clearly a bug.

I then managed to get the ddisk partitioned however the text based installer kepot failing to un pack modules properely even though I had checked the disk - so I went back to the basic ubuntu (automatic install) and as I had partitioned the disk this now worked and installed.  However, when I rebooted (the restart screen froze by the way) I got a GRUB error 18 on boot.   I looked this up on the net and found you have to set the main disk to Auto NOT user in the bios I did this and it now works:guitar:

*UBUNTU just works* ??????

Now does anyone know where I can get a driver for a belkin wireless card F5D7000

---

### Post by Pumalite on 2007-09-18
I suggest you try Networking & Wireless.

---

