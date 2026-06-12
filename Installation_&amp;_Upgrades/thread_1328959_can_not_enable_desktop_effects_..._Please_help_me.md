---
title: "can not enable desktop effects ... Please help me"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by brijith on 2009-11-16
Hai all,
I installed Ubuntu 9.10 few days ago and installed some software of daily use. The desktop effects were working fine initially....Two days after installation Update manager came up with some updates. I installed the updates. After that update when I restarted I found that desktop effects are not working..
When tried to enable through System->Preferences->appearance window. It says "Could not enable desktop effect"...I don't know what Happened...

Please help me ....


[COLOR="Sienna"]**Thanks In Advance **[/COLOR]

---

### Post by darco on 2009-11-17
Try re-installing your vid drivers, worked for me.


darco

---

### Post by brijith on 2009-11-17
> **darco said:**
> Try re-installing your vid drivers, worked for me.


darco

My driver is ```
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
```

How to reinstall it ...

Thanks for you reply ... :D

---

### Post by brijith on 2009-11-18
Hi,
I got it solved. somehow wrong divers got installed.... 
I removed the drivers and restarted my system ....
And it worked ....
Thanks to the one who helped through Ubuntu IRC
:D

---

### Post by RjNeLLY on 2009-12-10
HI! Im running through the same problem!!, i may also have to reinstall my drive but dont know how to go about doing that!:(  Can anyone help me PLEASE!!:P

---

### Post by brijith on 2009-12-10
> **RjNeLLY said:**
> HI! Im running through the same problem!!, i may also have to reinstall my drive but dont know how to go about doing that!:(  Can anyone help me PLEASE!!:P

Take Synaptic package manager and search display driver. It  will list all the display drivers available (you can find some installed and some not installed) remove everything starting with nvidia and reboot your system.

Note:- When I solved the issue in my system there was some one from ubuntu IRC who guided me. He asked me to run lots of command to see its out and then he suggested me to remove certain packages. I don't remember those command exactly. What I learned from it was, Ubuntu will automatically install the required driver. If some how the wrong driver got installed and display is not working as expected then the solution is to remove the display drivers installed and reboot. While booting Ubuntu will search for the correct display driver and install it..

---

