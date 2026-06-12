---
title: "Hiccups on install - comp shuts down every 15mins"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by JustGus on 2008-06-28
Hi there,

First post, but no doubt not the last and am looking forward to familiarising myself with Linux.

I've just installed 8.04 Desktop on a new VIA MiniITX system, 
2 Gig cpu, 
1 Gig ram memory
500GB HDD

A totally clean install.  But for some reason the machine reboots after around 15-20 minutes.  I'd be grateful if anyone can point to what to look at to see if this is system setting that can be fixed. I'm hoping this isn't a hardware problem. The BIOS boot up screen shows the CPU temp at 44C 111F, which I assume is okay, so hope its not something to do with overheating.

Also, is there anyway that I can set up the machine to simply boot up and not require a username/password? I've hunted around looking under the System menu, but can't find any box to tick to turn this off.

And finally, I was hoping to set up Webmin, so I could use my Vista laptop to make changes and run it headless. It doesn't have an internet connection so I downloaded the app and dragged the webmin_1.420_all.deb file from a USB to the desktop of my new machine.  But when I right click and select "Open with GDebi Package Installer" I get an error message: "Dependency is not satisfiable: libnet-ssleay-perl".  Any idea what I'm doing wrong?  When I've tried to find the file by opening the Synaptic Package Manager, the file doesn;t appear on the list.

Any help would be hugely appreciated!  

Gus

---

### Post by AlexBellisBrown on 2008-06-28
Do away with the log-in
I'm the only one using the ancient laptop I installed Ubuntu on, and I don't feel the need to keep interlopers off it, so I set it to start without requiring a log-in ID and password. To cancel the log-in, click System > Administration > Login Window, enter your password, and select the Security tab in the Login Windows Preferences dialog box. Choose your ID in the User drop-down menu, and click Close. The next time you start Ubuntu, the OS will load without prompting you for a username and password. You'll still have to enter your password to access Administration tools, however.

---

### Post by AlexBellisBrown on 2008-06-28
Regards to the CPU temperature, its perfect, mines currently 60´c, and HDD at 50´c. SO i see no problems there. Have you tried running the update manager?

---

### Post by JustGus on 2008-06-29
AlexBellisBrown, thanks so much!  The login works a treat.  Now if only i can fix the computer constantly and unexpectedly rebooting every 15-20 mins I'll be all set!

---

### Post by AlexBellisBrown on 2008-06-29
No problem mate, i dont know what to suggest about the turning on and off... Try System - Administration - Hardware Testing, to check its not a hardware problem. Also try giving the Update manager a spin, System - Administration - Update Manager. Let us know how it goes. :)

---

