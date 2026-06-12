---
title: "installing yahoo messenger"
date: 2012-03-23
forum: Installation &amp; Upgrades
---

### Post by Jinkeez on 2012-03-23
i was installing yahoo messenger in my ubunto following instructions from a website, I wrote in the terminal:

sudo apt-get install libssl0.9.6

and I got following error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libssl0.9.6
E: Couldn't find any package by regex 'libssl0.9.6'

Can someone please help me out with how to solve this issue and move on...thanx

---

### Post by 0011235813 on 2012-03-23
I don't believe Yahoo! Messenger is compatible with Ubuntu. Your best bet is to download the previous version of it (I think it's v8, but you can check WineHQ). Download the .exe and run it under wine. If you don't already have it installed:
```
sudo apt-get install wine
```
```
winecfg
```
and then you can open the .exe with Wine Windows Program Loader graphically by right-clicking, or command by typing *cd /home/<username>/Downloads * or where ever you left the exe and use 
```
wine <program name>.exe 
```

---

### Post by Frogs Hair on 2012-03-23
Hello and Welcome

Pidgin IM in the software center can connect to Yahoo . Also check for other threads with the search tool because the subject has come up before . Instructions for versions of Ubuntu prior to 11.10 may no longer work though.

---

### Post by mastablasta on 2012-03-24
pidgin is rubish. it can connect to Yahoo and you can chat on it, but that's about it.

the client that is the most compatible with yahoo messager (which won't work in Linux) is Gyache improved. Latest verison is here: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)

Install instructions are in the file you will download. simply copy the commands in terminal.

another option is to use a PPA: [http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)


not that graphics and all is not as imptressive as YM, however this is the most compatible client with YM i've seen.

---

### Post by dwpbike on 2012-07-27
> **mastablasta said:**
> pidgin is rubish. it can connect to Yahoo and you can chat on it, but that's about it.

the client that is the most compatible with yahoo messager (which won't work in Linux) is Gyache improved. Latest verison is here: [http://sourceforge.net/projects/gyachi/](http://sourceforge.net/projects/gyachi/)

Install instructions are in the file you will download. simply copy the commands in terminal.

another option is to use a PPA: [http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html](http://www.ubuntugeek.com/how-to-install-gyachi-on-ubuntu-11-04-natty-using-ppa.html)


not that graphics and all is not as imptressive as YM, however this is the most compatible client with YM i've seen.

i take exception to your remarks on pidgin and "rubbish" has two "b's".  i have used pidgin on ubuntu and fedora for over 5 years.  pidgin is for im (instant message) and it performs as billed.  i have done both video and audio, but im suits me fine.  i don't have to get dressed and i don't get interrupted when i speak.

---

