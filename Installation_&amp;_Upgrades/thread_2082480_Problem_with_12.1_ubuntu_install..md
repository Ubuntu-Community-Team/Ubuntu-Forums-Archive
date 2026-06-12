---
title: "Problem with 12.1 ubuntu install."
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by retsek on 2012-11-09
Hey all, 

I've just upgraded from 12.04 to 12.1 i'm currently running a sony vaio with an ATI chip (i know stupid me, but i didn't know much about linux when i got the laptop...) 

basically when ubuntu boots i get the normal log in screen can see the taskbar at the top with all icons working normally, after i log in, the screen is stuck in 4:3 (on a widescreenlaptop) horiffically zoomed in so i can't see the side or top bar. the 'start' button doesn't open the app screen and i can't use / to boot programs. 

by using the GUI to go into the change desktop background screen i can get into the system settings (the mouse hides behind icons) to try and upgrade my graphics driver. but as none have been released i'm unsure of what i can do. 

I can get onto the terminal using ctrl+alt+F1 (or shift i never remember which) but i'm unsure of what i should be doing... 

Any advice would be fantastic as i'm just stuck using win7 on the other partition at the moment. 

Thanks in advance. 

Kes (retsek)

---

### Post by Mr_JMM on 2012-11-09
1. It's 12.10 not 12.1.

2. If you can get to synaptic package manager, install the fglrx driver. For some reason I had no problems with ATI until 12.10 then the new driver that was auto installed didn't like it. This solved it for me.
You might have to remove the installed driver but I forget how to do that. Hopefully someone can fill you in there until I can get back home to check, then I'll update.

Also, once done it took 2 reboots to work correctly.

---

