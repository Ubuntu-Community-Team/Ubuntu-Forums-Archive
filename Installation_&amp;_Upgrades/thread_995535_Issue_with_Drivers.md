---
title: "Issue with Drivers"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by ZeeM on 2008-11-27
Hi i just installed Ubuntu 8.04 Desktop edition and am having issues with my drivers, my Mobo does not recognize that my Internet cable is plugged in, so i am looking for a way to fix this or the correct driver to install because i could not find it. My Mobo is Gigabyte GA-K8N Pro-SLI

thanks

---

### Post by inobe on 2008-11-27
tell us about your your modem' is it a usb modem ?

include the model and make of the device ....


next time please include as much information as possible, otherwise we are left to guess !

:)

---

### Post by ZeeM on 2008-11-28
i have a linksys broadband router the model number rt31p2-na, however i dont think that the issues lies there because when i plug it into my laptop which also runs the same version of Ubuntu i don't have any issues which is a Dell Inspiron E1505 which did not come with Ubuntu originally

---

### Post by inobe on 2008-11-28
does your connection work when you use a live cd ?

---

### Post by ZeeM on 2008-11-28
no

---

### Post by inobe on 2008-11-28
i am not understanding why your having complications !


plug in the ethernet cable then reboot the system..

---

### Post by ZeeM on 2008-11-28
tried that multiple times, i think that when i installed Ubuntu my MoBo stopped recognizing my Ethernet cable. which is why i am looking for a driver for my motherboard, which so far i have not found, cause i am most likely looking in the wrong places. If that is not the issue then i am stumped, and who should i ask for help?

---

### Post by inobe on 2008-11-28
in the bios' is onboard lan disabled ?

---

### Post by ZeeM on 2008-11-28
how do i check for that

---

### Post by inobe on 2008-11-28
upon restarting you should see a gigabyte bios splash screen, start tapping f2, if that is not the key' the splash screen should say which key to press to enter setup.


if onboard lan is enabled' i will assume you need to use ndiswrapper.

---

### Post by ZeeM on 2008-11-29
yeah that did not work there were not issues with that the lan is enabled its just that it does not recognize that it is there

---

### Post by inobe on 2008-11-29
we need to get that system online somehow, do you have the wireless card that comes bundled with that board or at least a wireless usb adapter ?

we can try and gather some information, also get the system updated.

another thing that bothers me, those drivers are opensource and are included in the kernel for more than a year now...

[http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

i am still wondering why this is happening.

---

