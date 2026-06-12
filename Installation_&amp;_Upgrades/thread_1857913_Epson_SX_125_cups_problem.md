---
title: "Epson SX 125 cups problem"
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by Yetojesse on 2011-10-11
ever since I upgraded my system, the printer stopped working... it keeps putting the files in a wait list and fails to print them.
I have cups 1.4.something and I heared that it gave a lot of problems... I'm pretty much a nub and I have NO idea how to downgrade to cups 1.3.11

please help me and keep it as simple as possible... 
I'm using ubuntu 11.04

---

### Post by Yetojesse on 2011-10-12
>bump<

Can't anybody help me?

All I need to do is sudo apt-get remove the current CUPS and install version 1.3.11. 
but I don't know if there is a command for that and when I got to the site, I have to download a file with instruction my computer doesn't understand (sudo make, sudo make ENTER?!)

---

### Post by Yetojesse on 2011-10-12
Problem solved! 

what the hell T_T

ok, for everyone who has the problem where he doesn't see a cupsys package or where the error is *error during the CUPS operation: client-error-not-possible*.
Just do this

Sudo apt-get remove cups
*I hope I don't have to explain this..

Sudo apt get install cups
*I can't explain this step -.-'

---

