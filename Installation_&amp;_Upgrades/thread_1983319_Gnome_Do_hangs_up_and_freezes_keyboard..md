---
title: "Gnome Do hangs up and freezes keyboard."
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by cr4321 on 2012-05-20
I have  a mulit-boot system. 

I have Ubuntu-12.04 newly installed in one of the partitions. I installed all the packages for my use and upgraded the softwares to the latest upgrades and everything worked well.  Then I installed Pidgin with all the plugins and also installed gnome-do as sugested.

On the next reboot, it boots fully and the gnome-do app also comes up. The mouse works but is unable to activate anything.

The keyboard also freezes - except for the Windows Key. The windows key is able to bring up the side bar menu etc but nothing activates. If the window keys are pressed for longer, another menu appears but none can be activated.

How do I remove this Gnome do application - even the Terminal cannot be activated with the ctrl-alt-T key presses.

Please help.

NOTE : Solution found in : [http://ubuntuforums.org/showthread.php?t=1488340](http://ubuntuforums.org/showthread.php?t=1488340)

Just did a "ctrl+alt+F1" and entered the virtual terminal and removed Gnome-do, by : code [sudo apt-get remove gnome-do]
Then did a reboot by : code [sudo reboot]
It rebooted fine : Hope this helps someone else :)

The villain is GNOME-DO (hope they come up with a solution)

Also think UBUNTU should warn users on this GNOME-DO problem
---------------------------------------------------------------

---

