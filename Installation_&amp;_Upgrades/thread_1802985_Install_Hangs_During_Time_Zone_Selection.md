---
title: "Install Hangs During Time Zone Selection"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by idlemind324 on 2011-07-12
System: Custom Built, Intel Quad Core, 8GB of RAM
Installing: Ubuntu 11.04 Desktop 64-bit from CD

Problem: During the installation my system hangs for several minutes as soon as it gets to the timezone selection screen. It eventually continues on with the installation.

Note #1: I can re-install as many times as necessary to replicate the bug or to pull any information out I can.

Note #2: Another user reporting this problem can be found [here]("http://ubuntuforums.org/showthread.php?t=1776815&highlight=Install+Hangs+Time+Zone+Selection"). My installation is doing this on a physical host.

Update #1: Is their a way to perform debugging during install that I can do to help with this. I was able to replicate it again last night.

---

### Post by ExTruckie on 2011-07-15
> **idlemind324 said:**
> System: Custom Built, Intel Quad Core, 8GB of RAM
Installing: Ubuntu 11.04 Desktop 64-bit from CD

Problem: During the installation my system hangs for several minutes as soon as it gets to the timezone selection screen. It eventually continues on with the installation.

Note #1: I can re-install as many times as necessary to replicate the bug or to pull any information out I can.

Note #2: Another user reporting this problem can be found [here]("http://ubuntuforums.org/showthread.php?t=1776815&highlight=Install+Hangs+Time+Zone+Selection"). My installation is doing this on a physical host.

Update #1: Is their a way to perform debugging during install that I can do to help with this. I was able to replicate it again last night.


System: Custom built Old Athlon XP 2900, 2G ram, 40G IDE hd for os, 320 SATA for data, 8X dvd burner for optical drive, 10.04.2LTS 32bit OS. This is a file server also.

Same situation as mentioned above. Install hangs at timezone selection. It has been 20min at this screen as I post this.  Third attempt to install. first install stopped due to a disk error. Did a disk check no errors found. next two attempts have same error. Powered down pc and restarted. Same as before.

---

### Post by MAFoElffen on 2011-07-15
> **idlemind324 said:**
> System: Custom Built, Intel Quad Core, 8GB of RAM
Installing: Ubuntu 11.04 Desktop 64-bit from CD

Problem: During the installation my system hangs for several minutes as soon as it gets to the timezone selection screen. It eventually continues on with the installation.

Note #1: I can re-install as many times as necessary to replicate the bug or to pull any information out I can.

Note #2: Another user reporting this problem can be found [here]("http://ubuntuforums.org/showthread.php?t=1776815&highlight=Install+Hangs+Time+Zone+Selection"). My installation is doing this on a physical host.

Update #1: [COLOR=Red]Is their a way to perform debugging during install that I can do to help with this. I was able to replicate it again last night.[/COLOR]
Yes there is a way to debug this...

Start up on the LiveCD and use "Try" after it boots up, double click on the Install Icon.

When it hangs at the the timezone screen.  You don't have to Cancel the install yet... Click on the top menu bar of the LiveCD Desktop on Applications > Accesories > Terminal.  In the Terminal window, type:
```

gnome-system-log &

``` Review any log you want...  I would look at NIC drivers and network resources.  Seems to me that in the install process, that is the first time it tries to make an Internet call to a timeserver.  In the LiveCD Environment you might also want to start up a browser window and see if it gets out to [www.google.com]("http://www.google.com").

Seems a lot of people get this far when they had a wireles connection and don't realise that their wireless card wasn't recognised until then...  It can be installed in the LiveCD Environment and then continue from there (If that is the case).

---

### Post by ExTruckie on 2011-07-16
> **MAFoElffen said:**
> Yes there is a way to debug this...

Start up on the LiveCD and use "Try" after it boots up, double click on the Install Icon.

When it hangs at the the timezone screen.  You don't have to Cancel the install yet... Click on the top menu bar of the LiveCD Desktop on Applications > Accesories > Terminal.  In the Terminal window, type:
```

gnome-system-log &

``` Review any log you want...  I would look at NIC drivers and network resources.  Seems to me that in the install process, that is the first time it tries to make an Internet call to a timeserver.  In the LiveCD Environment you might also want to start up a browser window and see if it gets out to [www.google.com]("http://www.google.com").

Seems a lot of people get this far when they had a wireles connection and don't realise that their wireless card wasn't recognised until then...  It can be installed in the LiveCD Environment and then continue from there (If that is the case).

I can tell you that in my case it is not the nic drivers or the connection to the web. I booted from the liveCD and set up remote desktop so I can use my wide screen monitor. I can access the desktop of the ubuntu box easily. an ever go to google and that works too.
The install still hangs at the call to the timeserver. Could it be down??? Any one know the url for the timeserver?

---

### Post by idlemind324 on 2011-07-19
I was gone on a long weekend so I just got the messages posted here. I am going to run the log during an install and see if I can narrow anything down.

---

### Post by 2F4U on 2011-07-19
I have ntp set-up on my machine and the default time server seems to be

ntp.ubuntu.com

which is reachable (at least at the time of posting).

---

