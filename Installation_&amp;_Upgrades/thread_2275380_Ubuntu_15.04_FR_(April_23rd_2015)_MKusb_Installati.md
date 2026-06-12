---
title: "Ubuntu 15.04 FR (April 23rd 2015): MKusb Installation feedback"
date: 2015-04-25
forum: Installation &amp; Upgrades
---

### Post by MikeMecanic on 2015-04-25
April 25th 2015, Testing Ubuntu 15.04 Final Release

I choose the default installation (New-York-LVM) and running it alone. 4g of RAM on an Intel mobo / Intel® Core™ i3-2100 CPU @ 3.10GHz × 4 / Graphics: Intel® Sandybridge Desktop 


This time the installation boot-up at the end but it restart in a black screen.  The black screen issue is less an Ubuntu problem then a HP computer one.  I have a HP wireless keyboard and was able to solve the problem by pressing the suspend mode button: it came back to normal after pressing a key.


**In the first 36 hours, I lost the desktop environment twice (fully frozen)**: on the same web site (set at 3000kps/Full HD Quality) doing the same thing.  Was trying to escape from full screen mode by clicking on the full screen icon (Opera 28 stable). ctrl+alt+delete didn't work (not able to logout). ctrl+alt+F1 work but it was pretty long to reach the terminal.  Made **$ sudo reboo**t and it restart normally.  Try many new things: Plank (works fine), activated Ubuntu Mate from there web site (not working), the files are there but it does not prompt.  Try (not install) Ubuntu Mate on a MKusb iso image (play with the desktop set up) and it was unstable. 


Basic Post-Installation was OK.  Test the firewall GUFW with a 202 full blended rules (some of them are related to Linux security) and it respond just fine (in and out).  Totem new design is nice: play video and music: no problem.  Same apply for VLC 2.2.0.  

Suspend Mode, **Lock Screen (works only with ctrl+Alt+L and not the mouse) **and Log Out: Connected or not to Internet  respond normally.


**Having problems with text size for at least one day**: /System Settings/Display/Scale For Menu And Title Bar was frozen to .75 for one day.  Not able to change it.  Same Apply for /System Settings/Appearance/Launcher Icon Size: in and out or not working properly.  

For what reason? It came back to normal the second day.  All of this is before I installed Plank and/or trying activating MATE that remains an issue. 


Regards,

---

### Post by MikeMecanic on 2015-04-25
After I install Plank, I was not able to restart the computer.  Instead, the desktop goes in logout mode and from there only I was able to restart.  I just removed Plank (Via Synaptic Package Manager) and things are back to normal.

---

### Post by kerry_s on 2015-04-25
lol, thats 2 down, 3 more to go
1) ubuntu-gnome
2) xubuntu
3) lubuntu
bonus) elementary os

i'm sure you'll find your place eventually.
i'm using xubuntu, cause it works the best on this old hp mini neetbook.

---

### Post by MikeMecanic on 2015-04-25
Curious by nature and born learner, I am not discourage at all.  My computer is not a mini but a all-in-one with a HD monitor.  It's not that old either: January 2011.  It came out of the factory with a black screen problem.  I used The Suspend Mode Button to overwrite it and it work . Will buy another later on this fall no doubt about it.:p

Dedicated to test Ubuntu 15.04**, ** I  Will reinstall it later (fool around a lot in the terminal: too much maybe).  For the rest, it runs better then ever (10.LTS). Running a fresh install (alone),** ain't got any major issue**: _IT'S QUITE AND STABLE_.  While testing it or I should say using it, I try new stuff that will be there in April 2016.

Take care,

---

### Post by MikeMecanic on 2015-04-30
Made a second installation and because it takes 15 minutes to install 15.04, I made a third one always on a LVM manner.  On my second installation, it boot up normally and the Lock Screen Issue was gone with the wind.  I got the same issue on NHL Gamecenter (3000Kbps) but CTRL+ALT+F1 responded at the speed of sound: Frozen desktop environment (reboot normally with $ sudo reboot). 

 I reported that issue to Opera Monday.  Tuesday (April 28) will all receive a patch of Opera that moved to 29 (using Chromium Open Project), Google Chrome did the same, moved to 42 + a network patch.  The frozen desktop issue is also gone with the wind:  Don't be shy to send data usage to Canonical Partners and report such issue to Google or Opera. 
 
Try Ubuntu after install beta 2.6 (works fine): [http://itsfoss.com/things-to-do-after-installing-ubuntu-1504/?utm_source=newsletter&utm_medium=email&utm_campaign=http_itsfosscom_things_to_do_after_installing_ubuntu_1504](http://itsfoss.com/things-to-do-after-installing-ubuntu-1504/?utm_source=newsletter&utm_medium=email&utm_campaign=http_itsfosscom_things_to_do_after_installing_ubuntu_1504)

Running system load indicator 0.4 and Psensor 1.1.3 that responded positively.  Finally, on a LVM manner (default installation: alone) and with Opera 29 (Disconnect, Adblock, Ghostery and Browsec), **Ubuntu 15.04 is not only quite and stable but it runs faster.**
.
All the best,

[http://www.opera.com/computer/linux](http://www.opera.com/computer/linux)

---

