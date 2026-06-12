---
title: "Unable to start xserver with ati card hd 6450"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by galgamo on 2011-10-16
Hi all!!

I'm trying to do a clean installation of ubuntu 11.10 in my desktop computer. I have an Ati/Amd hd 6450

I tried the live-cd and it worked well so i proceed with the installation. It finished ok.

But when it boots the screen keeps blinking with only one multicolor line at the top.

I thought that has to be the ati driver (i solved this problem in ubuntu 11.04 which i am running now) so i booted in recovery mode.

The first thing i noticed is that there isn't a failsafex option which there is in ubuntu 11.04 recovery mode.

Then i booted to command line and downloaded the latest ati driver for linux. I changed its permission and installed it (before i installed all the dependencies needed).

Everything was ok (i checked the fglrx log) so i run "aticonfig --initial" but it didn't work because the system miss libgl1.so.

Despite of that fact rebooted the system to try

This time i didn't get the blinking screen. it seemed to start xserver but it didn't.

Now i can see the initial post of telinit 3 but it froze. so i switch to console with ctrl+alt+f1 and run startx

i got "no screen found"

so i tried installing the package "fglrx" (what you should not) and rebooted again.

The fglrx ruined the ati driver, however now i could run aticonfig --initial. I did it and rebooted. Now i  got the login screen, which i shouldn't because i set autologin.

So i tried to log in but the xserver crashed and rebooted itself coming back to the login screen.

I don't know what to do more,

As i've said above, in ubuntu 11.04 i solved it booting into recovery mode, then into failsafex and then i click in additional drivers and installed the ati driver.

Any ideas?? May be the ati drivers doesn't work with the new kernel 3.0?

i also tried all this running first telinit 3 in the recovery mode console and it didn't work either.

Thanks for your help.

---

