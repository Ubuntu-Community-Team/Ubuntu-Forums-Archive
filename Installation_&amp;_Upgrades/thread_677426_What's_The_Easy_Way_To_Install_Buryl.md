---
title: "What's The Easy Way To Install Buryl?"
date: 2008-01-24
forum: Installation &amp; Upgrades
---

### Post by adn258 on 2008-01-24
Okay so I read the guide that comes with the package it says aquamarine-0.2.1 and anyway it says go to the directory in the terminal and type make install and then you can install it but I get what it says below what do I do?  Any help is appreciate your guys are a major help.

Peace

austin@bomb:~$ cd /home/austin/Desktop/aquamarine-0.2.1/src
austin@bomb:~/Desktop/aquamarine-0.2.1/src$ make install
make: *** No rule to make target `install'.  Stop.
austin@bomb:~/Desktop/aquamarine-0.2.1/src$

---

### Post by taurus on 2008-01-24
Which release are you running because Gutsy comes with compiz-fusion.  It's a replacement of beryl.  You just need to install a driver for your graphic card to enable 3D and then you can activate compiz-fusion.

---

### Post by adn258 on 2008-01-24
> **taurus said:**
> Which release are you running because Gutsy comes with compiz-fusion.  It's a replacement of beryl.  You just need to install a driver for your graphic card to enable 3D and then you can activate compiz-fusion.

Okay I have comp Fusion but how do I make it work and yes my 3d card supports it

---

### Post by adn258 on 2008-01-24
> **adn258 said:**
> Okay I have comp Fusion but how do I make it work and yes my 3d card supports it

okay I got it working and the cube and everything but friend how do I like install beryl too?

---

### Post by FuturePilot on 2008-01-25
Compiz Fusion is way better than Beryl. It would only be redundant since they are both composite managers and you can only have one composite manager running at a time. Compiz Fusion can do everything Beryl can and more. Not to mention development on Beryl has stopped since it was merged back into Compiz which is now Compiz Fusion.

---

### Post by adn258 on 2008-01-25
> **FuturePilot said:**
> Compiz Fusion is way better than Beryl. It would only be redundant since they are both composite managers and you can only have one composite manager running at a time. Compiz Fusion can do everything Beryl can and more. Not to mention development on Beryl has stopped since it was merged back into Compiz which is now Compiz Fusion.

alrighty :) thank you all I really appreciate you all your so nice and helpful I seriously mean that and everything on Linux is free which is amazing.  Umm but like lol can you tell me how do I get the effects like in this video?  The windows like explode and stuff.  

[http://youtube.com/watch?v=xC5uEe5OzNQ](http://youtube.com/watch?v=xC5uEe5OzNQ)

---

### Post by FuturePilot on 2008-01-26
```
sudo apt-get install compizconfig-settings-manager
```
Then you can go System>Preferences>Advanced Desktop Effects Settings and configure everything for Compiz there. Specifically for the exploding windows look under the Animations plugin.

---

