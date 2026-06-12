---
title: "Installing Ubuntu 12.04 graphics driver"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by randnum2000 on 2012-07-01
I'm trying to install Ubuntu 12.04 on my computer. I've tried a fresh install after a guided, then manual formatting. I've downloaded the iso multiple times and tried the alternate version, but it always runs into problems at the same final step.

After installing all of the base files it gets to the part where the CD is ejected and reboots to load the final stage of installation. it's at this point that it just goes to a blank purple then black screen, I hear a notification beep like drums as if it's reporting an error but the screen is blank and then turns off.  

I'm using factory Lenovo computer AMD A6-3600 APU with RAdeon HD graphics.  6gigs ram.  I also can't connect to the internet during installation because I don't know how to configure the wireless connection manually and it doesn't detect DHCP settings. I wonder if it would download the driver on installation if I had internet connectivity and after it detected my hardware...?

I'm not sure what to do from here, I have basic Linux experience.:p 

Thanks

---

### Post by critin on 2012-07-01
Are you able to use an ethernet wired connection?  If so, hook it up before beginning the install.

---

### Post by randnum2000 on 2012-07-01
> **critin said:**
> Are you able to use an ethernet wired connection?  If so, hook it up before beginning the install.


I'm about to try that now. Do you know that this will help or are you just guessing like me? The only way this would help is if it is smart enough to detect my hardware and install the missing drivers from online. It's a long shot but we'll see what happens. 

I'm curious if anyone knows how I could install the missing drivers during installation. I'm able to see all of the install steps from the CD.

I'm also considering just buying a new stand alone NVIDIA graphics card as those are well supported and seeing if that helps.

---

### Post by critin on 2012-07-01
Wired is always better than wireless during the install--it's more sure to connect, and won't drop off.
If it's on the system will find it automatically. You can install the drivers from the desktop as soon as it's installed, after reboot.

> how I could install the missing drivers during installationNot during--no.  as far as I know.  I don't see how it's possible if you're talking of drivers that are not in the system already.

Except, it does install the nouveau driver for me because my nividia is old and won't work with the recommended driver.  It is automatic and it always works for me.

---

### Post by elliotn on 2012-07-01
> **critin said:**
> Wired is always better than wireless during the install--it's more sure to connect, and won't drop off.
If it's on the system will find it automatically. You can install the drivers from the desktop as soon as it's installed, after reboot.



Not during--no.  as far as I know.  I don't see how it's possible.

isnt the purple screen due to graphics problems? can u boot to rescue mode after grub. if u can get in u can install your graphic drivers

---

### Post by elliotn on 2012-07-01
Either hold the shift key down during boot
and select the safemode/low graphics to
boot into a GUI then install your drivers

---

### Post by randnum2000 on 2012-07-01
> **elliotn said:**
> isnt the purple screen due to graphics problems? can u boot to rescue mode after grub. if u can get in u can install your graphic drivers

Exactly, I need the graphics driver to finish setup. I'll try holding down the shift key but it actually asks me if I want to start the rescue mode when I put the CD back in. So it's not a problem of getting to rescue mode. I've just never seen the menu option for "install additional drivers" or whatever it should be called.  I haven't even searched for the driver yet. The GPU and CPU are combined in this system.

---

### Post by randnum2000 on 2012-07-04
> **critin said:**
> Wired is always better than wireless during the install--it's more sure to connect, and won't drop off.
If it's on the system will find it automatically. You can install the drivers from the desktop as soon as it's installed, after reboot.

Not during--no.  as far as I know.  I don't see how it's possible if you're talking of drivers that are not in the system already.

Except, it does install the nouveau driver for me because my nividia is old and won't work with the recommended driver.  It is automatic and it always works for me.

You can actually install driver before installation. I just went into expert mode and one of the steps is "Load drivers from removable media".

---

