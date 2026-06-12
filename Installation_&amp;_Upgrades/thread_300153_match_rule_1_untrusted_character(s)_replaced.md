---
title: "match_rule: 1 untrusted character(s) replaced"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by punter1 on 2006-11-15
[SIZE=2][COLOR=#000000][FONT=Courier New]I have been investigating a problem with a usb joystick that does not generate any output in edgy.](*,) [/FONT][/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000][FONT=Courier New]While checking the udev stuff, I came across the following:-[/FONT][/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000][FONT=Courier New]When I run:-[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Courier New]... udevtest /class/input/js0[/FONT][/COLOR][/SIZE]
 
[SIZE=2][COLOR=#000000][FONT=Courier New]I get:-[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Courier New]... match_rule: 1 untrusted character(s) replaced[/FONT][/COLOR][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Courier New]as part of the output?[/FONT][/COLOR][/SIZE]
 
 
[COLOR=black][SIZE=2][FONT=Courier New]Does anyone have any ideas as to what could be causing this (apart from the obvious).[/FONT][/SIZE][/COLOR]
 
[COLOR=black][SIZE=2][FONT=Courier New]I have not modified any of the the /etc/udev/rules.d files so the problem should be reproducible. [/FONT][/SIZE][/COLOR]
 
[COLOR=black][SIZE=2][FONT=Courier New]Regards[/FONT][/SIZE][/COLOR]
[COLOR=black][SIZE=2][FONT=Courier New]Bill[/FONT][/SIZE][/COLOR]

---

