---
title: "Intrepid only runs in VGA"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by vaasnaad on 2008-11-15
I'm installing Intrepid on a Dell Dimension 512MB RAM and an onboard Intel 91X chipset graphics card.  I can run the live CD, but only in safe graphics mode.  If I try normal gaphics mode, I get 1024x something strange, I get an orange screen, then it goes black, and there's a cursor there but it won't do antything but move.  If I install, I get the background screen like Xserver is running all the way through the install, nice resolution and everything.  As soon as it reboots, same story as with the live CD.  I figured it was my monitor as it has prevented Xserver from starting on other distros because it's off brand, but I went to edit the xorg.conf file and it's basically a blank.  Everything is generic.  I'm stumped and I'd REALLY like to run Ubuntu.  It works on other systems I've tried.  In fact, I'm typing from one I'm running a live CD on now...  Any one?

---

### Post by RHTopics on 2008-11-15
Do you have access to a Live CD that works with your monitor.  Something like Knoppix or Mandriva One are good ones to have available.

If you do then boot up with one of them and save the xorg.conf file from it to a USB stick and then when you boot back into Ubuntu copy the saved xorg.conf file from the USB stick into /etc/X11.  Restart the X server by pressing Crtl-Alt-Backspace and you should have a better screen.

I have the same problem with an old Microtek monitor that I am using.

---

### Post by vaasnaad on 2008-11-16
GOOD IDEA!  I had thought of that... after I wiped the drive and it was too late!  hehe
But I put it back up in the Freespire Live boot and copied the xorg.conf over to Ubuntu and man, it did NOT like that.  Had to do a recovery and again I seem to be at a completely blank xorg.conf file (well except for generic placeholders for the sections), which really baffles me.  Another REALLY confusing part is I get the login screen, which is part of X starting, correct?  So I SHOULD, in theory get the desktop too once I got that far...

---

