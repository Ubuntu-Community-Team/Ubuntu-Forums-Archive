---
title: "esd causes login process to lock?"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by wdr1 on 2007-04-15
I've just installed Ubuntu 6.06 on a tower Intel PC at home.  So far pretty smooth.  I can get to the login screen, but after entering my name & password, I get a black screen + mouse cursor, but nothing else. 

 If I ssh into my box and 'killall esd' everything moves forwards fine.  (If I don't, it'll stay like that forever -- I've let it set for hours.)

I've double-clicked the sound icon & changed the device to my SoundBlaster card (using Asla).  

The irony is that I don't even have speakers hooked up, and don't even care about sound! :)

Can I make esd permanently go away?

TIA,
-Bill

---

### Post by kerry_s on 2007-04-15
Uninstall it with synaptic the packages are "esound-?" I'm not sure which ones ubuntu installs. Mines a custom install and i have all of them installed. There are 3 of them so just uninstall whats there.

---

### Post by wdr1 on 2007-04-15
Exactly what I was looking for...

The only gotcha seems to be that ubuntu-desktop says it's dependant on it? :(

---

### Post by christhemonkey on 2007-04-15
That shouldnt matter, ubuntu-desktop is just a metapackage.

If you want to disble esd, go to the sounds dialog and click disble system sounds, this stops it ever loading! :D

---

