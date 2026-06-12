---
title: "Weird artifacts with fglrx and Radeon 4830 in 8.10"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by npwhite on 2008-11-04
Just installed Ibex (64-bit architecture) on a machine running one of the new Radeon 4830 cards. 

The open source drivers, the ones installed by default, work fine though sluggish, and not able to run in widescreen resolution.

After I install proprietary drivers using the Hardware Manager, everything works great, except the bottom right corner of the screen has a few green and orange artifacts/garbled pixels. They show up over the desktop any windows -- but they don't affect the mouse cursor. 

The card is running great on my Windows install, so I don't suspect a hardware issue, though it's certainly possible. I also uninstalled and re-installed using Hardware Manager to no avail.

Has anyone run a 4830 successfully on Ibex?

What specs can I provide that might help diagnose the problem?  Any alternatives that I'm painfully ignorant to? I read about some issues with the proprietary drivers during beta. Is this still the case? 

Thanks in advance. A bit of a n00b with this stuff.

---

### Post by npwhite on 2008-11-05
Update: I tried doing a fresh install of Hardy to isolate whether this was an Ibex problem or a driver issue. 

In Hardy, the default open source drivers again work fine, but the Hardware Driver repository doesn't detect any available proprietary drivers whatsoever. I don't get the option to activate them. Just a message that says "No proprietary drivers are in use on this system."

I checked Software Sources, and have turned on third party sources.


Is there something I'm overlooking? Please help! I'd really love to get the Radeon 4830 working on the Ubuntu side of this machine. Don't want to have to exchange this for an NVIDIA card if it can possibly be avoided.

---

### Post by cyberkost on 2008-12-22
I just replaced Nvidia 7600GS with ATI 4830 and the X started after several coughs and hiccups. It does not go above 800x600 though and I also get "No proprietary drivers are in use on this system."

Would appreciate some hints to how extract the 4830's potential on the Linux side of things.

---

### Post by fudo on 2008-12-23
I'm had similar problems. I did a clean install of Ibex(x64) with a working Nvidia 7300 GLE setup. Then swapped out an NVidia card for an Sapphire ATI Radeon 4830 card. 

After first boot with new card, used the default VGA driver with UI without any problems. Used Envyng to remove all Nvidia drivers. Envyng only offers an older version of the official ATI Catalyst drivers. So I installed the latest Catalyst driver from the AMD site, all seems to work fine. 

I used the guide here : [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

@cyberkost have a look at the above link, this should get you past your problems.

@npwhite - I don't have any desktop rendering issues as such. Though I have now disabled 'Desktop Effects' meaning no Compiz. However when it was enabled it worked fine for me. 

The only problem I'm having is with games via Wine. For instance a few seconds after entering World of Warcraft the screen goes black and the display shutdowns. Have to power off. There are plenty of threads about these sort of issues with Warcraft on these boards, but none that mention 4830 so I thought I would post on this thread to see if anyone else is having problems.

I'm using the 8.12 Catalyst drivers, which version of the Catalyst drivers are other people using with Ibex? Also are you using 32-bit or 64-bit Ibex?


fudo

---

