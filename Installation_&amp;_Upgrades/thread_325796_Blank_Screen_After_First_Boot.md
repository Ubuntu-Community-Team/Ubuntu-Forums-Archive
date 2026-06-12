---
title: "Blank Screen After First Boot"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by dborras on 2006-12-26
Hello everyon and thank you for all of you help so far.
This is my first installation and I had a some problems loading from the default install disk, but with some help from the “Installation Forum” I loaded from the Alt I386 setup disk and everything loaded fine.  The problem I’m having now is on the first reboot after I remove the CD and hit Enter.  The system reboots and I get an option to press ESC, for a few second, to select boot options, but than tha screen goes blank and stays that way.  Selecting ESC and going into the boot option did not help.  I believe that it must have something to do with my video card, which is an Nvida  GForce card.  Has anyone run across this problem?  If I need to load a driver how do I do it?:confused:

---

### Post by meng on 2006-12-26
After the hard drive has gone quiet, try pressing ctrl-alt-f1 and see if you get a text-based login. Also, have you got an LCD monitor? It may not be the card that is the problem, but that it may be attempting a ridiculously high refresh rate that your monitor doesn't support.

---

### Post by wpshooter on 2006-12-26
Make sure that when you are doing the ALTERNATE CD install that when you get to the screen where it offers you a choice of various resolution settings that you choose only those that you absolutely know that your video card and monitor support.  Perhaps even a good idea to choose only 1, that being 1024 x 768.  Then once you get your system to a state where it will boot correctly all the way into the desktop, then start researching how you go about getting the correct drivers and/or configuration parameters setup for your video.

Good luck.

---

### Post by dborras on 2006-12-26
Thanks for the quick response.

I am running it on an older monitor, is there any way to reset the resolution?  It does give me the option to hit ESC to get to the boot options before it goes blank.

wsshooter
If the resolution is set to high for the monitor will I have to start all over with the installation or can I reset the resolution somewhere?

---

### Post by wpshooter on 2006-12-26
Yes, I think there is, if you can get to the terminal/command line you can use the gedit text editor to alter the parameters in the xorg.conf file and give yourself the proper settings.  However, I am not familar enough with ALL of the settings therein to advise you what and where to edit and I beleve all of this depends on the brand of video card you may have.  See if you can do some research/searches on editing the xorg.conf file or perhaps someone more comfortable with manually editing this file can give you some assistance.  However to me all this is easier to do if you can get the machine to the desktop.

Good luck.

---

