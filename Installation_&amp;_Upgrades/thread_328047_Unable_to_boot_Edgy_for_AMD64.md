---
title: "Unable to boot Edgy for AMD64"
date: 2006-12-30
forum: Installation &amp; Upgrades
---

### Post by am4c130d on 2006-12-30
Hi,

I upgraded a fully functional, clean AMD64 Dapper install based MythTV front end to Edgy, mainly to use the MythTV packages from the standard OS.  

Here is a lot of background to ensure I give as much information as possible.  I didn't use the "official" process having upgraded by modifying the sources.list and aptitude dist-upgrade for three or four years from Debian to Ubuntu etc. and being very comfortable with this process.  The upgrade completed as expected, with one new failure message (I don't have all the details) referring to a udev issue.  It finally stopped as part of the X upgrade, as I always forget to kill X first - this happens to me every time.  As per usual I rebooted the system ready to run aptitude dist-upgrade again, however the system did not come back up, it was hung on the Ubuntu splash screen with the progress bar at zero.  Using <ctrl> <alt> <f1> to try and get to a command prompt all I got was a partial boot status, the last status line was related to VGA FB.  I rebooted and choose the 2.6.15 kernel from Dapper to try and get the system up, this too froze mounting the root partition.  In both situations there was no command prompt to get to.  Recovery mode was also unable to boot.

I created a Live Desktop CD of the AMD64 distribution, and that froze at the same spot as the upgrade from the HDD.  Using a Dapper AMD64 Live Desktop CD worked fine.  As I wanted an Edgy install for the MythTV packages as I mentioned, I tried an x86 Live Desktop CD, and this worked fine, so I installed this without a problem (though its very slow).

I didn't drop to the command prompt as the local screen is a poor quality TV and not a monitor, it's pretty much useless for reading text on screen.

Of course all my configuration information was lost in the upgrade, but as it is a front end to a Myth only, this was not a great deal of hassle for me.  

The only real issue I've come across is that pressing the power button no longer shuts the system down, it simply brings up the logout/shutdown window in Gnome - which is a big retrograde step for me.

<EDIT>  This proved to be different default action in Gnome - changed under Power Management addressed the problem </EDIT>

This install failure is the first major issue I've had with Ubuntu, and have been pretty abusive in upgrades, such as from Debian unstable to Debian stable to Ubuntu hoary to Ubuntu breezy to Ubuntu dapper on other systems and had the usual package mismatches and messed up config files, all of which were easy enough to recover from - this was the first time I have had to give up and had to resort to "desperate" measures.

The real problem I see is that there is no avoiding upgrading to Edgy, unless one wishes to stay with Dapper forever, perform a clean installation or move to another distribution.  Ubuntu doesn't support jumping over versions for upgrades so upgrading to Edgy is a requirement - as such I would consider this a show stopping bug for Ubuntu.

Unfortunately I have no solution for anyone - and as I've got a working system I won't be retracing my steps to reproduce the problem - more of an informational update.  To my mind Edgy appears to have some serious upgrade/install issues with some systems, in my case an AMD64 based platform.

My system is an ASUS M2NPV-VM, with 1 G of DRAM, AMD Athlon X2 3800, 80G WD PATA HDD and a Plextor DVD/CD RAM.  Graphics is Nvidia G150 onboard.

Thanks

Alan

---

### Post by jonathan.hofman on 2007-01-05
I also have an ASUS M2NPV-VM and had the same problem. I could fix the problem by selecting 'kernel 2.6.15-26-amd64-generic' during boot. I changed the default boot item in /boot/grub/menu.lst. Unfortunately I do not know why the change works and the default setting hangs.

---

