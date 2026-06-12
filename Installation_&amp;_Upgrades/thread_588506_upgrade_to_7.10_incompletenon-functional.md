---
title: "upgrade to 7.10 incomplete/non-functional"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by iv2101 on 2007-10-23
I was running Ubuntu 7.04 on Dell inspiron 1420 [dell-preinstalled os] until yesterday, when I decided to upgrade to 7.10. 
There were no errors during the download part; there were a few warnings about non-critical packages during installation. However, packages 

ubuntu-desktop
gnome-themes
gnome-accessibility-themes

were not configured and the install gadget quit, instructing me to reboot. I did that and the graphics interface would not start (black screen with mouse pointer for ~5 minutes). ctrl+alt+f2 and similar commands gave nothing. I can only boot into the recovery mode. startx crashes:
```
I810: No matching Device section for instance (BusID PCI:0:2:0) found 
```
Needless to say, xorg.conf is the same one that worked for 7.04. I tried several calues for BusID - didn't work.  
I cannot get the machine to recognize the ethernet card either, so I can't redownload packages. 

Can someone help me get the ethernet to work and/or make X start?

Thanks

---

### Post by drewster1829 on 2007-10-24
I'm having the exact same problem, with the exact same three packages failing, with the exact same graphics driver and same BusID and same result with startx. :mad: Several people have been having problems with these three packages after an incomplete install 

(mine halted during the PAM business, about when the TabletPC crap is added to xorg.conf, and instead of waiting for my other system to finish upgrading and looking up the result, I rebooted)

The problems I had are on a Toshiba Satellite M55-S331 laptop.  So, you got these errors during the initial install, and THEN rebooted?

Anyway, I sure hope a solution comes up, soon.  Good luck!

---

### Post by iv2101 on 2007-10-24
Yup, I did the errors during install, and then they kept haunting me ever after. 

I actually took my computer to a linux-savvy person who managed to resolve the package conflict (remove LOTS of stuff - all gtk-dependent packages and probably more) and fetched them again. But this did not help: the system still failed to boot...

So i backed up the data and installed Ubuntu 7.10 from the CD. Works just fine. I think this is the thing to do (provided you can download and burn the cd and backup your data).

---

### Post by drewster1829 on 2007-10-24
Dang!  I was hoping you wouldn't say that...I've become fanatical about backing up, but as I ran out of space, I got lazy.  If only that 500 GB external drive I ordered showed up before yesterday (or if only I had the patience to wait for it before upgrading).

I do have a Dell desktop (that I'm typing this on) that the Gutsy upgrade went perfectly on.  I'd hate to have to start over on my laptop (even after getting my data onto that external drive, when it comes...no room on the desktop) because of all the installed programs and configuration settings.

Just out of curiosity, does anyone know how to xfer files over a Samba network in bash?  There's a few files I could really use on my desktop, but I don't know how to transfer them using just the terminal in the laptop.  (It (the laptop) seems to be connected to my wireless router...I can download packages, but it doesn't show up on the network list on my desktop.

iv2101, I'm glad you got it to work, but with how many other people are having trouble, I hope a solution surfaces that DOESN'T involve a clean install!  Thanks for the update, and for anyone who helps me (us).

---

