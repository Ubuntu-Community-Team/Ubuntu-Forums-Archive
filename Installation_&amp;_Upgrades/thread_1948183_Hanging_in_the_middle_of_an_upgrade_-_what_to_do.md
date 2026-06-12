---
title: "Hanging in the middle of an upgrade - what to do?"
date: 2012-03-27
forum: Installation &amp; Upgrades
---

### Post by AussieGuy on 2012-03-27
I am just upgrading my system (11.10) to use the newest packages, which weren't installed from the CDROM.

However, after some minutes the progress bar is stopped at 47%, in the middle of "Preparing to configure kdegraphics-strigi-analyzer".  And the Muon window has got stuck like this.

Should I abort the upgrade and restart it, or will this cause a conflict between new and older packages?

Thanks,
-A.

---

### Post by mastablasta on 2012-03-28
abort upgrade (actually this is update not system upgrade). it could be that something is wrong with the mirror server you are using to do the updates. you could try changing the mirror and then doing it again.
 
another otpion is to then run konsole (temrinal) and then copy &paste these commands to it:
 
```
 
sudo apt-get update
sudo apt-get upgrade

```
 
it will ask for password, you won't see anything being typed.
 
this will do the same update in terminal (just in case Muon is the one that is causing the crash/hanging)

---

### Post by AussieGuy on 2012-03-28
It seems to be a bug in Muon; there are a few other reports I've discovered since about Muon freezing.  I've done my upgrading/updating since using aptitude, which seems a far more robust front-end to apt-get.

Thanks for your reply!

-A.

---

