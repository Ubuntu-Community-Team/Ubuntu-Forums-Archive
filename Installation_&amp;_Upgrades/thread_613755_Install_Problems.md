---
title: "Install Problems"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by matt1978 on 2007-11-15
I am a noob to linux so bear with me here.

I can boot up with the live CD (7.10).

I have 2 Hard drives : 

1. SATA 120 G - Linux Install drive
2. IDE Data 300 G (SLAVE) - has all my data 

Computer Type : Compaq Presario @ 3.3GHz

Grpahics Card : Nvidea GForce 8500

RAM : 2 Gigs

Upon booting into the LIVE CD, I click the install on the desktop.  I go through the various screens for options and selecting my region and language.  I used guided install using HD 1 above.  Everything seems to go well and finish installing but when I restart after installing, I get prompted to remove CD and press enter.  I proceed to do that and when it restarts, I get a "Non-system disk or disk error Replace and strike any key..."

Pressing a key just repeats the same message.  I have no floppy and no USB devices attached so I have no clue how to proceed.  There is no other devices.  

Should I be changing anything in the advanced options prior to installing?  Should I install the boot loader?  Is it trying to boot from HD 2 instead of HD 1?

Any help would be much appreciated.

---

### Post by bulldog on 2007-11-15
Change the boot order in your BIOS,make the IDE hdd master boot device and see how it goes.
By default,GRUB will be installed tot the IDE hdd,not the Sata.

---

### Post by matt1978 on 2007-11-15
Thanks, I will give it a shot.  

What is the difference between OEM install and regular?  My latest attempt is the OEM install just to try something else, are there many differences?

---

### Post by matt1978 on 2007-11-15
Hey bulldog, still no luck.  I changed the IDE's so now the hard drive is the master and cd rom is slave.  I did a fresh install back onto the same 120gig SATA and then changed the boot sequence to try to boot from the IDE first (300 gig data).  When rebooting it, I got the error "GRUB Read Error".  I have been looking for a fix but cant seem to find out how to resolve.  Any thoughts?

---

