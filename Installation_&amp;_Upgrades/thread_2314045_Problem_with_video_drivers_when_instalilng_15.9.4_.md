---
title: "Problem with video drivers when instalilng 15.9.4  on Thinkpad W541"
date: 2016-02-18
forum: Installation &amp; Upgrades
---

### Post by kiwidba on 2016-02-18
I'm a long time partially-sighted user of Ubuntu. I now have a Thinkpad W541 and
am having zero success installing Ubuntu successfully enough to run Unity or Gnome. I'm aware the W541 is not currently on the list of supported hardware, but hey, this is the laptop I have, I need it for work, and I'd really really like to get Ubuntu running on it. Any help with that would be super-appreciated.  

It's been quite the multi-day saga so far, but to summarise: 
 
Trying to install Ubuntu 15.04 from a live CD, the first issue I
found was the error message "mmc0 unknown controller version(3), You may experience problems"
 
I finally got the live CD to boot using the "nomodeset" parameter in
the GRUB configuration, but after installation the installed version
of Ubuntu froze reliably very shortly after login. This was true for both Unity and
GNOME 3.
 
Following advice on various forum posts, I've tried:

Blacklisting the Nouveau video driver. That allowed slow, low-res command line access only, with the original error message popping up intermittently.

Installing NVidia drivers from the NVidia website. Same result.

Installing Bumblebee. That opened Ubuntu in low-graphics mode with error messages about the video drivers. It offered several alternatives to 
fix this, but when I tried the alternatives, Ubuntu wouldn't register any keyboard input. 
 
I found the following bug registered on Launchpad, which is
marked as "expired".
 
[http://www.google.co.nz/url?q=https://bugs.launchpad.net/bugs/1437386&sa=U&ved=0ahUKEwiCs6Kvw4DLAhVIIKYKHWXpAMYQFggfMAI&usg=AFQjCNF24QGV3sbopiR2QRsVKAWIDvplNQ](http://www.google.co.nz/url?q=https://bugs.launchpad.net/bugs/1437386&sa=U&ved=0ahUKEwiCs6Kvw4DLAhVIIKYKHWXpAMYQFggfMAI&usg=AFQjCNF24QGV3sbopiR2QRsVKAWIDvplNQ)
 
I can't find any references to later versions of Ubuntu addressing this.
 
What I'm aiming for is a working copy of Ubuntu
running on my W541 with a Windows dual boot, and also without
resorting to hand-compilation of drivers or other software outside the
control of aptitude. The reason for this is that I've
found in the past that compiling components manually has introduced
instabilities into my system when I later upgrade packages via
aptitude. I can't just not upgrade: I need to keep my software as up-to-date as possible to take advantage of the
constant improvements in accessibility for visually impaired
users. And I need the Windows dual boot for work (unfortunately).
 
Does anyone know a way to successfully install Ubuntu on the W541
using only packages available via aptitude? If it helps, I don't need
any fancy game-speed video modes, just plain Unity or GNOME access at
a reasonable resolution and speed. Thanks.

---

### Post by ajgreeny on 2016-02-18
I'm not sure what you mean by version 15.9.4 as there is no such version; you must mean either 15.04 or 15.10.

However, 15.04 has now lost any further support so there is little point in installing that version.  You need to either move to 15.10, or in my opinion use version 14.04 for the moment, which is supported until April 2019.

Remember also that there are alternative desktop versions of *Ubuntu which may suit you such as Xubuntu, Lubuntu or Kubuntu.

---

### Post by grahammechanical on 2016-02-18
Does this machine have hybrid graphics? By that I mean, does it have an onboard Intel graphic adapter and a discreet Nvidia Adapter? If it does not then you should not be trying to install Bumblebee because Bumblebee is the project for providing an open source video driver for hybrid graphics known as Nvidia Optimus technology.

We do not need to install drivers from a web site. We have a utility to do that for us. That machine seems to have either a Nvidia Quadro K2100M or a K1100M. The Nvidia recommended driver is version 361.28. I do not think that is available in Ubuntu 15.04. So, there is another reason for going with 15.10 or 14.04.4.

The Ubuntu live session comes with an open source video driver as a default. It is called Nouveau. Sometimes, we do indeed need the nomodeset option to load the live session with certain video adapters. But we can install a proprietary video driver after installation.

We go to System Settings>Software & Updates>Additional Drivers tab. We are connected to the internet and we allow time for the utility to find drivers from the repositories. We get offered a choice of 2 proprietary drivers each with 2 variants. There is no need to compile drivers. The Additional Drivers utility does all the work for us.

You do not make clear the present situation. We cannot give advice on past issues. 

At the Grub boot menu we can select Advanced options for Ubuntu and then select a recovery mode kernel. At the recovery menu we select Resume. That will often get us to working desktop overcoming any driver conflicts. From a working desktop we can get to Additional Drivers and experiment.

What you are aiming for is no different from what the rest of us want and get and often with next to no fuss.

Regards.

---

