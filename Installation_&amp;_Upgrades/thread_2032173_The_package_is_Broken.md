---
title: "The package is Broken"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by labNRI on 2012-07-23
I had copied some upgrade *.deb file(s) from another machine and installed using "dpkg -i *deb". Now when I try to update my machine or install any new software,  the system complains "The package system is broken". 

Please refer to the attachment for the details.

Please help me out of the problem.

Thanks in advance,

Lab Bhattacharjee

labb$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04 LTS
Release:    12.04
Codename:    precise


 cpu
          description: CPU
          product: Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7-2600 CPU @ 3.40GH
          serial: Not Specified
          slot: CPU 1
          size: 1600MHz
          capacity: 4GHz
          width: 64 bits
          clock: 100MHz

---

### Post by Frogs Hair on 2012-07-23
Hello and Welcome 

I'm not sure if I can help , but I have a question or two . Why did you copy and install the package and not just update the other computer if both computers are online ? You wrote you had tried to update and install software so I am assuming both computers have an internet connection.

If the computer receiving the package is off line I could understand the dependency errors because all dependencies are not always included with a .deb package and are pulled from the online repository . 

Are you both computers using the same operating system and desktop environment ? If different they may have different dependencies.

---

### Post by labNRI on 2012-07-24
This machine is of 64 bit whereas the other (from where I have copied) is of 32 bit. I had to copy as this machine being in office network is not allowed to download  files whose individual size>=10 MB.  Is there any way to remove & re-install the softwares causing this breakage. 

Thanks
Lab Bhattacharjee

---

### Post by Frogs Hair on 2012-07-25
The synaptic package manager is probably the best tool for locating and removing the package and dependencies. The purge command may also work.```
sudo apt-get remove --purge insert pkg name
```

---

