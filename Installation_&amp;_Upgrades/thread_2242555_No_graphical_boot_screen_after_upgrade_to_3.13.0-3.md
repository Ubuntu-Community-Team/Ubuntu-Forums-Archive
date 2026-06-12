---
title: "No graphical boot screen after upgrade to 3.13.0-35-generic"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by dkuhlman2 on 2014-09-02
This morning I did:
```
$ sudo aptitude update
$ sudo aptitude full-upgrade
```
That installed 3.13.0-35-generic.  When I re-booted, I do not get a graphical log-on screen.  It's just an entirely black screen.
Linux seems to be running OK, because I can switch to a plain text terminal screen (with ctrl-alt-F1), and do everything I'd expect to be able to do there.
I can also re-boot and select 3.13.0-34-generic (the previous version of the kernel), and when I do I get the normal graphical log-on screen.
I'm using the drivers from AMD (amd-driver-installer-14.10.1006.1001-x86.x86_64) because with the AMD A8 APU in this machine, I could not run the desktop (GNOME or XFCE) until I installed those drivers.
And, I'm running Ubuntu 14.04.1 LTS.
Is there something I can try or some place where I should report this?
Dave

---

### Post by QIII on 2014-09-02
Hello!

Since you are not using the driver from the repo, did you uninstall the driver before updating the kernel?

---

### Post by Mark Phelps on 2014-09-02
> I'm using the drivers from AMD (amd-driver-installer-14.10.1006.1001-x86.x86_64) When you install that way, you lock the drivers to a specific kernel version and MUST then uninstall those drivers before you update the kernel.  IF you don't, you get the problem you have now.  If you follow the instructions in the thread to remove the drivers, you can then reinstall them: [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch")

---

### Post by dkuhlman2 on 2014-09-03
Thanks for help with this.  Following the suggestions above, I uninstalled and then re-installed the drivers.  That seemed to fix the issue.  I'm now using the 3.13.0-35-generic kernel.

So, next time `aptitude full-upgrade` offers to upgrade my kernel, I'll try to remember to uninstall those drivers first, then upgrade, then re-install the drivers.

For notes on the drivers, including how to uninstall them, see this: [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx).  To uninstall the drivers, I booted into fail-safe mode, then did `[COLOR=#000000][FONT=Calibri]sudo aticonfig --uninstall`, then rebooted.[/FONT][/COLOR]

One question:  Why do I have to use those AMD drivers at all?  Is it because the Ubuntu Linux kernel does not support the AMD A8 APU?  Should I report that problem to Ubuntu?  And, if so, where should I file that report?

Thanks again.

Dave

---

### Post by Bashing-om on 2014-09-03
Dave;

In respect to:
> 
One question: Why do I have to use those AMD drivers at all? Is it because the Ubuntu Linux kernel does not support the AMD A8 APU? Should I report that problem to Ubuntu? And, if so, where should I file that report?


One understands that the 'driver' is but the interface between the actual chips that control the graphics and the software. Now depending on what the software requires is how the driver performs. In my case AND in my use case, I find that the open source drivers for ATI perform better than the proprietary drivers. Particularly now as release 14.04 had enhanced support for graphics drivers.

Only you can say why you chose to install the graphics driver from OEM, you can try the open source driver or the repository drivers and see if they meet your needs. ( uninstall, and -> the "Additional Drivers" utility ) You too may be pleasantly surprised.

no one else knows ubuntu like the developers of ubuntu

---

