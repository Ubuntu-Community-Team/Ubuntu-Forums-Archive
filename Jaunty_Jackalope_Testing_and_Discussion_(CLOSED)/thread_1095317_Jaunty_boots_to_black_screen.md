---
title: "Jaunty boots to black screen"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xeddog on 2009-03-13
I just installed Jaunty Alpha 6 (Kubuntu) on an old machine and it boots to a black screen with a cursor on it.  I read a thread where some people were having this problem with intel graphics, but I have an nVidia 6200 card in this machine.  I tried their resolution (remove "quiet splash" from the startup command) anyway with no luck.

Any other ideas??   

TIA, 

xeddog

UPDATE:  I swapped the nvidia 6200 graphics card with an ATI Radeon 9600 and did a fresh install of Kubuntu 9.04.  Same problem.

---

### Post by Flag on 2009-03-14
Had the same, System -> Prefs -> Appearance -> Visual Effects set to none.
In the black screen hit Alt + Ctrl + F6 or F7 to get a normal screen.

---

### Post by Azhtabak on 2009-03-14
I'm having the same problem - it was working fine until today though, so could it have been something in an update today? I seem to remember downloading one.

---

### Post by Azhtabak on 2009-03-14
Actually, Nevermind, I don't think it is, that shortcut doesn't seem to be working with mine.

---

### Post by zer0max713 on 2009-03-14
Issues Upgrading from Ubuntu 8.10 to 9.04 Jaunty Jackalope
OK here it goes, so i attempted to upgrade from 8.10 to 9.04 and after completing the install and rebooting, when i attempt to login everything freezes. I am able to put in my username and password but from there i get a black screen with a weird white bar right in the center. I did this with an existing install and a clean install of 8.10. Has anyone run into this issue? If so, where you able to fix it? Any input would be greatly appreciated. Thank you all in advance.(Newbie)

---

### Post by lanzen on 2009-03-14
I've tried testing alpha 6 on my eeepc and I got the same. I've seen some crash warnings. One was about plasma, I think.

I've later tried the AMD64 version for my Desktop PC in virtual box and the same thing happened.

In tty1-6 the system seems to be up, but I've no idea how to fix it.

Seemed fine in alpha 5.

---

### Post by Halow on 2009-03-14
I was having much the same problem as zer0max713. When I got to GDM, I'd get a quick glimpse of the text box, but it was seeming that X crashed. The screen would go... rainbow colored(?) a moment, then black, with a large white box in center in which I could type nothing. Jaunty simply refused to boot. This happened this morning, after a fresh install of alpha six and update yesterday.

---

### Post by jerrylamos on 2009-03-14
Just in case the recent compiz changes are causing trouble (again):
Boot in recovery mode.  When the options window appears,
Select root shell prompt
apt-get remove compiz compiz-core
reply y or whatever it may ask for
exit
resume normal boot

Jerry

---

### Post by lanzen on 2009-03-14
Solved. See [Kubuntu Forum]("http://kubuntuforums.net/forums/index.php?topic=3102117.30#bot")

---

### Post by xeddog on 2009-03-14
Thanks for the tip lanzen.  Worked for me too.

xeddog

---

