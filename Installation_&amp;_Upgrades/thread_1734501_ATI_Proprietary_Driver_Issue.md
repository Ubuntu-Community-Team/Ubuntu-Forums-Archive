---
title: "ATI Proprietary Driver Issue"
date: 2011-04-20
forum: Installation &amp; Upgrades
---

### Post by penguineggtheif on 2011-04-20
I installed Ubuntu 10.10 from the Ubuntu website. Everything installed correctly, and the first time boot was successful. I installed all updates, and rebooted. Everything was still working. I then installed the Proprietary ATI Drivers. When I restarted My computer I was at a black "out of range" on my LCD TV.
               I rebooted and tried to figure it out in failsafe graphics mode to no avail. I went into recovery, and reset display configuration, and was able to boot regularly again. My video driver wasn't setup. I installed it again, and rebooted to the same out of range.
               I know to hit CTRL+ALT+F1, F7, and F9. I have tried multiple commands in the terminal to fix this problem, and have been browsing on ubuntu forums for a few days now. I can get it to boot without my ATI driver, but "out of range" every other time. I have tried the command with "-phigh" to reconfigure xorg. And no resolution choices come up. I would really like a little help please.

The graphics card is a ATI Radeon HD 4870.

---

### Post by Jechem on 2011-04-20
Maybe this can help:
[http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Updating_the_Driver)

---

### Post by penguineggtheif on 2011-04-20
Thanks for the link. I tried for a few more hours and still nothing. More than half the time I follow the commands given I just keep getting errors. I switched from windows, and now I can't even get my video card to work... maybe someone could link me a copy of their xorg.conf?

---

### Post by coffeecat on 2011-04-20
Maybe the best thing would be to purge the proprietary driver and re-install the open source driver for which you need no xorg.conf. At least then you should have a system with a GUI from which you could start again.

This link gives you all the commands you need, because some bits of the proprietary driver can be persistent.

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I would guess the best thing would be to boot up in recovery mode and drop to a root shell with networking. Then you would be able to run all the commands under "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch", but without the sudo. It's possible that "dpkg-reconfigure xserver-xorg" will remove any xorg.conf but you might want to do that yourself to be sure.

By the way, was the open source driver not adequate for you? I get perfectly good 3d (enough for compiz) with the open source driver and my Radeon HD4350 card.

---

### Post by penguineggtheif on 2011-04-21
I am very new to Ubuntu, so when it prompted me to install the proprietary driver I just thought that was the best plan of action. I have had nothing but problems with it so far, so I think I need to use the open source driver as was suggested. I will give it a try, thanks. I would like to just be able to play full screen 3d games, as fast as possible.

---

