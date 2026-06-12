---
title: "Screen Resolution and the disappearing Mouse Pointer under VirtualBox"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by grahamt on 2007-08-15
I am using VirtualBox 1.4.0 under WindowsXP to run Ubuntu 7.04.  The install works perfectly and I have no problem using Ubuntu in this environment.  However, the maximum screen resolution with vanilla install is 1024x768 which, on my Acer TravelMate 15.4" wide screen at 1650x1050 requires a magnifying glass to read.  I set out to see how to increase the screen resolution to a more user-friendly size, either 1152x864 or 1280x1024 as an initial experiment.

I discovered that this requires the installation of the VirtualBox Guest Additions.  This, in itself, is no easy task for a relative beginner like me but, with much advice on various forums I managed to accomplish it.  The process involves running the following commands from the Terminal:

 1) sudo aptitude install build-essential linux-header-`uname -r`

 2) sudo sh /media/cdrom0/VBoxLinuxAdditions.run all

After doing this you have to then run:

 3) sudo dpkg-reconfigure -phigh xserver-xorg

...in order to add the additional screen resolutions to the list of those available.  However, even when I had done this, Ubuntu refused to offer me the additional screen resolutions.

Going back and running step 3 again I noticed that I was also offered a choice of video drivers.  The default was "vesa" but "vboxvideo" was also offered.  This time I chose "vboxvideo".

Restarting the Xserver I was suddenly confronted with no mouse pointer!  The mouse was obviously there as I could "touch" buttons but where on the screen it was was a matter of guesswork.

I checked xorg.conf against the version immediately after the install of the Guest Additions and noticed that something else had changed.  The mouse driver had been changed back from "vboxmouse", as it was, to just "mouse".  I edited the xorg.conf file back to "vboxmouse" and restarted Xserver and the mouse pointer reappeared.  Not only that but I could now choose the additional screen resolutions.

In conversation with various very helpful people on various Forums I have reached the conclusion that the problem is in the configuration script for xserver-xorg.  I understand why the mouse driver was changed back to "mouse" but what I don't undrstand is why the config script doesn't offer any opportunity to choose the mouse driver required.  It does allow the choice of the video driver so why not the mouse?  If a choice had been offered then I wouldn't have needed to edit the xorg.conf file manually and debconf would have been aware of the changes.

Can whoever is responsible for maintaining the config script for xserver-xorg (Branden Robinson?) please add this selection option?

---

### Post by Mets on 2007-11-04
Thank you so much for posting this!  I had the exact same problem, and I had no idea what to do.  I didn't know you needed to recofigure xorg.conf and I would never have guessed the vboxmouse problem.  this saved me a significant amount of fustration.  This entire process should be automated when you install the virtualbox guest additions, in my opinion.

---

### Post by wormser on 2007-12-06
Thank you for this post.  It resolved my mouse issue in a Gusty Virtualbox machine.

---

### Post by hegderavin on 2007-12-13
After reconfiguring the xorg-xserver using dpkg-reconfigure, I installed guest additions again and the mouse pointer is back.

---

### Post by Thelasko on 2008-04-10
Good post!  Running the dpkg-reconfigure script fixed my problem with virtual box being stuck in 24 bit mode but then I lost the mouse.  This fixed the mouse.

How do you do Ctrl+Alt+Backspace in Virtualbox without restarting X on the host?

---

