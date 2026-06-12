---
title: "Upgrade failed from 12.04 to 14.04"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by Rustom_Billimoria on 2014-07-21
Hi Guys,

This is the first time I am posting here.

I have a Dell XPS L502x

I recently upgraded fro Ubuntu 12.04 desktop (x64) to 14.04. When I started the update procedure, everything seemed fine. When the update ended, it told me that errors had occured. Ignoring that I rebooted my laptop. I saw the Ubuntu 14.04 splash screen to login. When I tried to login, It gave me an error that session failed to start. At this point of time my wireless and wired connection both were working. I Pressed CTRL + ALT + F1 and got into term. Logged in. No prblems. I ran an sudo apt-get update. Still not able to login to gui desktop. Went through google and someone told me to run "sudo apt-get install ubuntu-session" . Now my desktop logs in. But all icons are just blank (white in colour)and no network cards are detected. I got a lot of work to do but no working OS. 

The ifconfig -a does not list my netowork card.

 Please do help

---

### Post by grahammechanical on 2014-07-21
If you are getting to a desktop can you get to a terminal? Ctrl+Alt+T? If so then run

```
 unity --reset-icons
```

Two other useful commands

```
dconf reset -f /org/compiz/
```
```
setsid unity
```

The first resets Compiz the second resets Unity.

Regards.

---

