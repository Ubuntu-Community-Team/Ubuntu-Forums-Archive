---
title: "Upgrade to Feisty and Wireless - Oops?"
date: 2007-05-19
forum: Installation &amp; Upgrades
---

### Post by sarahr on 2007-05-19
Hey, folks - 

A couple nights ago, I upgraded from Edgy to Feisty.  I had some trouble getting the GUI updater to work (errors about server connections), so went to the command line to run the update, then ran again from the GUI, per instructions I read posted here.  

After that false start, the upgrade went swimmingly, but my wirless card, a **D-Link WDA-1320**, suddenly stopped working.  This card was a plug-and-play with the last version of Ubuntu I had installed, Edgy.  I am running on a desktop PC with an AMD Athlon 2700 processor (NB: I'm a Mac user under normal circumstances).

Can someone steer me to some basic troubleshooting tips for getting this sucker back up and running?

Thanks a lot.

---

### Post by Borzo on 2007-05-20
uhh... i don't know but maybe try installing the linux kernel restricted module packages for the new kernel? 
I have to do that everytime the kernel changes in order to have my built in wireless working

good luck

---

### Post by sarahr on 2007-05-20
Okay, I need some more information on what exactly that means.  I'd be more than happy to do it.  I didn't have to do anything at all under Edgy, which is why I am (so easily) befuddled.

Thanks.

---

### Post by Borzo on 2007-05-20
That means:

Uninstalling your current restricted modules, these are probably
restricted-modules-2.6.17-11-386
and
restricted-modules-2.6.17-11-generic 

you can do that either in synaptic, or from console like this:
sudo apt-get remove restricted-modules-2.6.17-11-386
sudo apt-get remove restricted-modules-2.6.17-11-generic

and then, installing the restricted modules for your current kernel, and these are probably:  
restricted-modules-2.6.20-15-386
and
restricted-modules-2.6.20-15-generic
you can do that either in synaptic, or from console like this:
sudo apt-get install restricted-modules-2.6.20-15-386
sudo apt-get install restricted-modules-2.6.20-15-generic

after all that, you reboot and everything should be OK.

Good luck :)

---

### Post by sarahr on 2007-05-20
I imagine I'll need to be on a LAN connection for this, right? ;)

---

### Post by Borzo on 2007-05-21
well, yes :) , either that or a direct connection... you could select your previous kernel at boot time at the GRUB menu ( by pressing esc  ), 
and boot to the previous kernel, see if your connection works ( that worked for me ), you can then install the new restricted modules.

---

### Post by sarahr on 2007-05-21
That's a great idea, and just what I'll do.  Thanks a lot.

---

### Post by sarahr on 2007-05-22
> **Borzo said:**
> well, yes :) , either that or a direct connection... you could select your previous kernel at boot time at the GRUB menu ( by pressing esc  ), 
and boot to the previous kernel, see if your connection works ( that worked for me ), you can then install the new restricted modules.

Should I be using ndiswrapper?

---

### Post by Borzo on 2007-05-22
according to what i read about your wireless card, you need to use madwifi, which is in the restricted modules i mention earlier.

---

### Post by sarahr on 2007-05-22
Thanks, and sorry for the clueless.

---

### Post by sarahr on 2007-05-22
> **Borzo said:**
> That means:

Uninstalling your current restricted modules, these are probably
restricted-modules-2.6.17-11-386
and
restricted-modules-2.6.17-11-generic 

you can do that either in synaptic, or from console like this:
sudo apt-get remove restricted-modules-2.6.17-11-386
sudo apt-get remove restricted-modules-2.6.17-11-generic

and then, installing the restricted modules for your current kernel, and these are probably:  
restricted-modules-2.6.20-15-386
and
restricted-modules-2.6.20-15-generic
you can do that either in synaptic, or from console like this:
sudo apt-get install restricted-modules-2.6.20-15-386
sudo apt-get install restricted-modules-2.6.20-15-generic

after all that, you reboot and everything should be OK.

Good luck :)

So, I'm at my Ubuntu machine now, booted up into 2.6.17.10 (.11 wouldn't load, for some reason).  Wireless card is, clearly, working.  I went to the command line to remove and install the restricted-modules-*, and, alas, there is no such item residing on my system. 

I fired up Synaptic and looked there, too; all I have is a package that manages the Restricted Drivers (not the drivers themselves).  When I fire that up, I see my ATI drivers and "Atheros Hardware Access Layer (HAL)," which I assume to be what is making my wireless card go.  Both of these were present under Feisty, too.

What should I try next?

Thanks again.

---

### Post by sarahr on 2007-05-22
For crying out loud...

It's now working under Feisty. What the hell?
:p

---

### Post by Borzo on 2007-05-22
so is it working?

---

### Post by sarahr on 2007-05-22
It sure is.  

I have no idea...

---

