---
title: "/var out of space"
date: 2005-09-12
forum: Installation &amp; Upgrades
---

### Post by mohoohoo on 2005-09-12
hi
i'm trying to install the latest release (5.10) on to a Dell Optiplex GX1 500Mhz machine with a 15GB HD and 128MB of RAM. I've tried the install 3 or 4 times now and I get the same error each time - /var out of space. I did try the server install and that worked but that is not what I really want; haha! Any ideas? I am happy to provide more info but if you're requesting can you keep it simple as I am pretty new to this and need good clear instructions.
cheers,
adrian
---
to add to my message above i just tried a new install and again it exited unfinished with a message along the lines of ...
Copying packages failed ... may have run out of space on /var ... checking the virtual console  shows me that the install failed with code 1 while copying xfont100dpi.6.8.2.1-3_all.deb

---

### Post by debenham on 2005-09-13
Try cleaning out your apt cache first. I may clear up the needed space.
Do this by running 'sudo apt-get clean' in a terminal window

---

### Post by mohoohoo on 2005-09-13
Hi thanks for the tip. Unfortunetly it did not work though. It got to 90% and exited with that same familiar error. I just hit return and let it continue in it's default manner. It ejected the CD and went on to install further packages but it didn'r get far and has hubg at 0% - it says "Preparing for installation ..." 
Any ideas?

Just adding that the machine is running an Intel i4400 #X or BX chip (that's a PIII 500) - hope some one out there is able to help.

---

### Post by soth83 on 2005-11-09
Hey, this is just the same problem i'm having! I cannot start the graphic mode!
help!

---

