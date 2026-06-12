---
title: "Help!! :(  Problems with Nvidia, Logitech Mouse, on-board sound detection"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by Roey Katz on 2007-07-28
20070728

First off, much thanks to the Ubuntu and Kubuntu teams for raising the bar in GNU/Linux installation.
OK, now the problems:  I installed off the text-based ("advanced") Kubuntu 7.04/ia32 this morning hoping to shed seven years of wrestling the debian-sid aligator.  But it's as if I exchanged my old installation's problems for a set of new ones... Why don't these things just /work/ out of the box???  It's not like I have an exotic system setup...[1]

1.  Screen resolution:  My Dell 2405FPW monitor was incorrectly identified with 1600x1200 resolution instead of 1920x1200 (I sifted through Google and found out that it's an issue with xresprobe that will hopefully be fixed in the next Ubuntu release[2])

2. Mouse detection: I have a Logitech MX1000 mouse; For some reason, the mouse wheel scrolls vertically only when the mouse pointer hovers directly over the vertical scrollbar.  I see this with both KDE/Qt and GTK applications (the GUI installer didn't exhibit this behavior; the mouse wheel scrolls fine there).

3. Sound detection:  I don't hear sound when I play through my digital-out on my on-board via82cxxx controller (motherboard/cpu is an MSI NEO K8T FIS2R with an athlon/3200).  I made sure to set Amarok to ALSA output, and both it and mpg123 seem to think they're playing something (amarok's frequency analyzer fires away with the music), yet I don't hear anything.  In alsamixer I already had the IEC ports set to "PCM-OUT", btw.

4. NVidia:  On every boot, /lib/modules/2.6.20-16-lowlatency/kernel/drivers/video/nvidia/nvidiafb.ko seems to disappear, and I have to issue "sudo apt-get install --reinstall linux-restricted-modules-2.6.20-16-lowlatency ; sudo modprobe nvidia" before I start X (since X can't start otherwise).  Why is it getting clobbered??  I have a Geforce4 Ti4200 video card, and I use it with the nvidia-glx drivers (no -legacy, no -new)

5. Mouse detection again:  In KDE's System Settings program, in Keyboard and Mouse->Mouse- in the "MX1000 Laser" tab, I see this message:

  "You have a Logitech Mouse connected, and libusb was found at compile time, but it was not possible to access this mouse.  This is probably caused by a permissions problem - you should consult the manual on how to fix this."

  What is this?? How can I find out what's missing?

6. X-Chat:  Relative to my old debian-sid/amd64 installation, this XChat's tabs no longer highlight (relative to my old debian/sid installation) to reflect new messages in the Channel.  I kept my old /home, so it's not anything in my .xchat2 to blame... so what is it?

7.  When I log in as another user and issue "startx -- :1", the screen starts at 640x480.... I can't tell for the life of me why it does this...

8. GRUB:  I originally wanted / on the XFS filesystem, but since GRUB has issues with this combination, I decided to go with ext3.  When will Ubuntu ship with a GRUB that supports XFS installed on / ?

9. Adobe Flash:  Could the next version of Ubuntu make it easy to install a 32-bit Adobe Flash on a 64-bit system?  I just want to apt-get nonfree-flash and have Ubuntu's Apt take care of the netscreen-wrapper issue for me.  I don't want to have to care that it's a 32-bit plugin even.  


Thanks for your help :)
- Roey Katz


[email]RoeyKubuntu@gmail.com[/email]



--
references:

1. System setup:
   - MSI NEO K8T FIS2R motherboard athlon3200 with onboard sound and LAN
   - Geforce4 ti4200 video card
   - 2 GB ram, 2 GB swap
   - ext3 on / and /boot, xfs on /home, software raid1 on all three drives
   - wacom tablet
   
2. [https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/40422](https://bugs.launchpad.net/ubuntu/+source/xresprobe/+bug/40422)

---

