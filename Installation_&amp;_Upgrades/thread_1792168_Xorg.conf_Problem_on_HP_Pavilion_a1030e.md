---
title: "Xorg.conf Problem on HP Pavilion a1030e"
date: 2011-06-27
forum: Installation &amp; Upgrades
---

### Post by webusr1 on 2011-06-27
All,
I installed Ubuntu 10.04.2 on a HP Pavilion a1030e, it seems that X is crashing my Nautilus windows consistently and after running with no Nautilus windows over an hour the other applications lock up the screen. I'm struggling with the Xconfig. If I boot to RECOVERY MODE and select "failsafeX" Run in fail safe graphics mode, windows denotes "Ubuntu is running in low graphics mode" then I select radio button on next screen "Run Ubuntu in low graphics mode for just one session", and this works great.

How do I save this configuration? I've tried several things but it doesn't save this low graphics mode configuration.

I'm looking for a spare video card as alterative too. I'll keep you posted!

Thanks!

---

### Post by webusr1 on 2011-06-27
All,
I was able to Google the answer... Here's my solution in case it comes in handy for someone else.

1. CTRL+ALT+F1  (This takes you to a Terminal window)
2. sudo service gdm stop
3. sudo Xorg -configure
4. sudo service gdm start

NOTE:A new file xorg.conf.new will be generated in you current working directory

5. sudo cp xorg.conf.new /etc/X11/xorg.conf
6. sudo vi /etc/X11/xorg.conf
NOTE: edit xorg.conf file for you system if needed. For my system I could only use "vesa" for Driver or my system crashed after using it for some time.

Reboot system so that the new xorg.conf can take affect. System fixed.

---

