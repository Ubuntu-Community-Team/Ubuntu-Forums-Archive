---
title: "Turn off Software Updater application"
date: 2020-04-11
forum: Installation &amp; Upgrades
---

### Post by umbongodrink on 2020-04-11
Hello

Could I ask please if anybody knows how to turn off the GUI application "Software Updater"? 

I'm very happy running apt-get update / apt-get upgrade at the CLI, and would like the Software Updater application to not run automatically / by itself. The reason is that I'm running Kodi in full-screen mode (and hiding the mouse) and when the Software Updater auto-runs, it disrupts this, essentially making the mouse reappear and becoming the uppermost application in the UI. 

If anybody knows how to do the question, I'd be very appreciative. 

Thank you and good evening!

---

### Post by ajgreeny on 2020-04-11
It would help us to know which version of *ubuntu you're running, but that aside, it sounds as if you have ***unattended-upgrades *** enabled, meaning the OS will download and indtsll security packages automatically without input from you, great if you're the sort who never updates the system manually, but potentially a problem for some users who need the OS to run smoothly all the time..

I always remove that specific package, preferring to run the updates daily using terminal, in order to know what's happening in detail, and more importantly, when.  On my Xubuntu system I also disable the update-notifier utility in the autostart list, mainly because a daily update makes it totally unnecessary.

---

### Post by crip720 on 2020-04-11
Should also be settings box in software updater that you can set from daily to never for notifications.

---

### Post by umbongodrink on 2020-04-12
Thanks so much for both of your recommendations. Apologies, I should have said the version of OS I'm using, it's 18.04LTS with a 5.3.0 Kernel. 

I have uninstalled "unattended upgrades". 
I think I have disabled the automatic updates by following the CLI instructions here: [https://linuxconfig.org/disable-automatic-updates-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/disable-automatic-updates-on-ubuntu-18-04-bionic-beaver-linux)
I have also edited the autostart list to turn off the update-notifier utility using the instructions here:
[http://ubuntuhandbook.org/index.php/2019/06/list-all-startup-applications-services-in-ubuntu-18-04/](http://ubuntuhandbook.org/index.php/2019/06/list-all-startup-applications-services-in-ubuntu-18-04/)
(Is this ok ajgreeny? Anything else that I should add?)

Thanks too crip720, I have done that as well. 

Have a very nice day.

---

### Post by ajgreeny on 2020-04-12
I'm pretty sure everything should be OK for you having done all that.

Let it go for a few days and if is well please mark as SOLVED from the Thread Tools menu up-top.
It is a great help to other users searching the forum.

---

### Post by mastablasta on 2020-04-14
> **umbongodrink said:**
> 
I have uninstalled "unattended upgrades". 


but this service is CLI based and runs in the background. it doesn't touch the GUI and doesn't need it.

---

### Post by CelticWarrior on 2020-04-14
> **mastablasta said:**
> but this service is CLI based and runs in the background. it doesn't touch the GUI and doesn't need it.

Yes, but if it's running and finds updates it pops up a GUI, which is what the OP is trying to avoid. ;)

---

### Post by ajgreeny on 2020-04-15
The whole point of unattended-upgrades is that it happens without action or notifications to the user; it all happens in the background, possibly slowing other processes, which I think is the OP's situation.

---

