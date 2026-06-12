---
title: "Cannot load Ubuntu installer"
date: 2011-01-22
forum: Installation &amp; Upgrades
---

### Post by BigRicky on 2011-01-22
Hey, all,

I am a Linux newbie, but I have had the pleasure of installing Linux (mostly Ubuntu) a dozen or so times, and out of all the conceivable problems one could foresee with Ubuntu, installation is not one of them- it's usually easier than cooking a poptart.  

I'm trying to install Ubuntu 64 bit alongside Windows 7 on a new Dell laptop.  Specs:

Processor: AMD Athlon II P340 Dual-Core Processor 5.3 4.1 
Memory:  3.00 GB 5.5 
Graphics: ATI Mobility Radeon HD 4250  
OS: Windows 7 64 bit

And here is my odd story:  I downloaded Ubuntu 10.10 64 bit, tried to install it from CD.  Got a black screen, and then ten seconds or so I would get a cursor where I couldn't do anything.  Typing didn't do anything, and neither did Ctrl Alt F1.  Tried installing via USB drive.  Same thing.  

Tried installing via Wubi.  Went successfully in Windows, then said I had to reboot into Ubuntu to finish the installation.  Boot into Ubuntu, and it says it's installing and then freezes.  Several hours and headaches later, I uninstalled my Wubi Ubuntu.

By recommendation of a nice gent in IRC who thought this might be a graphics issue, I downloaded the alternate version.  When trying to install by USB or CD I get one step further.  I get to the Ubuntu install screen where it asks what I would like to do: Install Ubuntu or perform a mem check or whatever.  Then after I select "Install Ubuntu" it shows a bunch of commands going through and stops at one and doesn't continue.

Any advice will be greatly appreciated.  

Many thanks,
Ricky

EDIT:  Apparently it is due to my graphics card.  I was able to install by checking the advanced parameters 'acpi=off', 'noapic', and 'nolapic'.  Now it won't boot because of aforementioned graphics problem, but it IS installed.

---

