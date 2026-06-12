---
title: "Can't get VLC to start ! Pls help"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Siamstat on 2011-06-19
Hello everyone . I just started to work on Ubuntu and i'm having a problem with vlc , i can't get it to run i'm not trying to run it as user Root , i followed this tutorial from google [http://www.webupd8.org/2010/06/how-to-install-vlc-110-final-in-ubuntu.html](http://www.webupd8.org/2010/06/how-to-install-vlc-110-final-in-ubuntu.html) . The problem is that I installed VLC and all seem well,i can find it in Applications > sound and video > VLC but when i click on it to run it nada , nothing happens , this is the error i get when in terminal i use "vlc" command 

> VLC media player 1.0.6 Goldeneye
[0x92414d0] inhibit interface error: Failed to connect to the D-Bus session daemon: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
[0x92414d0] main interface error: no suitable interface module
[0x91aa148] main libvlc error: interface "inhibit,none" initialization failed
No protocol specified
[0x9240560] main interface error: no suitable interface module
[0x91aa148] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x91aa148] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
No protocol specified
[0x9241710] qt4 interface error: Could not connect to X server
No protocol specified
[0x9241710] skins2 interface error: Cannot open display
[0x9241710] skins2 interface error: cannot initialize OSFactory
Remote control interface initialized. Type `help' for help.Thanks in advance for any info you might provide me with . Cheers!


Edit : Spellcheck

---

### Post by Siamstat on 2011-06-20
No one can help me ?

---

### Post by waynerod on 2011-06-20
You're running Ubuntu 11.04 right? The link [which you looked at]("http://www.webupd8.org/2010/06/how-to-install-vlc-110-final-in-ubuntu.html") is almost a year old. So there may be some problems with it (PPA may be outdated). 

I think VLC is already included in the Ubuntu repos, at least in the universe repo. So, my suggestion would be to go to "Software Sources" and remove that PPA which you just added. Then, Make sure "Universe" and "Multiverse" repos are enabled. Then search for "VLC" via "Ubuntu Software Centre". That should work now.

It may or may not solve your problem, but at least its worth a shot (and you'll have VLC up to date). At least you got something to try as I can see no one else has replied yet...

---

### Post by Gotlieb on 2011-06-20
Hi,

Did you try re-installing it? Did it work before?

---

