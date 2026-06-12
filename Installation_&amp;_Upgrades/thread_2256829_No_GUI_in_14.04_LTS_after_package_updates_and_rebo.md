---
title: "No GUI in 14.04 LTS after package updates and reboot"
date: 2014-12-15
forum: Installation &amp; Upgrades
---

### Post by jweiner on 2014-12-15
Dear Forum:
I had 14.04 up and running for months with no problems.  Then, after several weeks of inactivity, I turned on my PC and rebooted (with no problems) and used the update manager to install new packages that had accumulated during the period of inactivity.  After the installation I was prompted to reboot, which I did, but now I get the black screen with a blinking curser in the upper left corner.  The system DOES boot in text mode, so I attempted the command "xstart", which resulted in the same problem black screen.  Clearly the problem is in the X session.  In the boot options, prior to booting, the video driver is "on chip" and this has always worked in the past.  In my .xsession-errors file I see a number of messages beginning with "Script for bus started at run_im", Script for auto started at run_im", Script for default started at run_im", then "init: upstart-event-bridge main process (1544) terminated with status 1","init: upstart-even-bridge main process ended, respawning", and many more similar messages.  A very ominous line near the end of the file says, "init: gnome-session (Unity) main process (1753) killed by TERM signal".  For some reason the windows manager cannot get started, but I don't know what to do further to diagnose the problem or fix it.  I would greatly appreciate some suggestions.  Thanks, John

---

### Post by jweiner on 2014-12-15
Well, the problem is resolved in the sense that I have my GUI back, although I don't think I did it in a very smart way.  I just took my 14.04 live DVD and reinstalled 14.04 from it.  I made sure that my onboard video was "on" in the BIOS and then I rebooted.  The GUI came up after a few seemingly endless minutes.  Then I reinstalled my wireless keyboard (Logitech) and my Radeon graphics driver from the AMD site.  Then I rebooted, went into the BIOS Chipset Section, changed to offboard video "on", and let the boot proceed.  Again everything came up ok and I verified that my Radeon graphics card was the one being used.
I think my essential problem was that I did not know how to restore the X configuration to some default configuration so that I could at least get a default GUI running.  In the course of reinstalling everything the correct configuration file was reinstalled, but this is a very poor way of solving problems.  Can anybody point to a tutorial or explain to me how I can backup up a default X configuration so that the next time I don't have to resort to the "nuclear option" of starting from scratch with the live DVD?

---

