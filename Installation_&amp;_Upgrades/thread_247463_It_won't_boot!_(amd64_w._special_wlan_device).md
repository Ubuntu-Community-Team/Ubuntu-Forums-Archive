---
title: "It won't boot! (amd64 w. special wlan device)"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by martinrandau on 2006-08-30
My girlfriend has bought a fancy new HP Pavillion dv6000 with AMD Turion 64-bit. It has one of those buttons to turn on/off the wireless network device. 

She wants ubuntu on it, so I try to boot it with the amd64 cd. The wlan device is turned off. The boot goes fine until it comes to "~setting up enterprise volume managment". Then it hangs and I have to reboot. This time I try to turn on the wlan device (located on the front of the computer) and it stops at "configuring network interface" (the step after the enterprise volume managment step). 

I think the problem lies in this wlan device. Does anybody know how to overcome this problem? 

I am thinking that I either should pass some parameter to the kernel about skipping the network configuration - is there such an option?

I could also try to plug in an ethernet cable and hope that the kernel skips the wlan device (then I first need an ethernet cable, which is why I haven't tried this yet.

Any help is appreciated!

edit: It boots with acpi=off but then the sound doesn't work. I will install it as a 32-bit system

---

