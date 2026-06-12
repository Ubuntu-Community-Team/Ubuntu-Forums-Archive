---
title: "Problem with LM 17 Xfce Power Manager"
date: 2014-11-22
forum: MINT
---

### Post by Vladimir Pavic on 2014-11-22
[COLOR=#003300][FONT=Verdana]Dear Friends,[/FONT][/COLOR]

[COLOR=#003300][FONT=Verdana]A week ago I had Linux Mint 17 Xfce installed on my laptop (Dell Inspiron 1545). It has the same desktop environment as Xubuntu 14.04.The persistent problem is that after 10 minutes of inactivity, the screen turns black. It gets back to life as soon as a key is touched or the mouse moved. It happens even during video and audio play. I am pulling my hair out. In spite of the settings that you could see in the images, it seems that Thunar doesn't remember the command. None from LM community could give me the solution. How to disable this automatic blackout? What to do? [/FONT][/COLOR]

[COLOR=#003300][FONT=Verdana]Thank you in anticipation.[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-11-22
Look in the other side-tabs in Power-manager as there is a Monitor setting section in the On **AC tab** and also **On Battery** if running on a laptop.

---

### Post by Vladimir Pavic on 2014-11-22
Setting on **AC tab** is the same (so is the problem). I don't see battery tab anywhere. Is there any third party, external Power Manager program?

---

### Post by Dennis N on 2014-11-22
The 10 minute screen blanking is caused by the DPMS system (Display Power Management System).

[http://www.computerhope.com/jargon/d/dpms.htm](http://www.computerhope.com/jargon/d/dpms.htm)

To stop it from activating, install xscreensaver and add it to your startup applications. The command is **xscreensaver -no-splash** 

As long as the xscreensaver daemon is running, it will inhibit the DPMS from putting the screen in standby mode (blank). Check the screensaver settings in **Settings > Screensaver** and either set it to disabled (screen will always be on), or use a screensaver and set the activation time. In either case, DPMS is inhibited. 

This works in Xubuntu 14.04. It may work for you. It also works in Linux Mint 17 MATE. Linux Mint 17 Cinnamon doesn't seem to have this problem.

---

### Post by Vladimir Pavic on 2014-11-23
[SIZE=3][COLOR=#800000][FONT=Verdana]Dear Dennis N, thank you very much for this valuable advice. It works! I can't believe my eyes. All Xfce users should do this immediately upon OS installation.[/FONT][/COLOR]
[COLOR=#800000][FONT=Verdana]Thank you.[/FONT][/COLOR]
[COLOR=#800000][FONT=Verdana]Greetings from Croatia![/FONT][/COLOR][/SIZE]

---

### Post by Dennis N on 2014-11-23
Thanks for the feedback - I'm glad to hear that this tip worked for you.

---

