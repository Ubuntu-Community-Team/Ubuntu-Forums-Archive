---
title: "HPLIP 3.16.3 Will Not Install"
date: 2016-04-16
forum: Installation &amp; Upgrades
---

### Post by SpikeLS6 on 2016-04-16
Bought new HP Laser Jet Pro M225dw to use wireless with my PC and laptop. Downloaded the 3.16.3 file from the HPLIP site. I Began the installation on Terminal where it is still sitting on "RUNNING PRE-PACKAGE COMMANDS" for the past 2-3 hours. What might be wrong that it is not continuing the installation? I am using Ubuntu 15.10. The older HPLIP 3.16.2 I was using installed and worked fine.

---

### Post by ajgreeny on 2016-04-16
Do you really need that latest version of HPLIP?  Does your printer work with the version available in the repos?
You can easily find the HPLIP version needed for that printer from the site at [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

If you can do so just use the repo version; it will be so much more simple to install in the normal way along with hplip-gui if you also want to toolbox.

I have tried the same version as you did as I need to use a later version than is available in the repos for 14.04 for my wifi printer, but the most recent version that I can get to work with my printers is 3.15.9; all later ones will not work with my hardware or printers.

---

### Post by SpikeLS6 on 2016-04-16
Minimum for the M225dw is 3.14.10, which is several updates below the 3.16.2 I already have. I did get it to print via wireless just a few minutes ago, so that should do it. No updates until it quits working.

By the way, what is the "repo version"? And how does one install it via the hplip-gui toolbox? That may be something I need to print out for the future.

---

### Post by ajgreeny on 2016-04-17
The "repo version" as I called it (sorry about my shorthand) is simply the version available by running command ```
sudo apt-get install hplip
``` so it is the version of hplip that is in the normal repositories for your version of Ubuntu.

I am assuming that you normally upgrade or install any packages that you require in this way using the software-centre or apt-get commands and not by searching in the web for packages; if you do the latter you should stop doing so and use the repositories.

I assume you have now reinstalled the 3.16.2 version?

---

### Post by SpikeLS6 on 2016-04-17
I tried the repo for HPLIP, but it was down in the 3.14.X area, so I kept my 3.16.2 that I had previously installed. This is the way I normal try to install new software if Synaptic or the Software sites do not have it. Getting the spelling correct for a new apt is usually my biggest problem.

Thank you again for your help. Nice to have a wireless printer working with 15.10.

---

