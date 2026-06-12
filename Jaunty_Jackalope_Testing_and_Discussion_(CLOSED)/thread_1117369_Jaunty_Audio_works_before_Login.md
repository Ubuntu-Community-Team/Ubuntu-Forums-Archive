---
title: "Jaunty Audio works before Login"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jordanp123 on 2009-04-05
The audio for my seconday desktop ( A AMD athlon XP 2500+ with a Nforce 2 chipset). works when you login and that little sound plays, but once its has fully loaded the sound does not function what so ever. Any Idea's ?

---

### Post by Fenris_rising on 2009-04-06
Same boat here. From constant reading (I am now cross eyed) 2 'cures' may be- first one  in terminal;

```
killall pulseaudio
```

Which in some cases helps. The other is to disable the login sounds altogether and all other sounds then work. 

For now I am changing my install as I can't take the excitement anymore.

regards

Fenris

---

### Post by lindsay7 on 2009-04-06
I have the same problem with 9.04. No sound at all, nothing will play. I tried the killall command and still no luck. How do I disable the login sound as you mentioned?

---

### Post by jordanp123 on 2009-04-06
I wonder exactly whats changing between the login and the actual desktop loading, its seems like something is loading and its etheir not loading correctly, or its a bug in the software thats being loaded. Of course I could be completly wrong.

---

### Post by Fenris_rising on 2009-04-06
Hi there

System>Admin>Login Windows> Go to the accessability tab untick the sounds.

Good luck. For now I have admitted defeat and installed eeebuntu. But even there I had to go into Amarok and change its 'engine' from auto detect to Alsa for that to play my music. There is something wrong with the something in the ubuntu sound control I had to do the same on my PC's Amarok after months of no problems when it suddenly stopped playing my music.

Regards

Fenris

---

### Post by Fenris_rising on 2009-04-06
OK I just lost my Amarok sound and only one thing was changed between it working and not working.........

I have themed my desktop which includes 2 sound samples that are used for the login chimes. I have one to indicate ready and a second to indicate successful login.

With these installed and active via the login window (please note the 'Login screen ready' sound is ticked by default) I tick the 'login successful' box so that sound works as well. Reboot I get my login sounds thereafter no sounds whatever within the system.

Disabled both sounds in the login window, reboot (silently) and I have all my sounds back after boot (amarok, totem).

OK I kept my login ready sound ticked it's box, rebooted and got my login ready chime. Logged in and bearing in mind that the 'login success' chime is disabled it chimed anyway **but was the Ubuntu version** Not my own which is selected but is not as mentioned ticked to work.

**I believe this is the problem I was having with my jaunty and easy peasy installs as this is the only common factor in that I ticked the Login successful sound to work as well as changed the sounds to my own samples. Is this important to know as far as anyone else is concerned or is this set of circumstances particular to me and my set up. One other consideration is does the file format of the sounds have any relevance at all with the disruption of app sounds once logged into the system?**

**EDIT: I have just played around with my main PC where I have had the same problems and had worked around them with a lot of hit and miss poking around. I have again disabled the 'Login successful' sound by unticking it in the Login Window and again upon reboot my login ready works but obviously my now disabled succes chime doesn't BUT AGAIN THE UBUNTU CHIME DOES SOUND and now after weeks of head scratching totem player once again plays my DVD's and anything alse I throw at it. Is this a bug?**

regards

Fenris

---

