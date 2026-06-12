---
title: "Sequel to upgrading accident"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by Thrasyllus on 2008-10-22
I upgraded to 7.10 last Saturday - I know, I left it to the last moment - and the files all downloaded without incident. Then came the installation/configuration phase and in the middle of that there was a two-minute POWER FAILURE (damn Hydro-Québec!) When I rebooted the system was a bit stilted - half Feisty, half Gutsy - but it was working. 
 
So as root I did **apt-get update** followed by **dpkg --configure -a** and rebooted. The system did some more configuring on its own initiative after I logged in and everything seemed fine. 
 
But then I got my first update notification as a 7.10 user - some time zone stuff (tzdata version 2008g-0ubuntu0.7.10 to 2008h-0ubuntu0.7.10). After clicking on the update button and watching what seemed like a normal download, I got the following messages: 
 
[B]E: acpid: subprocess post-installation script returned error exit status 1
E: acpi-support: dependency problems - leaving unconfigured
E: powermanagement-interface: dependency problems - leaving unconfigured
E: ubuntu-desktop: dependency problems - leaving unconfigured[/B]
 
Is this a consequence of my accident? Did I omit something when recovering and continuing the installation process? What to do?
 
I also get error messages I never saw before whenever I use *evince* - **cairo context error: NULL pointer** repeated four times. Other than that, *evince* works normally.

---

### Post by cariboo on 2008-10-23
Try:

```
sudo apt-get install -f
```

This might fix the problem.

As for your problem Hydro Quebec, there not much you can do about that, except purchase an inexpensive ups.

Jim

---

### Post by Thrasyllus on 2008-10-23
Thank you Cariboo! Williams Lake BC, I presume. Axel
 
PS - I should add thanks to Linux - can you imagine installing Windows through a power failure?

---

### Post by jalirious on 2008-11-04
Seems that the evince bug is inherent. No printing and a repeated 

Cairo context error: NULL pointer

error following the last evince update.

---

