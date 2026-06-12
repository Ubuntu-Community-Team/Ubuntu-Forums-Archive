---
title: "I Can not Access By My Name !! Permissions problem"
date: 2006-04-10
forum: Installation &amp; Upgrades
---

### Post by Me! on 2006-04-10
Jus I install some applications & system base & edubuntu .. after rebooting I can not access by any user (root only)

Login error msg:
$HOME/.dmrc premissions problem

if I want to login from terminal
/home$/ startx
/usr/bin/startx: line 133: cannot create temp file for here document: No space left on device
xauth:  timeout in locking authority file //.Xauthority
/usr/bin/startx: line 145: cannot create temp file for here document: No space left on device
xauth:  timeout in locking authority file //.Xauthority
/usr/bin/startx: line 145: cannot create temp file for here document: No space left on device

X: user not authorized to run the X server, aborting.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

giving up.
xinit:  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  timeout in locking authority file //.Xauthority

Please help me

---

### Post by rmjokers on 2006-04-10
Well, first of all the errors seem to indicate that at least one of your partitions (maybe whichever contains /tmp) is completely full.  You might want to run 'df' in the terminal and make sure you still have space on disk.

---

### Post by Kresten Kjaer on 2006-04-10
And please run:
ls -l /home/
And tell us your username

---

### Post by Me! on 2006-04-11
Thank you !

the problem is with my space .

but The system not give me a warning msg for that !

Thank you rmjokers
Thank you Kresten Kjaer too

for your replys

---

