---
title: "apt shows upgrades available but can't install them"
date: 2019-07-22
forum: Installation &amp; Upgrades
---

### Post by rattskjelke on 2019-07-22
I am using Xubuntu 19.04. I have never had this problem before.

When I run *sudo apt update* it says:
*3 packages can be upgraded. Run 'apt list --upgradable' to see them.*

*apt list --upgradable* shows the three packages:
[I]linux-generic/disco-updates 5.0.0.21.22 amd64 [upgradable from: 5.0.0.20.21]
linux-headers-generic/disco-updates 5.0.0.21.22 amd64 [upgradable from: 5.0.0.20.21]
linux-image-generic/disco-updates 5.0.0.21.22 amd64 [upgradable from: 5.0.0.20.21][/I]

If I run *sudo apt upgrade* or *sudo apt full-upgrade* they both say:
* 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.*

Running Software Updater says everything is up to date.

I thought something might have broke so I ran *sudo dpkg --configure -a* and *sudo apt -f install* which didn't find any problems.

How do I troubleshoot this?

---

### Post by uRock on 2019-07-22
That's weird, have you run **sudo apt dist-upgrade**?

---

### Post by rattskjelke on 2019-07-22
> **uRock said:**
> That's weird, have you run **sudo apt dist-upgrade**?
apt-get dist-upgrade should be the same thing as apt full-upgrade. Neither works. I still get *0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.*
I also tried Synaptic and it doesn't show any upgrades available either.

I just tried to install the 3 packages and got this:
[I]sudo apt install linux-generic linux-headers-generic linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-5.0.0-21-generic but it is not installable
 linux-image-generic : Depends: linux-image-5.0.0-21-generic but it is not going to be installed
                       Depends: linux-modules-extra-5.0.0-21-generic but it is not installable
E: Unable to correct problems, you have held broken packages.[/I]

My kernel version is 5.0.0-20 from last week. Maybe these packages got into the repo before the next kernel version or something. I don't know what's going on or how to fix it, or if it needs to be fixed.

---

### Post by Impavidus on 2019-07-23
It could be a server glitch: upgraded packages available before their new dependencies. Try again. I just installed the same update.

---

### Post by rattskjelke on 2019-07-23
> **Impavidus said:**
> It could be a server glitch: upgraded packages available before their new dependencies.
That must have been what happened. Today it updated the kernel with no held packages or other problems.

---

