---
title: "Nvidia drivers causes Black/Blank Screen at login"
date: 2006-12-05
forum: Installation &amp; Upgrades
---

### Post by taco-man on 2006-12-05
Whenver i install the Nvidia drivers after i reboot i will not be able to login as the screen is blank.

i have:
BFG Geforce 6600
Brand new installation of Ubuntu 6.10 (with newest updates)
i have the normal x86 version of ubuntu NOT the 64-bit version

i have tried getting installing them from the repository as well as from the nvidia installer script. i have also tried using older drivers (8776) as i saw this recommended somewhere and figured i might as well give it a try. After installing the drivers the only way to be able to login again is by removing them and switching back to the nv drivers.

ive tried method 1 and 2 from this link -> [http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

somebody please help me i dont know what is wrong and have been trying to figure this out for a few days. Thanks in advance

---

### Post by 7infinity on 2006-12-08
I have the exact same problem, with an Nvidia GeForce4 MX 460. It worked fine with an earlier distribution.

---

### Post by 7infinity on 2006-12-08
Okay, at least for my case, I figured this out. The problem was that the binary nvidia driver provided by the linux-restricted-modules package was compiled for a different kernel version than what I am running. I saw this in the Synaptic when I expand the "Installed Version" column wide enough. This would seem to be a repository error. Anyway, I removed the restricted package then used the Nvidia installer from their website to compile a driver as they instructed and ran their setup script. Now it works.

---

### Post by zneastman on 2006-12-08
You have got to be freaking kidding me.  Ubuntu's a great distribution, and I don't mind finding bugs in bleeding edge software, but a version mismatch that leaves a machine unusable?  Come on.

---

### Post by sqeaky_topp on 2006-12-09
I am having a similar issue. When using the nvidia drivers my screen will intermittently go blank, and the machine will be very locked up (no keyboard response, no ssh access). I was under the impression that a kernel module simply couldn't be loaded in the event of a version mismatch. If some how it did load, I would assume error catching of some kind would prevent it from working, or it would crash immediately, however I have been able to log into my machine, start playing doom3, and make significant progress before getting the error.

I too see in synaptic where it states the version mismatch, I am just wondering, how my machine functions at all?

---

