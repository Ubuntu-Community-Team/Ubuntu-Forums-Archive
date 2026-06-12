---
title: "Installtion difficulties"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by perika on 2010-04-18
Hello,

I can't install the beta. I've tried several daily builds, and controlled the check sum.  The installation begins normal but after the first screen where I select language etc, the screen goes blank. I have a Nvidia card and run through my TV screen, hooked up via S-video.
Installation of previous version (9.10) worked without problem.
Thanks,

Per

---

### Post by ronparent on 2010-04-18
This may be more than you bargained for,but, many people including myself, have benn initialy unable to install with similar symptoms. To overcome this type freeze often requires that you hit <F6> after the language screen on the live cd. This brings up a list of booting options that you can enable or disable. The most likely suspects are the apic lapic dmraid and nomodest. To get things going you could select all of them - moving to them with the up/down arrows and secting them with the space bar. If it still doesn't come up try rebooting and doing the same thing again. But this time additionally hit the <end> key which will move the cursor to the end of the boot line boot parameters. Use the back arrow to move to the end of the 'splash' parameter and then use the backspace key to erase it. In most cases adding or deleting one or more of these parameter will free the system to boot. Post here if you have further need.

---

### Post by perika on 2010-04-18
Hi, thanks. Unfortunately it didn't work fully... It now begin the installation process, and I can see "ubuntu" with the red dots. After a while it just stops. Any other ideas?
Thanks,
Per

---

### Post by dino99 on 2010-04-18
> **perika said:**
> Hi, thanks. Unfortunately it didn't work fully... It now begin the installation process, and I can see "ubuntu" with the red dots. After a while it just stops. Any other ideas?
Thanks,
Per

so installation is complete but freeze/hang with plymouth ?

try with console to uninstall plymouth or try to boot by adding nomodeset and/or acpi=off and/or lapic=off and/or apic=off on the boot line ( can remove quiet splash too)

---

### Post by perika on 2010-04-19
Hello again, 
tried this as well, and I can now follow whats happening. The installation hangs at "Setting sensor limits"

Thanks,

Per

---

### Post by ranch hand on 2010-04-19
The RC is due out Thursday and if you are using the Beta Image try the daily build it is more up to date.

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

