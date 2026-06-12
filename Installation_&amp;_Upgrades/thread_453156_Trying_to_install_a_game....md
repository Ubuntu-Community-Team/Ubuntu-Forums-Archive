---
title: "Trying to install a game..."
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by LiNoobster on 2007-05-24
Hello I was trying to install a game and I get a message "No write permission to /usr/local/games". How do I get a write permission?

---

### Post by renzokuken on 2007-05-24
you need to be root (i.e. use sudo) to write to that directory.

what game are you installing and how are you installing it?

---

### Post by LollYouSuckZor on 2007-05-24
Yeah really, what game are you trying to install? If It's BF2, Give up now... If it's a free game, there may already be a Linux version...

---

### Post by LiNoobster on 2007-05-24
I'm trying to install this game : [http://www.garagegames.com/products/12/](http://www.garagegames.com/products/12/)

I am using the : /home/name/Desktop/name.bin    to install this game but I think I need to be under root administrator which I never made and don't know what the password would be. It starts installing but stops at the need permission thing.

---

### Post by LollYouSuckZor on 2007-05-24
Is that game really worth it?

---

### Post by stefaan.dutry on 2007-05-24
type **sudo** in front of the command.  That gives you root priveleges for the command behind it.  It will ask for your password, just type your normal password.  (gksudo if you want a window poppup for your password)

```
sudo command
```

---

### Post by LiNoobster on 2007-05-24
Yes it is worth it to me, it is FUN. Here's the game website : [www.planetthinktanks2.com](www.planetthinktanks2.com)

sudo command : not found?...tried it

---

### Post by stefaan.dutry on 2007-05-24
instead of command you needed to put the command you use to install it

or if it's just opening the file then just type 

sudo /home/name/Desktop/name.bin

---

### Post by LiNoobster on 2007-05-24
Thanks...I got it now and it is installed but when it is about to start it does'nt work - got some kind of an error about i think graphic??? But the other games that were preinstalled work fine?

---

### Post by EndPerform on 2007-05-24
> **LiNoobster said:**
> Thanks...I got it now and it is installed but when it is about to start it does'nt work - got some kind of an error about i think graphic??? But the other games that were preinstalled work fine?

The preinstalled games might not have the same requirements as the game you're trying to install.  It sounds like the game you installed is looking for a library that's not installed.  Could you post the error message?

---

### Post by littlescout on 2007-05-24
will bf2 work on any linux?? if yes what one??

---

### Post by LiNoobster on 2007-05-24
Do the error messages get logged somewhere cause I did'nt write down the error I got??? Does it have to do with the Open GL thing for the game?

---

### Post by LiNoobster on 2007-05-25
Thank-you for those that tried to help but I got it running now after upgrading to 7.04.;);):D

---

### Post by LiNoobster on 2007-05-27
One other thing...the sound on this game echoes. Game runs fine but the echoes on the sound is annoying.

---

