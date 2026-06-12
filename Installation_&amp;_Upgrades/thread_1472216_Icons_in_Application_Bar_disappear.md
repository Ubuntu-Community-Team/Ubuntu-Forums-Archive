---
title: "Icons in Application Bar disappear"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Euphorion on 2010-05-04
Hallo

I have installed Ubuntu 10.04 Lucid on 3 machines, using the following methods. On the machine having 8GB Memory the 64bit version from scratch, one machine 32 bit via update from Karmic and the last machine 32 bit from scratch.

All machines have installed with no trouble at all, the only effect that I notice on all machines is the following: The Loudspeaker Icon for the volume appears on reboot after installation and then disappears never to reappear, during longer use the all other icons on the right hand side of the application bar with the exception of the date and time display also disappear, these (Shutdown, Network, etc) reappear when the machine is rebooted.

Anyone know the reason why this is happening and how I can repair the missing loudspeaker icon for the volume control.

Thanks in advance.

---

### Post by inameiname on 2010-05-04
I found this when I was in search of a resolution to the same problem.  And it seems to work:

                                 go to System > Preferences >  Startup Applications

in the startup tab, look for 'Volume Control' and check it if its  unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....



There are actually quite a few postings on here about this very issue, one being: 
[http://ubuntuforums.org/showthread.php?t=1466400](http://ubuntuforums.org/showthread.php?t=1466400)

---

