---
title: "How to recover mouse an dkeyboard?"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2011-01-05
I installed a bunch of updates on one of my 10.04 systems before the holidays and then shutdown.  Upon my return the initial boot greeted me with the "low resolution graphics" dialog and no functional mouse or keyboard.

I dual booted to 8.04 and replaced /etc/X11/xorg.conf with the contents of the xorg.conf.failsafe in the same directory and rebooted.  Got the 800x600 VESA Gnome desktop but still no mouse or keyboard.  I tried booting with a different brand mouse (was MS, tried Logitech trackball) but still no good.  I have to press the reset button to reboot :(

It is not a hardware issue as mouse, keyboard and 1920x1200 graphics all work fine when I boot 8.04, 6.06 or Windows 2000.  None of the four 10.04 kernels listed in my boot menu makes any difference.

Ideas on how to recover?

---

### Post by wkulecz on 2011-01-06
Bump,

Fair number of looks, but no ideas?

---

### Post by wkulecz on 2011-01-12
I stumbled on to the weird fact that if I boot without the mouse and keyboard attached and then plug them in after the Gnome desktop come up I can use ALT-TAB to get to a terminal window I had open by default and the keyboard then works, but still no mouse

lsmod shows little:

lp
paraport
floppy
forcedeth
pata_amd
sata_nv


This is strange as the system has no floppy and the only installed printers are network printers.

What module need to be loaded for an MS mouse?

Any command to trigger a liveCD like hardware detection?

---

### Post by wkulecz on 2011-01-12
Got it mostly back, redoing "hardware drivers" now in low resolution mode.

after doing sudo -i in the terminal I did:
dpkg-reconfigure -a

apt-get update 
which triggered the graphical update manager to pop up.  I stumbled around with alt-tab and other non-mouse keyboard "equivalents" and got it to quit with an error message saying I need to run:

apt-get install -f  
Which seemed to complete and told me to run:
dpkg --configure -a

I then did:

apt-get update
apt-get upgrade

~77MB of downloads later I rebooted and had low resolution graphics desktop and a working mouse and keyboard.  Kind of brute force, but at least it sorta usable now.

Rebooting as I type this to hopefully get the full Nvidia driver desktop I had before.

Had some issues with the web site and before I could post this my reboot completed and my full 1920x1200 desktop with working mouse and keyboard are back!

I pity the poor fool who has only a single computer!

---

