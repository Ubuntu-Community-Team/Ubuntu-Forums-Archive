---
title: "[SOLVED] Appearance preferences selecting extra error + Compiz + AWN Help!"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by wilsong on 2008-10-01
Ok, This is really frustrating, 

I used to have this working, at first when i installed 8.10 I went an switched it to EXTRA (i have a Dell Insprion E1405 with the Intel GMA945) 

This worked great! so i installed CCSM (Compiz Config Settings Manager) 

Which worked GREAT! I had the settings i set in compiz that i liked and it would come back up when i restarted.. 

I installed AWN (Avant Window Navigator) which i used to replace my "task bar" (basic config nothing really special) 


I installed some more things and went on using ubuntu, and i somehow installed ubuntustudio-look and it changed the look of some windows and i tried to remove it and was able to get back to my old look

Somehow through this i started noticing that AWN wasnt at the bottom anymore, so i tried to run it through terminal and it gave the warning that i needed to have compiz up 

So i was a little upset like GRR compiz should be running, well I went first to look to make sure it was still on EXTRA, but it was on NONE 

when i try to switch it to EXTRA it says in an error box just "Desktop effects could not be enabled" 

BUT if i go into a terminal window and i type "compiz" i can get Compiz up, AWN launches! and thinks look simi normal again (expect that all the compiz settings i liked have all lost :(

BUT when i restart, it all goes away, I have to launch terminal or leave a terminal window open (i tried compiz & to put the process in background but it didnt seem to work) 

Can anyone  help me get compiz running when it  boots, and i think it has to do with the EXTRA is there any more information to find out why it cant change to extra instead of just that simple generic error?  PLEASE RESPOND! THANKS IN ADVANCED!

---

### Post by wilsong on 2008-10-01
Anyone seen this? Really bugs me heh.

---

### Post by wilsong on 2008-10-02
I am still having this issue.. I cannot figure it out.. Compiz is still working I just dont know whats going on.. ? anyone have any ideas?

---

### Post by wilsong on 2008-10-02
I have a new update, i joined #compiz and was trying to get help , it seems that i cant even add a startup item to the sessions, startup to do a run of compiz --replace at boot, i put that into it , but it still doesnt run. 

I tried several things, theres a window manager item that loads "gnome-wm" but i unchecked that, 

I just wonder why it wont let me click extra,  saying that the setting could not be enabled.. 

but then when i run compiz and click extra it says "do you want to keep the settings or change back to the original settings within the next 40 seconds" and if i hit keep it changes it to extra, but then compiz closes (i assume this because awn closes) 

This is really wired since i cant run compiz at start any ideas or things i could try even however simple willing to listen

---

### Post by wilsong on 2008-10-02
Well I eventually solved this with help from someone on IRC. 

I dont know why or how it worked but this is how i did get it going.. 

I tried several times to add compiz to start up, but never really had success


I eventually did '  apt-get install fusion-icon  '

once that was installed i flicked system, pref, sessions, startup, and added a startup calling it compiz and putting in the run  "  fusion-icon  " 

and now it works,

---

