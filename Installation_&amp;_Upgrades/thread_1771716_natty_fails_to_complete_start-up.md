---
title: "natty fails to complete start-up"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by blackmail on 2011-05-30
Ok people, so i have installed compiz 9 and it didn't quite work for me, then i have reverted to compiz 8 and things where fine, but after a while my desktop started slowing down for no apparent reason, so i decided to install the nVIDIA drivers from the manufacturer's site, good, i typed in:
```
sudo /etc/init.d/gdm stop
```
and then i installed the drivers with the sh command, stuff went right, but i could not start my the X server, so i restarted the computer with the:
```
sudo shutdown -r now
```
command, and when it all started, before the login screen, the system was loading the modules, but it always stops at the:
```
Checking battery status
```
and only ctrl+alt+del works for restart...

Any suggestions please?

---

### Post by blackmail on 2011-06-17
Ok in case someone will experience this problem ,i have the solution to it. 
Boot your linux in recovery mode, and then in low graphincs mode.
You install the most un-recent drivers you can find for your system, in case those are installed you can install a more recent one, mainly the idea is to switch drivers. Ok after that the desktop has to be tinkered with, you should go ahead and install Gnome 3 and also you can slam up KDE from the developer's site :)

If you complete all these with success you will get back your system running. After one boot or so you can just switch back to your natty desktop by purging the Gnome3 install

There are quite some tutorials on how to do this kind of stuff...

Have fun

---

### Post by blackmail on 2011-06-17
Yeah i posted it i solved it :D
Kinda like in the Eclipse and the Cplusplus forums :))

---

