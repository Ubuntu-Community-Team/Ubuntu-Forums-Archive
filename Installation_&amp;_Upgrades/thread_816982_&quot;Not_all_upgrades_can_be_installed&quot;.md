---
title: "&quot;Not all upgrades can be installed&quot;"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by DavidFourer on 2008-06-03
Since upgrading to Hardy, I've been getting a failure when I try to upgrade packages.  Some packages install, but I get error message 
> Not all upgrades can be installed
possible problems:
*   previous update did not complete
*   problems with some of the installed software
*   unofficial software packages
*   normal changes of a pre-release version of Ubuntu
The packages that are greyed out are:
* Recommended upgrades:
f-spot
linux headers generic
linux image - 386      (no version number)
linux image - generic   
* Distribution updates:
gstreamer0.10-plugins-bad-multiverse
libgtk1.2
libmjpegtools 0c2a
mjpegtools
mplayer

Can anyone tell me what this means?  I have limited knowledge of this stuff.  I have Linux on my home Dell notebook compluter and I can usually keep it working.  Since Hardy, I've had to re-install Firefox2 and I have trouble with sleep so I sometimes boot from old kernel, though now I'm running 2-6-24-16-generic

---

### Post by dogdog on 2008-06-03
I run Ubuntu Gutsy Heron 8.04 LTS upgraded from 7.10 at end of April. When I switch on PC it shows 103 updates available to install. I go to Update Manager and click on install updates. Nothing happens - the "egg timer" icon spins but the PC stays like this and does not go to next stage. I have left PC like this for a long time. I do not get any error message. I have to reboot to get rid of spinning icon.

What is going wrong??

---

### Post by christianxxx on 2008-06-03
I had the same problem a few days ago. 100+ updates, but it refused to install updates for f-spot and openoffice.
I resolved (by itself?) after a couple of days.

---

### Post by ajgreeny on 2008-06-03
Open synaptic and look in the system bar at the bottom.  It may tell you there are broken packages on your system.  If so go to **Edit>>Fix Broken Packages** and that may sort it out.

If that doesn't work, try in terminal ```
sudo dpkg --configure -a
``` and that may help, or ```
sudo apt-get install -f
```to fix any broken packages.

---

### Post by ChameleonDave on 2008-06-03
> **dogdog said:**
> I run Ubuntu Gutsy Heron 8.04 LTS upgraded from 7.10 at end of April. When I switch on PC it shows 103 updates available to install. I go to Update Manager and click on install updates. Nothing happens - the "egg timer" icon spins but the PC stays like this and does not go to next stage. I have left PC like this for a long time. I do not get any error message. I have to reboot to get rid of spinning icon.

What is going wrong??
Thread hijacker!

I don't know what has gone wrong.  I assume you are using Adept Updater or something like that.  Instead, close all that down and open Synaptic instead.  Hit "Reload", then "Mark All Upgrades", then "Apply".

Or just don't upgrade at all.  Your system will still work.

---

### Post by DavidFourer on 2008-06-03
Thanks, ajgreeny.  Synaptic Package Manager...Edit>Fix Broken Packages.  A message at bottom bar said "Dependencies Fixed"  Then I installed all upgrades with Synaptic.  Now my system is up to date and I'm running kernel 2-6-24-17-generic.

---

### Post by ajgreeny on 2008-06-03
Glad to be of assistance.
You'll pick up these tricks little by little, and every so often they come in really useful!

---

### Post by dogdog on 2008-06-03
Many thanks for all the help and suggestions. I have managed to install 77 out of 103 updates.

When I tried to install emaining 26 updates I got message:

An error occurred. The following details are provided.

Then 26 messages (one for each failed update)along the following lines:

W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server-2.22.1-Oubuntu](http://gb.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server-2.22.1-Oubuntu) 2.1_i386.deb  404 Not Found (IP: 91.189.88.45 80)

Is this a temporary problem with ubuntu server or symptomatic of a problem at my end??

Synatic said no broken packages.

Any reason why the updates that did work, worked with Synaptic Package Manager but not with update Manager??

Again - many thanks for help.

---

