---
title: "sudo ltsp-build-client command fails"
date: 2006-08-31
forum: Installation &amp; Upgrades
---

### Post by edkey on 2006-08-31
I am running edubuntu 6.06 lts and for some reason the ltsp client portion of the install failed and my screen whent black. The install still continued. Upon reboot, everything was fine except for the opt/ltsp/i386 folder. I tried booting a client via PXE and the dhcp server portion was working, I recieve an address and it started booting. Upon loading the kernel, it failed. 

I assumed it was because of the install that failed on me, so I first:

**sudo rm -rf /opt/ltsp/i386 **

and then

**sudo ltsp-build-client**

Upon installing the packages, it again failed and my screen went black loging me out of the system. When I loged back in, the install/rebuild did not complete. Any ideas why the build client fails? 

I do have experience with installing ltsp servers and clients. I have set up over a dozen configurations with all types of hardware. I imagine this to be a hardware issue. 

My system is a Toshiba Tecra A3, dual boot with winXP, centrino processor.

---

