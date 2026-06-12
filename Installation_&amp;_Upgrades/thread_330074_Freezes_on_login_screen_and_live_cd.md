---
title: "Freezes on login screen and live cd"
date: 2007-01-02
forum: Installation &amp; Upgrades
---

### Post by eggert on 2007-01-02
Hi.

I installed Kubuntu 6.10 from alternate install cd and everything ran smoothly.  I used alternate cd because live cd always hung right after starting X server but before starting GNOME / KDE (I tried both ubuntu and kubuntu 6.06 and 6.10) with or without changing / removing xorg.conf.
After the installation finished and pc is started the login screen comes up, everything looks normal, I can move the mouse and type my username, but it hangs after the cursor in text box has blinked 3 times (about 1.5 seconds).  Everything locks up, no keypresses work, only thing to do is press reset or power button.
By selecting recovery mode in the boot menu I can get to terminal and from there start X and KDE starts with everything normal (might be a bit unstable) except that when I logout kde * manager (can't remember the name) crashes everytime.
Searching through the logs I found some errors in xorg.0.log and commented out the offending sections but it didn't change anything.  Can't find any other error in log files.

My hardware is:
AMD Sempron 3000+
ABIT KU8 mb (ULi M1689 chipset)
  with built in IP100A ethernet controller
  and ALi M5455 Audio device
Linksys NC100 ethernet controller
1 GB 333MHz DDR2
120 GB EIDE hdd
nVidia NV31 (FX5600 256Mb)
Mitsubishi Diamond plus 200 monitor
ps2 keyboard
USB mouse

If anyone has ideas, suggestions or questions they are very welcome

best regards
Eggert

Edit:  Turns out it was powernow daemon causing these problems.  Disabling it allows the computer to boot normally, and since it is not running on batteries I am not to concerned.

---

