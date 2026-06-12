---
title: "New Installation Advice needed"
date: 2005-08-21
forum: Installation &amp; Upgrades
---

### Post by PhilB on 2005-08-21
Have been a Linux user (though mainly point and click) for some time now-Mandrake/Mandriva, Thought I'd try Ubuntu because I like the idea of never needing to install new versions again, and like the Debian apt system.
Did what I always do and tried on a spare disc, which was fine, but had a problem with my main drive. 
I kept the /home partition and formatted swap and /, and did a complete install, but as soon as I log in I get a pop up saying I logged out after less than ten seconds (there was also an error message which I unfortunately  failed to note down). However I could log in and see my home partition etc in safe mode, so I'm assuming there is a problem with the desk top settings in my home partition.

Before I try installing again, presumably I should delete some of the hidden folders in home, but I'm not sure which-both Gnome and KDE are used. 
Any advice would be much appreciated.

---

### Post by jasmuz on 2005-08-21
There is no need for reinstall, you have an old .ICEauthority file from your previous system.
Just go to a console (alt+ctrl+f1) and type rm .ICEauthority and that should be it!

---

### Post by PhilB on 2005-08-22
Thanks for the advice-once I knew what to look for, found a few suggestions on the net.
Unfortunately it did not work for me, I suspect that because my settings had been heavily modified over the last few months, I would have had to delete or modify many files. 
Instead I took the sledgehammer approach, found a way to back up 42Gb of files and wiped the old home partition and started from scratch.
Now a happy Ubuntu user.
Phil

---

