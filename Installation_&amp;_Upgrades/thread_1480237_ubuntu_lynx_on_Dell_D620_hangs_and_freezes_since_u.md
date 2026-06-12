---
title: "ubuntu lynx on Dell D620 hangs and freezes since upgrade to lynx"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by egstern on 2010-05-11
I have been running 32 bit karmic (and before that jaunty, intrepid and hardy) with no problems on my Dell D620 laptop.  Since I upgraded to lucid, I get occasional freezes.  It often happens at the gnome login screen after I click on my name but before I can enter the password, or upon restore from suspend but sometimes at other times.  It doesn't happen all the time but often enough to be really annoying.  When the freeze occurs, the mouse pointer responds to the touchpad or an external usb mouse, but no mouse button events are recognized and the keyboard has no effect either.  I can't switch virtual terminals or anything.  If the system was up and had a DHCP address at the time of the freeze, I believe the network still responds to ping.  The only thing I can do to get the system back is hold the power button for 30 seconds until it powers off.  The desktop CPU temperature monitor does not indicate excessive heating at the time of the freeze.  I don't know whether I should try a re-install of lucid, or just go back to karmic.  Any suggestions on things to look at?

      Eric

---

### Post by dino99 on 2010-05-11
lot of issues around on web:

[http://www.google.com/search?hl=fr&q=d620%2Blucid&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=](http://www.google.com/search?hl=fr&q=d620%2Blucid&btnG=Rechercher&aq=f&aqi=&aql=&oq=&gs_rfai=)

---

### Post by egstern on 2010-05-11
I happen to have had an ssh login into the laptop at the time one of these freezes occured.  From the network the laptop appeared OK.  When I killed the X process, gdm restarted it and I had the screen back, so it does seem likely related to the nouveau driver.

---

### Post by egstern on 2010-05-12
Apparent fix: use

Administration->hardware drivers

to enable the proprietary driver.  Reboot.  Use the hardware drivers tool to disable the proprietary driver.  Reboot.

It seems a lot happier now.  I haven't had any freezes, suspend/resume seems to work with no problem and I can switch virtual terminals.

     Eric

---

### Post by egstern on 2010-05-15
I spoke too soon.  I still had problems with the laptop hanging.  Even more damning was that the problems occurred even when I booted from the desktop install CD.  My latest workaround is to remove xserver-xorg-video-all (which depends on all video drivers) and xserver-xorg-video-nouveau.  Now X is running with the nv driver as it used to.  I haven't had any hangs so far, suspend and resume seem to work.  The only problem is that there is sometimes display corruption when switching to different virtual terminals and the boot-up splash screen is broken.  I don't care about that so I just removed the spash options from the grub menu.

     Eric

---

