---
title: "Hardy to Lucid Upgrade Errors"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by Virgo53 on 2010-08-21
Hello All,
I decided to try upgrading Hardy to Lucid and
encountered the following problems:
Error occurred while loading or saving configuration
information for evolution-alarm-notify. Some of your
configuration settings may not work properly.
Adding client to server's list failed, CORBA ERROR:
IDL: omg.org/CORBA/COMM_FAILURE:1.0
Could not install 'Linux-Headers-2.6.24-26'
The upgrade will continue but the 'Linux-Headers-
2.6.24-26' package may not be in a working state.
Please consider submitting a bug report about it.
Cannot remove '/usr/src/linux-headers-2.6.24-26/
include/linux/udp.h'
Error during commit
A problem occurred during the clean-up. Please see
the message below for more information.
InstallArchive() Failed
Is this enough information to provide some insight
on a solution? I would like to try Lucid, or at
least return to Hardy in a bootable condition, provided that it's still there. Did the upgrade
attempt wipe out Hardy requiring a reinstall?

---

### Post by mörgæs on 2010-08-21
First of all: Does your machine like 10.04? That is, can you boot a 10.04 live CD?

---

### Post by Frogs Hair on 2010-08-21
Delete- wrong info 8.04  to 10.04 upgrade is supposed to be possible.

---

### Post by Virgo53 on 2010-08-22
I suppose I foolishly thought that the upgrade
would have went smoother, since it's been well
over 3 months since Lucid's release and now that
Synaptic shows the upgrade is available to 10.04,
I thought why not go for it! Fortunately, I can
still boot-up XP until this gets straightened out,
since grub still shows my boot menu.
Will Lucid require a clean install from an .iso?

---

### Post by mörgæs on 2010-08-22
If you know that 10.04 works on your machine, then yes: A clean install is the fast and safe solution.

---

### Post by Virgo53 on 2010-08-22
I have never tried Lucid, so I am not sure if it
will work okay or not. I will download and burn it
as an .iso to see how it does running live.
I must have messed up choosing to keep the current
menu.lst since Lucid uses grub2 over the original
grub version?
I see from all these other threads that upgrading
Ubuntu certainly has its share of problems! So much
for smooth transitions. :mad:

---

### Post by Virgo53 on 2010-08-24
Okay, I'm back to using Hardy- I downloaded 10.04.1 LTS i386-generic, verified it, burnt it to a CD. Then tried running it live, and it started to load, but ended up with a blank screen! So I guess Lucid doesn't like my hardware or whatever?
Reinstalled Hardy, updated it, and now everything is back to normal.  :p
I wonder how many others will make the mistake of clicking on the upgrade button before all the problems with it are resolved? It seems that Lucid is "not ready for prime-time",imho- at least not on my Toshiba Satellite A45-S150 Notebook. #-o

---

### Post by mörgæs on 2010-08-24
Good. 8.04 is supported until april 2011, so you are not in a rush to upgrade.

---

### Post by Virgo53 on 2011-03-19
Well now that support for Hardy (desktop version) is ending next month, I decided to give Lucid another installation attempt. This time around, though, I used an alternate cd for a supposedly text install. The installation was successful, but not without some problems- mainly, I can't get X to start up or configured.
I tried using xrandr, but it displays "can't open display".
(This is on my Toshiba Satellite A45-S150 Laptop 2.4 Ghz.,BIOS version 1.50; 1264 MB RAM; 15.0" TFT active-matrix display; Intel(R) 852 GME Chipset; 32 MB DDR SDRAM (UMA); video BIOS version 2894, current graphics mode: 1024x768 true color (32-bit) 60Hz, as reported in Win XP).
During the installation, I was at the "How would you like to reconfigure your
display?" window, and using the default (generic) configuration did not work.
Nor did choosing "Create new configuration for this for this hardware", or "Use
your backed-up configuration". (Selecting either of the latter options just returned to the default.)
I tried to review both the xserver log file and the startup errors, but they were both blank.
I am using a Chakra Live cd (free drivers) right now and it reports the display as
LVDS1 (connected) Size: 1024x768 (Auto) Refresh: 60.0 Hz Orientation: No rotation Position: Absolute  0   0
Can anyone provide some insight on how to get the GUI working, please?

---

### Post by Dutch70 on 2011-03-19
Have you tried choosing "nomodeset"? I'm really not familiar with the alternate install, but it's quite common around here for people to get a black screen when trying to run the live cd or install. Choosing nomodeset at start up seems to be taking care of it for most. 

 I think you hit the f6 key when you get to the purple screen to choose nomodeset.

---

### Post by kansasnoob on 2011-03-19
This is referred to in the release notes:

[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by Virgo53 on 2011-03-19
Thank you Dutch70 and kansasnoob for your replies- I'll try the "nomodeset" to see if it does the trick, and if not, I'll
try the workarounds. I don't currently have a network connection set up in Lucid- the network setup repeatedly failed during the installation, and the workaround that suggests rolling back to the 2.6.31 kernel probably won't fix things since the Chakra GNU/Linux Live cd I was running yesterday had X working with the 2.6.37 kernel series. :confused:

---

