---
title: "Serious problem after kernel (header) update"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by neowampyre on 2007-09-26
Hi all!
This morning I updated (using the automatic update) my operation systems, with kernel updates. I have 2 pc-s, a DELL Latitude D820 laptop with 32-bit Ubuntu, and an another one, with 64-bit Ubuntu. The desktop pc config is: 4GB Kingston RAM, Galaxy nVidia 8600 GTS, ASUS P5N-E SLI motherboard, nVidia nForce chipsets. After I reboot my computers, the Ubuntu didn't boot on both.
On blue background there was the following message:
"Failed to start the Xserver (your graphical interface). It is likely that it is not set up correctly. Would you like to view the Xserver output to diagnose the problem? (Yes)"
"Error: API mismatch: this NVIDIA driver component has version 100.14.11, but the NVIDIA kernel module's version does not match.
Please make sure that the kernel module and all NVIDIA driver components have the same version.
(EE) NVIDIA (0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA (0): that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA (0): that the NVIDIA device files have been created properly
(EE) NVIDIA (0): Please consult the NVIDIA README for details
*** Aborting ***
(EE) Screens found, but none have a usable configuration.
Fatal server error: no screens found."
And then: "Would you like to view the detailed Xserver output as well? (Yes)
-Sorry, there was a lot of details, I don't understand those...
And: "The Xserver is now disabled".

I tried to use the earlier kernel, choosing it at the startup, but it didn't help, the blue screnn appears with the message...
I can enter/boot to the recovery mode, but I don't have graphical interface :(
So, my question is: how can I rollback the latest updates (as I remember, there were 3), or what can I do to fix this?

---

### Post by Pumalite on 2007-09-26
You have to reload or recompile your video drivers depending on the method you used to install them in the first place.

---

### Post by GatorV on 2007-09-26
I'm sure you installed them via envy, so try the command:
```

sudo envy -t

```

And recompile your video driver ;-)

---

### Post by neowampyre on 2007-09-26
Solved!

Thank you Pumalite! You rock :)
I reinstalled the nVidia driver in recovery mode on both machines, and: success!!!!! :)
After the reinstall, I can use the X interface! 
I downloaded the newest drivers from the nVidia webpage, installed, and the new drivers (100.14.19) work great on both pc-s too!
Thank you Puma, and Ubuntu community!

---

### Post by Pumalite on 2007-09-26
You are welcome. Good luck.

---

