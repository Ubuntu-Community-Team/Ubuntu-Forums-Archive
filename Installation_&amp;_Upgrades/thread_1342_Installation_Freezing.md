---
title: "Installation Freezing"
date: 2004-10-20
forum: Installation &amp; Upgrades
---

### Post by matt-j on 2004-10-20
Hi

I'm having a bit of trouble installing to my HP NX5000 laptop.

The installation of the base system goes ok, it even finds my wireless network - wow!, then it reboots and runs the base configuration.

The configuration stops at:

Setting up gstreamer0.8-cdparanoia (0.8.5-1ubuntu2) ...

I have tried running the install a bunch of times, but it always freezes at the same point, just incase it was a bad cd i installed on a different pc and it went ok.

Any ideas?

Cheers
Matt

---

### Post by Rancoras on 2004-10-20
At first glance, I suspect a bad burn on the CD.  Have you tried burning a new one?

---

### Post by matt-j on 2004-10-20
Yeah I burned another one - same problem, and they both installed ok on anaother pc i have.  i'm currently downloading the iso again just incase.

---

### Post by matt-j on 2004-10-20
OK I've tried another iso, still getting stuck.  I've noticed that its getting stuck just after HAL gets set up and started.

Any ideas?  Has anyone managed to get ubuntu on a nx5000?

---

### Post by FLeiXiuS on 2004-10-20
This has been a comon issue, is it the new 4.10 warty release?

---

### Post by knappen on 2004-10-21
Are there more than one release?

---

### Post by knappen on 2004-10-21
Just realised that there is a new release out as of yesterday.

Oooops...

---

### Post by matt-j on 2004-10-21
---- This has been a comon issue, is it the new 4.10 warty release? ----

Yeah, I've been trying the warty-rc-install-i386.iso for the last couple days, i downloaded the warty-release-install-i386 last night but that is doing the same thing.

---

### Post by FLeiXiuS on 2004-10-23
I would consider moving to another program until this problem is fixed, im not sure of the problem, is there any logs you can provide me with?

Other Mutlimedia Players
- Xmms
- Google some others, xmms is my fav!   ;)

---

### Post by matt-j on 2004-10-23
FLeiXiuS, i can't use another program unless I can get the OS installed.  I don't think it is gstreamer that is causing the install to freeze.  From looking at the way the install stops at the same spot each time, just after HAL starts, it seems that HAL is causing the machine to lock up.

---

### Post by 3rdOne on 2004-10-29
Hi,
  
   I am using a Compaq Presario V1040 laptop. I was also facing the same
problem. After doing several installations in the past two days I
figured out the same thing as you that HAL is the culprit. So, finally
this is what I did.
   Installed Ubuntu with custom settings. This creates a simple text
based system. Later ran aptitude to select all the packages that
I needed. You only need to disable HAL and gnome-volume-manager
which depends on HAL. 
   After that the system is working fine. Hope that helps you.

Thanks.

---

### Post by toxxic on 2005-01-21
Hello

youst solved this Item for my HP NX5000
use as Bootparameter pci=noacpi

---

### Post by adamslade on 2005-02-15
What are the side-effects of not having HAL installed, because my laptop keeps reinstalling it, and then it won't run.  If I uninstall it and everything that depends on it, it runs but keeps complaining that HAL isn't installed, and some things such as sound aren't working.

---

### Post by littlepaul on 2005-02-28
in our german forum we also had  similar problems with an medion 42200. Both user mentioned that the installation was freezing when hal started or gstreamer was in process to be installed. Both tried to install with warty, hoary (or even with sarge) several times but the installation failed every time. They also tried all documented boot parameter. One user found an workarround and this method worked for both.
During the installation activate the internet connection and enable the option to download and install the packages directly from internet server.

---

