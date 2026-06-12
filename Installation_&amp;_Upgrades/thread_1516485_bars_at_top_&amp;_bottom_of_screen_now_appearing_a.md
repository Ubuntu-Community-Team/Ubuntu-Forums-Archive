---
title: "bars at top &amp; bottom of screen now appearing after log-in"
date: 2010-06-23
forum: Installation &amp; Upgrades
---

### Post by eyehatehippies on 2010-06-23
So i just installed 10.04 and everything went rather smoothly. After signing in however the "utility bars" at the top & bottom of the screen are not appearing and clicking in those areas does nothing. The mouse moves smoothly, and i am still able to click as normal, but all i see is the cursor and the background. NOTHING else. A lil help?

Thanks In Advance,
gEoRgE

---

### Post by flick on 2010-06-23
Could try killing the panels. Usually they'll "respawn" right away when you do that.

Applications > Accessories > Terminal. Click on Terminal.

In the terminal window that opens, type :

killall gnome-panel

and hit Enter.

Your top and bottom panels may "respawn", reappear, however you like to think of it.

---

### Post by eyehatehippies on 2010-06-23
That's just it. I can't see or click on the upper or lower bars that're normally on the screen (just upgraded from 8.04). They're not present, and not clickable. I can get a standard right click reponse as per normal, but had to use a backwards method of connecting to the internet to even get advice.

Picture my screen as just my background and mouse cursor. NOTHING else. I cannot left click or select anything on the entire screen. 

-I have tried the "duh" concept of auto-adjusting the monitor. Didn't help. -I have tried restarting and didn't help. 

After initial install i was able to see the bars, look through programs, etc. As soon as i updated & restarted the bars disappeared and are now non functional and missing.

---

### Post by flick on 2010-06-23
Sorry about that. No problem. There are alternatives.

Hold down your Alt key, while holding it down, press your F2 key. That should give you a dialog box you can type a command in. Type in that box :

killall gnome-panel

and click the Run button. Maybe your panels will respawn.

---

### Post by eyehatehippies on 2010-06-23
Thank you VERY VERY much. I was able to get my bars back. Greatly appreciated and thank you so much for your speedy and helpful response. Much appreciated!
-gEoRgE

---

### Post by flick on 2010-06-23
Glad I could help. If your issue is truly resolved, edit your original post title and put SOLVED at the beginning, please -- helps forum moderators and other users see what issues are all done with. :)

---

### Post by eyehatehippies on 2010-06-27
tried to but couldn't figure out how  =(

---

