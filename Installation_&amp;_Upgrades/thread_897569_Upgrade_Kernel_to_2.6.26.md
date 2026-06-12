---
title: "Upgrade Kernel to 2.6.26"
date: 2008-08-22
forum: Installation &amp; Upgrades
---

### Post by nolanzoe on 2008-08-22
My kernel is: 2.6.24-19

I noticed a new Linux Kernel on [www.Linux.org](www.Linux.org)  I downloaded the package and the Patch but could not install it. I unzipped them and put them in my folder and ran sudo apt-get install ...(directory path)  error message said it couldn't find package. 

I find the Linux instructions to be convoluted and unclear sometimes.

Can someone provide simple instructions on where to place the file and what commands to run to get them unzipped and installed???  Should I apply the patch or the upgrade???


Also what Jukebox do you recommend????????

---

### Post by mordak13 on 2008-08-22
I too would be interested in advice on this upgrade. I'm running 2.6.24-22 currently.

---

### Post by livestockPimp on 2008-08-22
"apt-get install" is used for installing packages from "apt" this is a package repository.

If you have a .deb file that you are trying to install you install it with "dpkg -i packagename.deb".

I am guessing you downloaded the source though and this is a .tar.gz.
to install this you need to use "tar -zxvf file.tar.gz" and extract it and then use "./configure", "make menuconfig", ect, ect.

If you have not built a kernel and do not need the latest kernel I would avoid this since generally there can be problems and if you break the kernel the system will not boot making the process of recovery alot harder.

---

