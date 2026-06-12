---
title: "GTA San Andreas in WINE..?"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by Rush3d on 2010-06-17
Ok i've heard alot of people say that GTA works in WINE.

Truth is it doesn't for me

I bought the game, and tried to install it. When I tried to run it, my screen went to a bigger resolution and just stopped..

Can anyone give me some files that WORK? Or maybe tell me how to fix this?

---

### Post by Rush3d on 2010-06-17
[CENTER]Bump
[/CENTER]

---

### Post by radddi on 2010-06-17
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780)

Acording to this thread San Andreas works fine in Wine. Read it through and look for similar problems - there might be solutions for them. I'm guessing that your Wine needs configuration. This includes DirectX and often NET Framework.

One question though. You said that your screen stops. Is this a PC crash or are you able to safely stop it and return to Ubuntu? If it's a computer crash then it's probably much greater trouble.

---

### Post by Rush3d on 2010-06-17
My computer doesnt crash..

You know when you like start up a fullscreen game and your screen goes to a bigger resolution?

Its like that, only the game doesn't start up, and I have to change my resolution back.

Here are my specs:

Im running ubuntu 8.04 Hardy Henry

I have WINE 1 .0 according to the info tab.

Would upgrading to 10.4 fix it..?

Or maybe a newer version of wine..? Because on the WINEHQ it said there was a newer one.

I did

> sudo apt-get update

and I still had the same version of Wine.

---

### Post by Labus on 2010-06-17
Do these things in terminal to get the newest wine

sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo apt-get update

If this doesn't work, read the link radddi gave you. Others might have had the same problem, an solved it.

---

### Post by Rush3d on 2010-06-17
when i do the first command I get an error:
> sudo: add-apt-repository: command not found


---

### Post by lechien73 on 2010-06-18
The words in the command were transposed, the correct command is:

```
sudo apt-add-respository ppa:ubuntu-wine/ppa
```

---

### Post by Labus on 2010-06-18
Oh, my bad.
Corrected it

---

### Post by Rush3d on 2010-06-18
> root@HOSTBOx:~# sudo apt-add-repository ppa:ubuntu-wine/ppa
sudo: apt-add-repository: command not found



Still not working >.>

Should I upgrade to 10.04 Ubuntu? Or stick with my 8.04?

Or like someone give me an updated wine version.

---

