---
title: "[upgrade]Gutsy Gibbon 7.10 to Hardy Heron: Login screen freeze!"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by sriki on 2008-08-12
Hi
I did manage to dual boot my HP dv2401 latop with vista and Ubuntu gutsy gibbon 7.10.
Everything was perfect until I did an upgrade to Hardy Heron using upgrade tool provided by update manager. Upgrade went smoothly without any problems; however when I rebooted my system Ubuntu freezes at login screen. I can just see the orange screen with no login prompt. 

I have tried the following so far
1. Booted my system in recovery mode and tried reconfiguring the Xorg.
2. Added the following lines in xorg.conf file under "Screen" section
SubSection "Display"
Depth 4
Modes "1024x768" "800x600" "640x480"
EndSubSection

I'm a newbie and tried the above looking at threads in forum
Kindly someone help me solve this

Thanks in advance!

/Sriki

---

### Post by Partyboi2 on 2008-08-12
You may have struck [[COLOR=Blue]this bug[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434"). There is a workaround and possible fixed mentioned.

---

### Post by btc50 on 2008-08-12
I tried the same upgrade scenario 7.1 to 8.04.1 and I have a hangup in the same place. I too can get to terminal via alt+ctrl+F1. The funny thing is that everything passes as OK in recovery mode. I can login to GNOME failsafe and I get the following two errors:

Internal Error: Failed to Initialized HAL!

and

The panel encountered a problem when loading: OAFIID: Deskbar_Applet. Do you wish to delete this applet? 

These are the only two errors I have to go on.

Any Ideas?

---

