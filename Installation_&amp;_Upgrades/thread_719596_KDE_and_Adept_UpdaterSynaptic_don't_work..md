---
title: "KDE and Adept Updater/Synaptic don't work."
date: 2008-03-09
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2008-03-09
Hello everyone :)

I have an Ubuntu system installed with gnome desktop.
Today I installed KDE 3.5 and 4.0

As soon as I installed KDE 3.5 I saw that there were 36 updated packages available.

Clicked on the notification and it started launching adept updater.  After a bit of grinding nothing happened.

I tried to launch synaptic and it doesn't work either.

What is happening here?  Anyone had the same problem?  How did you solve it?

Please note that synaptic works just fine with my gnome desktop.

Thanks.

---

### Post by Peter09 on 2008-03-09
Worth looking into two things :-

1. Is it asking you for a password (it should do as it should need admin privileges)
2. Try doing it from the command line and see what happens.

---

### Post by Ifaistos on 2008-03-10
nope it doesn't ask me for a password in either one.

What do I type in the terminal to invoke them?

---

### Post by jcanini on 2008-03-10
I had a similar problem using KDE, when I clicked the update button it kept saying the updater was already in use.

I used 

```
sudo dpkg --configure -a
```

after reading thread 

[http://ubuntuforums.org/showthread.php?t=719228](http://ubuntuforums.org/showthread.php?t=719228)

This fixed the problem for me.


I took a bit of a punt doing that command as I dont really understand what it is doing, maybe someone here can explain.

---

### Post by Ifaistos on 2008-03-10
nope didn't work :(

---

