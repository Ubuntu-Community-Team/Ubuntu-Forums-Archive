---
title: "freeze at GDM login"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by 2centaur2 on 2006-06-05
I have been running Ubuntu 504 on my PC without problem. I have a Sempron 3100+ PC with an XFX NVIDIA Geforce 6200 display adaptor, a Proview HD-972 19" lcd monitor and a Gigabyte K8VM800M motherboard.

When I tried a clean install of Ubuntu 606 I ran into problems. Installation completed without problem but after rebooting the system froze at the GDM login screen.

Rebooting in Recovery Mode I could login without problem after typing GDM at the command prompt, but after logging in I got following message:

Quote

Power Manager

Warning

This program cannot start until you start the dbus system service

Unquote

Clicking Close to close this warning message brought up the following Error window:

Quote

Internal Error

Failed to initialize HAL

Unquote

As the forum threads often point to nvidia as the probable cause I used Method 2 of tseliot's guide ([http://doc.gwos.org/index.php/Latest_nvidia_dapper](http://doc.gwos.org/index.php/Latest_nvidia_dapper)) to install the latest nvidia driver:

Original /etc/X11/xorg.conf:
           Monitor:
           HD-972
           DPMS
           Device:
           NVIDIA Corporation NV40?
           nv
           PCI:1:0:0

New /etc/X11/xorg.conf
          Monitor:
          HD-972
          DPMS
          Device:
          NVIDIA Corporation NV40?
          nvidia

However the result was the same: Freeze at the GDM login screen.

I am at a complete loss about how to proceed.

---

### Post by llamakc on 2006-06-05
What about restarting /etc/init.d/dbus?

---

### Post by soulglo83 on 2006-06-05
weird doesnt sound like a driver issue if the behavior is identical on both nv and nvidia drivers.  just to be sure though, try launching your xserver w/ using vesa in place of nv or nvidia in your /etc/X11/xorg.conf

i myself experienced the same problem with dapper and the new nvidia binaries, both the method 2 and 1 installs trashed x.  then following the advice of an nvidia tech, i added:

Option          "NvAGP"         "0"

to my device settings for my video card.  this is not likely to help if the problem occurs with nv drivers though :(  report back on your results using vesa, as it lacks even 2d hardware acceleration, everything should be done in software.  if vesa fails, there is a good chance you installed from a corrupted install cd, or otherwise your ubuntu environment may be contaminated!

---

### Post by 2centaur2 on 2006-06-05
To llamakc: You can of course start the dbus service manually, but that doesn't solve the problem. I just mentioned the dbus problem as it might indicate where the problem originates.

To soulglo83: I did try VESA but that didn't work either. It clearly is not a video driver problem.

---

### Post by quasibdjord on 2006-06-10
Re-installing HAL through Synaptic seemed to work for me.

---

### Post by sbooth on 2006-06-10
Reinstalling HAL hasn't worked for me - I have the same problem and it seems to have appeared overnight after this mornings updates (I installed all the notified ones).  I can log in and access all my smb shares (need those - my firefox and thunderbird profiles are stored on them) if I use a gnome failsafe session - but not if I use my normal gnome session.  Where are the differences between the two?

EDIT:
I now don't have the power manager warning if I log in to a normal Gnome session... but it takes ages and I still get the HAL error.  If I log in to a failsafe Gnome session I don't get the problem.  Hmm.

EDIT 2:
I just logged in to a normal session and got neither error... earlier I'd logged in to a failsafe session and got the HAL error.  I hate intermittent errors... I don't know what to do about them or even where to start.

EDIT 3:
This is still going on - seems that a failsafe session is okay, but if I change session to "Gnome", it gives me the "Failed to initialize HAL" error.  I've reinstalled HAL without joy :-(

---

### Post by sbooth on 2006-06-13
Okay, so I think I found a solution - but I'm not happy with it!

I've had this problem intermittently since the update-manager updates on Saturday morning. Very odd. Lots of searching found me a potential cause - to do with automounting samba shares on start up. I just took out the automount (added 'noauto') to the relevant lines in /etc/fstab and rebooted... and it started fine. Have mounted the shares having booted, no problems. The intermittent nature of the problem made me think it was a timing problem - with the order things start in - but I'm a bit too much of a newbie to know how to play with those safely.

I wish I could make it work **and** automount my samba shares (running Ubuntu on a laptop and keep everything data-like/profiles/email etc on a server).  Any suggestions?

---

