---
title: "Upgrade: no nvidia, apt-get corrupt, no sound"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by kilowhisky on 2010-06-08
So far i've had nothing but problems with the 9.10 to 10.04 upgrade. Anyways here's my problems. 

1. With Karmic i had been using avernard repos for updated nvidia drivers. When i upgraded i wanted to stop using the repos so i removed the source and apt-removed  the drivers. But when i attempted to reinstall the nvidia-glx-195 i would get an error about broken packages. (the 195 and 190 drivers and any mention of them have since disappeared from my sources list. :confused: ) So i back tracked it to this 

> 

The following packages have unmet dependencies:
  nvidia-96: Depends: dkms but it is not installable
E: Broken packages



I also tried installing the drivers manually and their installer said it was successful but it failed. 

Can anyone help?

2. Apt-get is going apt-insane
In my attempt to get my audio working i removed pulseaudio. But when i tried to reinstall them i get these messages. 

> 
Package pulseaudio is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package pulseaudio has no installation candidate


I also tried uninstalling and reinstalling ubuntu-desktop and i got the same message:
> 
Package ubuntu-desktop is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ubuntu-desktop has no installation candidate


I've tried several other things and apt-get seems to just be bugging out for some reason.  Can anyone help?

EDIT: Got it working. Had to grab another person who is using 10.04 sources.list

---

