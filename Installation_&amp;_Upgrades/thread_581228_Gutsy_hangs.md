---
title: "Gutsy hangs"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2007-10-19
I have two machines that I have upgraded to Gutsy, both of them 2-3 days before the official release (one laptop, one stationary). 

The laptop is a Toshiba Tecra. It was upgraded from Feisty to a Gutsy prerelease. After the release I have run apt-get update and apt-get dist-upgrade (which didn't actually do anything).

When using apt-get, it complains that three packets, libxml-sax-perl, libxml-libxml-perl, and libxml-simple-perl have dependency problems and can't be configured, but it doesn't list any packets as needing updates.

If I leave this machine on and not doing anything, it will hang after a few hours. The screen is black (my screensaver is all-black, so that's somewhat unsurprising) but you can tell that it's on since it's somewhat lit up. The only thing it reacts to is holding the power button down for five seconds to turn it off. 

In /var/log/messages, I see a number of lines reading "-- MARK --", then "syslogd 1.4.1#21ubuntu3: restart", then a reboot. Judging from the times, the mark lines appear before the crash and everything else after.

The stationary machine has been upgraded in the same way and also crashes. The only difference is that I don't have it handy here to check the logs, and that it will display thin diagonal lines on the screen when hanging, otherwise everything is the same.

This definitely isn't an improvement over Feisty (even if my wireless LAN works better). Please help!

---

