---
title: "Update notifier for systray icon is gone"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by robertsaron on 2007-08-26
I used to have the little triangle or square tih a ! in it, the update notifier was down by the clock. It does not pop up anymore. There lots of instructions on the forums, but they were kind of vague.

How can I get it back? I am using Feisty fawn 7.04 Kubuntu

---

### Post by mocoloco on 2007-08-27
It's because there aren't any more updates for you right now :)  Next time more updates are needed it will show up again.

---

### Post by robertsaron on 2007-08-31
Not true, cause when i run sudo apt-get there are updates for it that it pulls down.

---

### Post by mocoloco on 2007-08-31
I see.  In that case open KSysGuard (or from a terminal do ps -A) and see if "adept_notifier" is in the list or running processes.  If not, hit Alt+F2 and type in adept_notifier, and see if your little icon shows up after a few minutes.

---

### Post by mocoloco on 2007-08-31
Maybe this will help.
[http://ubuntuforums.org/showthread.php?p=1158726]("http://ubuntuforums.org/showthread.php?p=1158726")

---

### Post by robertsaron on 2007-09-06
thanks guys for the help. I will try this and get back to you.

---

