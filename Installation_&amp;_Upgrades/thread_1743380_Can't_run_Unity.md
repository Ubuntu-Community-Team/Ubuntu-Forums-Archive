---
title: "Can't run Unity"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by lapalorky on 2011-04-29
I just upgraded to 11.04 and I can't run Unity. The following error shows, but I don't know what to do about it:

```
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

compiz (core) - Error: InitPlugin 'unityshell' failed
compiz (core) - Error: Couldn't activate plugin 'unityshell'
```Please advice me.

---

### Post by leeman101 on 2011-04-29
Can you boot into recovery mode > failsafe graphics (low graphics)??
If so, do that, and then go to system settings > additional drivers > and check for proprietary graphics driver update.  Make sure you are connected to the internet, of course.  This worked for me when I was unable to get unity funning, however I had a different error happening.  Good Luck.

---

### Post by lapalorky on 2011-04-29
Thank you for your answer. But unfortunately this didn't help. There is nothing in this list. I have run compiz without problems for a long time, I have a ATI radeon graphics card.

---

### Post by leeman101 on 2011-05-02
Bummer :(
My graphics card is ATI as well.... Mobile Radeon HD 3200.  I had problems, and i fixed it by doing what i mentioned above.  
I guess your situation is different.
are you able to boot into recovery mode at all? do you get a grub menu?

---

### Post by lapalorky on 2011-05-02
It works now. I did the [this]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch"):
```
sudo apt-get remove --purge fglrx*   
sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon    
sudo apt-get install xserver-xorg-video-ati   
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core  
sudo dpkg-reconfigure xserver-xorg
```And then logged in to a newly created user-account. There it works just fine. To bad I have to move a lot of stuff from my old user-account though.

---

### Post by Le Gluon du Net on 2011-10-28
lapalorky: your solution works for my friend wich have an ati video card, thank you very much.

LGDN.

---

