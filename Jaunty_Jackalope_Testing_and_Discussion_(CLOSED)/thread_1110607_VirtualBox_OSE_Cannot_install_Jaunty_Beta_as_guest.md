---
title: "VirtualBox OSE: Cannot install Jaunty Beta as guest"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrew.46 on 2009-03-30
Hi,

I am installing a fresh iso of Jaunty beta after successfully running most of the alphas as guest with VirtualBox 2.1.4_OSE. The installation gets to 95% or so and then reboots and logs on as generic user again and asks me if I wish to install. Anybody else with this problem?

Andrew

---

### Post by roastpotato on 2009-03-30
I have a similar problem, when it reaches 90 percent (Detecting Hardware) on virtualbox (non-OSE) it either quits the installation and goes back to the live session or restarts with the installation incomplete.

---

### Post by andrew.46 on 2009-03-30
Hi roastpotato,

> **roastpotato said:**
> I have a similar problem, when it reaches 90 percent (Detecting Hardware) on virtualbox (non-OSE) it either quits the installation and goes back to the live session or restarts with the installation incomplete.

Glad it is not just me then :-). I am attempting a new install with a recompiled VirtualBox and a few different installation options but I don't like my chances.

**[COLOR="Black"]Edit:[/COLOR]** Exactly as in your case the process dies at 'Detecting Hardware'. First the system freezes and then reboots to 'Live User' leaving about 2.3 gigs of failed installation.


Andrew

---

### Post by itsStephen on 2009-03-30
I can get the install to finish but then it will just load the live user. When I restart I just get a black screen with a white line on it which makes me think that it didn't actually install and left 2.3gb of fail.

---

### Post by saboritsu on 2009-03-30
Me too. My problem is very much the same as roastpotato has.

---

### Post by andrew.46 on 2009-03-31
Hi,

Well I have had success of a sort. I added:

```
Section "ServerLayout"
       Option "AutoAddDevices" "False"
EndSection
```

to xorg.conf which meant that hardware detection (hot plugging disabled at least for the installation) was a little off and xorg needed to be reconfigured after reboot but the system is now up and running.

It is all a little dodgy so I would advise people to find a better method :-). Or at the very least be prepared for unpredictable results with this method.

Andrew

---

### Post by andrew.46 on 2009-03-31
Hi again,

Woooo hooooo!! Guest Additions up and running as well !!! Just had to alter the install.sh file as is [well documented now]("http://www.ubuntugeek.com/ubuntu-904jaunty-and-virtualbox-video-driver-for-xguest-additions.html").

Andrew

**Edit:** Hi Moog!!!

---

### Post by saboritsu on 2009-03-31
Thanks, Andrew!

---

### Post by andrew.46 on 2009-03-31
Hi saboritsu,

> **saboritsu said:**
> Thanks, Andrew!

This worked for you or are you just hopeful :-).

Andrew

---

### Post by Wraith's Hand on 2009-03-31
Thanks for the link.  I was able to get Jaunty Beta installed with no problems until I tried adding the guest additions.  Hm.  Now I wonder if I can fix the the virtual machine or if I am going to have to start over.

---

### Post by jespdj on 2009-03-31
I had something similar the first time I installed 64-bit Jaunty Beta on VirtualBox 2.1.4 running on 64-bit Hardy.

I noticed that the checksum of my Jaunty ISO image was incorrect, so I downloaded it again, made the ISO image on my harddisk read-only, and then it did install without problems on VirtualBox.

Thanks for the VirtualBox video driver fix; I also noticed that I couldn't get the VirtualBox video driver to work.

---

### Post by saboritsu on 2009-04-01
> **andrew.46 said:**
> Hi saboritsu,



This worked for you or are you just hopeful :-).

Andrew
Hi, Andrew. It worked perfectly for me, thank you!

---

