---
title: "Lucid Lynx Updates Causing Screen Errors"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bluberri on 2010-04-09
Today I ran the Update Manager to check for Lucid updates.  

Installed the updates, rebooted and am now having issues with seeing complete windows whether I open in Gnome or Netbook Edition - I cannot see the  top of any window (e.g. minimise, maximise, close window icons etc).

Also the mouse pointer icon has switched to being an X rather than and arrow.

Also, in Netbook the screeen flashes/flickers constantly.  Running in  Gnome appears ok wth the exception of the windows issue above.

Hardware: Asus 1005ha Netbook.

Update: when I attempt to run set windows properties through System|Preferences|Windows I receive the message:

"Cannot start the prefernces application for your window manager.

Window manager "unknown has not registered a configuration tool."

---

### Post by lovinglinux on 2010-04-09
[Lucid Lynx Testing and Discussion](http://ubuntuforums.org/forumdisplay.php?f=377)

---

### Post by Mykk on 2010-04-09
> **Bluberri said:**
> Today I ran the Update Manager to check for Lucid updates.  

Installed the updates, rebooted and am now having issues with seeing complete windows whether I open in Gnome or Netbook Edition - I cannot see the  top of any window (e.g. minimise, maximise, close window icons etc).

Also the mouse pointer icon has switched to being an X rather than and arrow.

Also, in Netbook the screeen flashes/flickers constantly.  Running in  Gnome appears ok wth the exception of the windows issue above.

Hardware: Asus 1005ha Netbook.

Update: when I attempt to run set windows properties through System|Preferences|Windows I receive the message:

"Cannot start the prefernces application for your window manager.

Window manager "unknown has not registered a configuration tool."

Try reinstalling your ubuntu-desktop

Sudo apt-get reinstall ubunutu-desktop

---

### Post by philinux on 2010-04-09
Thread moved.

---

### Post by psyke83 on 2010-04-09
> **Bluberri said:**
> Today I ran the Update Manager to check for Lucid updates.  

Installed the updates, rebooted and am now having issues with seeing complete windows whether I open in Gnome or Netbook Edition - I cannot see the  top of any window (e.g. minimise, maximise, close window icons etc).

Also the mouse pointer icon has switched to being an X rather than and arrow.

Also, in Netbook the screeen flashes/flickers constantly.  Running in  Gnome appears ok wth the exception of the windows issue above.

Hardware: Asus 1005ha Netbook.

Update: when I attempt to run set windows properties through System|Preferences|Windows I receive the message:

"Cannot start the prefernces application for your window manager.

Window manager "unknown has not registered a configuration tool."

It seems likely that you ran a Partial Upgrade which removed either metacity or compiz.

The [sticky thread on Partial Upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") is essential reading if you wish to test the development release. Also keep in mind that [another thread]("http://ubuntuforums.org/showthread.php?t=1450282") already discusses this specific partial upgrade issue (which would not need to exist if the sticky thread was read).

---

### Post by Bluberri on 2010-04-09
> **psyke83 said:**
> It seems likely that you ran a Partial Upgrade which removed either metacity or compiz.

The [sticky thread on Partial Upgrades]("http://ubuntuforums.org/showthread.php?t=1343434") is essential reading if you wish to test the development release. Also keep in mind that [another thread]("http://ubuntuforums.org/showthread.php?t=1450282") already discusses this specific partial upgrade issue (which would not need to exist if the sticky thread was read).

Reinstalled Compiz.  Back to normal now, thanks.  

I have read the thread on partial upgrades and take on board what is said - will be paying more attention to any future updates.

---

