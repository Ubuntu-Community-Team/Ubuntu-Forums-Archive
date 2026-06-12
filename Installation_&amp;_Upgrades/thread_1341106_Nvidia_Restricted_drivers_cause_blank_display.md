---
title: "Nvidia Restricted drivers cause blank display"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by bigfootnmd on 2009-11-29
My Housemate's computer has a NVIDIA Geoforce 8400 card installed (onboard graphics chip is disabled).  After Windows VISTA Blue Screened we decieded to forget Mr. Gates and go with Ubuntu on his system (he has used my Netbook with Ubuntu 9x NBR) so he is familar with Ubuntu.  After loading 9.04 (because of problems with the 9.10 image) and upgrading to 9.10 (Gnome) I started loading updates.  Ubuntu 9.1 informed me that we were not using the restricted Nvida drivers and click here to install them.  Well I use the Nvidia driver version 185 and my Dell has the same card has his HP.  So, I installed driver 185
and then clicked restart. The computer reboots and next thing I know there is no display anywhere.  I rebooted choosing recovery mode and had no choice to repair graphics offered.
I searched this site and I could not find anything that told me how to revert to the default VESA display driver.  So,  having an impatient housemate who is ready to go buy Windows 7 I had to act.

I have reinstalled Ubuntu 9.04 and upgraded to 9.10.  I will not load any of the Nvidia drivers on his machine since obviously the 185 driver caused a problem.  I also do not want to try any newer drivers until I know how to remove a driver from the command line if this mess happens again.

So,  how do you remove a display driver from the command prompt if you do not know the exact package name?  Is there a way to revert to default video settings from the command line?

Thank you in advance.


OK,
I took myUbuntu 9.04 CD and installed 9.04 on to this PC.  After the install was complete I then restarted and 9.04 came up.  I next upgraded to 9.10.  Now this machine boots to the command prompt and not the gui.  I have tried the sudo dpkg-reconfigure -phigh xorg-conf and nothing changes.  I have booted to recovery mode and there is no choice to repair display driver settings.  So I have machine running 9.10 that boots to the command prompt and nothing else. I have not loaded the Nvida drivers either.  Also, "sudo dpkp-reconfigure gdm" did nothing.

---

### Post by bigfootnmd on 2009-11-29
OK,

The problem is solved. After searching these forums I found instructions that directed me to copy the xorg.conf.failsafe file onto my xorg.conf file.  Ubuntu 9.10 boots normally.
Oh Happy Day.

---

