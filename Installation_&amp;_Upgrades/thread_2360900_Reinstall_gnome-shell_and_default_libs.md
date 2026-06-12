---
title: "Reinstall gnome-shell and default libs"
date: 2017-05-09
forum: Installation &amp; Upgrades
---

### Post by Jorge_Lazo on 2017-05-09
Hi,

I made a serious mistake while using apt-get and I removed all of the core libraries (and apps) that came with gnome by mistake. What is the easiest way to revert back to the default installation?
My sources list are up to date, but when I do:

```
sudo apt-get install gnome-shell


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 gnome-shell : Depends: evolution-data-server (>= 3.7.90) but it is not going to be installed
               Recommends: gnome-contacts but it is not going to be installed
               Recommends: gnome-control-center but it is not going to be installed
               Recommends: gdm3 (>= 3.10.0.1-3~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I tried fixing it with apt-get update/upgrade and reinstall, but I still get the unmet dependencies issue. I can't install aptitude either because of the same issue. What can I do?

---

### Post by ian-weisser on 2017-05-09
The 'Impossible Situation' usually means that you have upgraded from stock Ubuntu, usually using non-Ubuntu sources (like PPAs) for the upgrade.
Is this correct?
What release of Ubuntu?  14.04? 16.04? 17.04? Something else?

---

### Post by Jorge_Lazo on 2017-05-09
Yes I was messing around with testing/proposed but then reverted back to stock. the version of Gnome I was using was 16.04

---

### Post by ian-weisser on 2017-05-10
Perhaps you have not completely reverted all packages from -proposed.

---

