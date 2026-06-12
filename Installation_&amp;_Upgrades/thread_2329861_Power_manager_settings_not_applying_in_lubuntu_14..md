---
title: "Power manager settings not applying in lubuntu 14.04.1"
date: 2016-07-05
forum: Installation &amp; Upgrades
---

### Post by michael_brown2 on 2016-07-05
Hey everybody

I couldn't really find the perfect sub-forum to which I should post this, so this will have to suffice, since it is an issue with a downgrade.

On an ASUS Eee PC R101, I'm running lubuntu 14.04.1 due to external monitor output issues with later versions. 

I go into Xfce Power Manager and change the settings as follows: 

Under both "On AC" and "On Battery", I set the following:
"When laptop lid is closed:" "[do] Nothing"
"Put the computer to sleep when inactive for:" to "Never" 
"Put display to sleep when computer is inactive for:" to "Never" 
"Switch off display when computer is inactive for:" to "Never" 
"Reduce screen brightness when computer is inactive for:" to "Never"

However none of these settings seem to apply properly. When I shut my screen, my computer still goes into suspend mode and if left inactive for a while, the computer still shuts off and locks the screen.

If you could give me any ideas on how to fix this, I'd really appreciate it.

Thanks
Michael_Brown

---

### Post by Dennis N on 2016-07-05
Your display is also affected by Light Locker which is installed in Lubuntu 14.04. Check the Light Locker settings (Preferences > Light Locker Settings), and under screensaver section, set "Blank Screen after" and "Switch off display after..." to Never.

---

### Post by michael_brown2 on 2016-07-06
Checked. The settings are already set the way you described. It appears that when I changed the settings to appear that way way in "Power Manager", the settings would appear the same way in "Light Locker Settings", however the system still goes into suspend when I shut the screen, so I still have the same problem.

---

