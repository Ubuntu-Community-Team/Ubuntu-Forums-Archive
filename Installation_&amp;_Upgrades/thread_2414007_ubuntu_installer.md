---
title: "ubuntu installer"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by boregard on 2019-03-04
Hi,I was thinking of moving from Ubuntu 16.04 to 18.04. In the past i never got ubuntu installer to just work.I always had to partition the drive and install it.Just wondering if Ubuntu installer is working any better now? Thanks

---

### Post by kc1di on 2019-03-05
18.04 installer works fine here.  Not sure what your asking,  If the installer partition page doesn't work for you , it's usually a hardware issue. not the installer. Anyway had no problems with 18.04 partitioning on several machines.

---

### Post by ajgreeny on 2019-03-05
I am also not sure what your problem is so please tell us if you want to use specific partitions for the OS, ie reuse your 16.04 partitions, or simply do a full install to the whole disk.
Is this a single OS system or do you already have, and wish to keep, another existing OS?

---

### Post by boregard on 2019-03-06
sorry for taking so long to reply back. you know when using live cd then it ask do you want to install alongside another os or just install ubuntu by itself? well every time i chose to  install ubuntu only ,it would install ubuntu but i never could get it to boot up. only way i could get it to work was to partition hd with gparted and have 1 mb un formatted space on hd. i guess my question is can you choose to let the live CD just do the installation now. for some reason i never had any luck letting live cd install on efi machine. hope this clears up what i am wanting to know. thanks

---

### Post by ajgreeny on 2019-03-07
If you boot the install USB in UEFI mode you should be able to install using the default partition arrangement; when booting the USB there will usually be two options, one with UEFI at the start of the USB and a second without the UEFI.  Make sure you choose the one that uses UEFI.

The mode in which you boot the USB is the mode in which the OS will be installed and if you have a UEFI firmware machine it must be booted in UEFI mode.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for a lot more info about UEFI vs MBR.

---

### Post by boregard on 2019-03-07
thanks, ajgreeny. i ll try that. probably what i have been doing wrong,

---

