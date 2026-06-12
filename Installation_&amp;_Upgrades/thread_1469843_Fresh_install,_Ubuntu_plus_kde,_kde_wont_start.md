---
title: "Fresh install, Ubuntu plus kde, kde wont start"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by swiggy349 on 2010-05-02
I installed the release version of Lucid a couple of days ago (clean install). I still cant decide whether I prefer gnome or kde so I installed the gnome version, then just

```
sudo apt-get install kubuntu-desktop
```

to install the kde desktop. I chose to keep the gnome login display manager, exactly the same as i did for karmic a few months ago. Then trying to log in to kde I get the message 

**Re: kstartupconfig4 does not exist or failed. The error code is  3. Check your install**.

then Im back to the login screen. Gnome works fine. This wouldnt be too big a problem, Im quite happy using gnome but none of the KDE apps work either, and Im a big fan of Kile in particular. If I try to start any KDE app i get a whole host of error messages, along the lines of

 p, li { white-space: pre-wrap; }  Configuration file "/home/steve/.kde/share/config/kilerc" not writable.
 Please contact your system administrator.


with various files being the subject of concern depending on what app it is, kdialog then crashes, a few more errors about files not being writeable, another kdialog crash then finally the app itself crashes. (All these crashes are reported by the kde crash handler).


As i said, fresh install and I dont have any unusual set-ups, just the one user account on a several week old laptop thats a pretty decent spec. I have read about problems with user permissions since i installed kde as root? these are all relating to older versions of ubuntu however.

---

### Post by laidbackwebsage on 2010-05-31
Bump

I'm having the same problem...

---

