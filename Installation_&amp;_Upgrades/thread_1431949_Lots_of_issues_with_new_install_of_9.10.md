---
title: "Lots of issues with new install of 9.10"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by GARoss on 2010-03-17
This problem is way over my head & I'd appreciate some help. I still have issues with a faulty install. Spyrule & oldos2er have & still are trying hard to help solve the issue(s), documented here- 

[http://ubuntuforums.org/showthread.php?t=1431266](http://ubuntuforums.org/showthread.php?t=1431266)

Things like Software Manager, Update Manager & Hardware Drivers are listed as they should be but any attempt to open these fails. Something didn't install properly but somehow the system thinks it is. Trying repairs by booting in Recovery Manager mode, update & upgrade in the terminal indicate everything is there with nothing to install.

And, it affects other software, too. I tried to launch Rhythmbox  from Applications/Multimedia/Rhythmbox. It tried but never opened. Then I loaded a song & tried to play it with Rhythmbox. Same thing. Then in the terminal it typed Rhythmbox, enter &  got;
george@george-desktop:~$ rhythmbox

** (rhythmbox:3956): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (rhythmbox:3956): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

(rhythmbox:3956): Rhythmbox-WARNING **: Could not import pygtk
ImportError: No module named pygtk
Segmentation fault
george@george-desktop:~$

In Synaptic Manager I un-installed & reinstalled but fared no better. Weird!

Any thoughts or suggestions are appreciated!

---

### Post by wojox on 2010-03-17
This is a fresh install not an upgrade? Would reinstalling the OS be an option?

---

### Post by GARoss on 2010-03-17
> **wojox said:**
> This is a fresh install not an upgrade? Would reinstalling the OS be an option?

Thanks. Yes, new install.
Yes, reinstall would be an option but when I tried that the disc booted to a point before you get to 1st of 7 steps & the screen flashes like mad with just text on the screen. I cannot do a live cd boot either, it does the same thing.:confused:
The disc was scanned for errors prior to install & checked okay. My PC uses nVidia & there has been lots of 9.10 issues with that which I've experienced, too.
I could try burning a new disc & try that. Just trying to avoid the nVidia issue which I have, at the moment, solved.

---

### Post by GARoss on 2010-03-17
I burned a DVD install disc & I am able to do a live cd boot; something I could not do with the CD install disc.
Can a repair be done from a live cd boot? In Synatic Package Manager it says I need to download 250mb of data but, of course, I'm in live cd - not my desk top. Just wondering if that might help?

---

