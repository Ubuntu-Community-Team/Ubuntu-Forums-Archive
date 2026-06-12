---
title: "Lubuntu 15.04 goes into standby during install"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by diogenes_3 on 2015-10-25
I have an old Notebook, a Clevo 888E with Pentium 4, ATI Mobility Radeon 9000, 512 MB RAM. It runs XP.

When I try to install Lubuntu 15.10 from CD, I get as far as the first graphic screen after the language selector and the "install Lubuntu" selector. It adds dots under the logo for a while, and then it goes into standby, in the middle of CD/disk activity. When I hit any key, it promptly comes back, but it keeps going into standby, at random intervals down to seconds, so it never quite gets into swing again. The BIOS has only rudimentary power management settings, and they don't make a difference. 

I tried verifying the CD (alright) and the memory (alright). Also Windows still runs nicely.

---

### Post by mörgæs on 2015-10-25
Have you tried the [alternate 15.10 ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

Remember to use wired internet access while installing.

---

### Post by grahammechanical on 2015-10-25
One of the things that I find frustrating when installing Ubuntu and any of the flavours is that "Turn screen off when inactive for" is enabled. I always forget to disable it before starting the installation and I have to wiggle the mouse from time to time.

Try setting "Turn screen off for" to never and then do the install. This will confirm that it is not the screen brightness setting that is activating. Laptops and notebooks power down to save battery life. Could this be happening?

Regards.

---

### Post by diogenes_3 on 2015-10-26
I guess the alternate it will be. Running low on empty DVDs... Wired internet is obvious on such ancient machine.

---

### Post by diogenes_3 on 2015-10-26
I tried to switch off what I could in the BIOS, though it only appears to reference shutting down the HDD. It wasn't just turning off the screen, it was really bringing the system to standby (power LED goes to blink). And all the mouse wiggling and any-key-hitting (I use shift so as not to signal anything obviously) didn't stop it from going to what it thought was sleep. Though anyway it was in no way inactive.

---

### Post by diogenes_3 on 2015-10-26
The alternate install succeeded. On its first startup of same graphical screen as before, the standby thing immediately happened again. Thankfully the system was fast enough now to proceed to login screen after "waking up" again. Then, once logged in, it was working normal. So, I guess the status is "solved" as in "it went away", though not "solved" as in "I understood why it happened so I learned for the future".

---

