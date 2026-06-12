---
title: "Epia 800 - Ubuntu 6.06 Installs ... and then craps out!"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by fiddler1000 on 2006-07-11
Hi Folks

I was previously running Win98 on my Epia 800 machine with no problems.  I decided to install Ubuntu instead.  I backed up my data so I wasn't worried about wiping the machine.

I downloaded the Desktop 6.06 ISO and made my CD.  Ran the memory checks and the CD integrity check first.  Everything passed OK.  I then ran the install and selected the following options:

- Chose to NOT auto-configure my network hardware as I would manually do this later.
- Chose to erase my hard disk and let the Ubunutu install partition my disk.

Everything seemed to go OK.  The install completed and my CD was ejected.  All that was needed was a re-boot and I'd be in business.

Nope!

Everytime I boot up now I get to a point and then the machine reboots.  The last thing I see on the screen is the word 'boot' and then the machine resets.

Guys, sorry about this but I'm completely new to Linux and Ubunutu.  I haven't the first idea where to start to figure out what's going wrong.  Any ideas?  What do you need me to tell you?

My system spec is as follows:

- VIA Epia 800 Mainboard
- 256MB RAM
- 10GB Hard Disk
- Gigabyte 802.11g PCI card
- Slimline CD-ROM
- USB Keyboard
- USB Mouse

Cheers,
Fiddler.

---

### Post by cyent on 2006-07-11
Boot in rescue mode, mount your root partition and dig around in the /var/log directory for clues....

ls -lrt /var/log

I don't think there is enough info for us to chew on in your current post.

Any clues to at what point it reboots would be Good.

---

### Post by fiddler1000 on 2006-07-12
I've opened the directory and can see the following files:

hardware-summary
syslog

But ... erm ... sorry, but how do I actually READ these file?! :-|

---

