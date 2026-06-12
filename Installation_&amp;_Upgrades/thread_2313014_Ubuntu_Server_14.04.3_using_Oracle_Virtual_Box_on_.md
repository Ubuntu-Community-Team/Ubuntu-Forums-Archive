---
title: "Ubuntu Server 14.04.3 using Oracle Virtual Box on Windows 10"
date: 2016-02-09
forum: Installation &amp; Upgrades
---

### Post by nordy on 2016-02-09
[COLOR=#111111][FONT=Ubuntu]I'm trying to install Ubuntu Server on a Windows 10 Machine using Oracle Virtual Box 5.0.12 r104815, but cannot get past the "Select and install software" step.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried running Virtual Box as Administrator, and a whole lot of other things, but nothing works.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
The ISO Image i'm using for the install ubuntu-14.04.3-server-amd64.iso is on drive C:\ of my laptop. The MD5 of the ISO I've downlaoded matches the one supplied by Ubuntu. I've also checked the ISO using the Verify CD-ROM option that appears during startup.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
What could I be wrong here? No step after "Select and Install Software" will work

.[/FONT][/COLOR][ATTACH=CONFIG]267195[/ATTACH][ATTACH=CONFIG]267194[/ATTACH][ATTACH=CONFIG]267193[/ATTACH][ATTACH=CONFIG]267192[/ATTACH]

---

### Post by QIII on 2016-02-09
Hello!

What happens if you set up your VM to use the optical drive as a pass-through and attempt to install from optical media?

You'll have to burn the iso to the media (NOT just copy it.)

Typically, installing from the iso on magnetic media works just fine and is substantially faster.  But let's see if this works as a diagnostic tool.

---

### Post by nordy on 2016-02-09
I'll try. I was able to install a previous version of Ubuntu Server using an ISO located on my HDD. But that was on Windows 7.

---

### Post by nordy on 2016-02-09
I'm doing all this on a SSD. Could that be the problem?

---

### Post by QIII on 2016-02-09
I always install from an image on HDD.  But let's see if this works.

---

### Post by QIII on 2016-02-09
I have a Win10 guest running on an SSD on Kubuntu, so I'm inclined to believe that the SSD is not a problem.

---

### Post by mastablasta on 2016-02-09
if you can't figure it out use one of bitnami stack virtual appliance images. you just extract it and open it with vbox...

otherwise i too had issue with latest server install, but for some reason it suddenly proceeded on reboot and another retry at install. 

in any case you can try ubuntu minimal iso and install things on that. 

the pictures you provided do not reveal much information which is why we are all guessing as to what might have gone wrong. select and install software is basically the tasksel installer right? so you select the software but it doesn't proceed to next step to install it. and virtual box machine does have the internet connection (it is connected to internet?)?

---

