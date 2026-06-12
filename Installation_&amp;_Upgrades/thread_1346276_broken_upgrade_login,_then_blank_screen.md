---
title: "broken upgrade: login, then blank screen"
date: 2009-12-04
forum: Installation &amp; Upgrades
---

### Post by sboisen on 2009-12-04
I'm a ubuntu newbie, so please be patient if i don't get all the details quite right. I had a Ubuntu 8.04 installation which seemed to be working correctly. I used the online installer to upgrade to 8.10, which (for the brief time i used it) also seemed okay. Then i continued upgrading to 9.04. I'm afraid i don't completely recall the upgrade steps: it was whatever was offered on the upper right of the menu bar. 

Apparently something went amiss during this last installation. So now when i boot up, i get the login prompt, enter my username and password, and then the screen goes blank and never brings up the window manager. 

From the login screen, the options button (lower left) lets me Select Session. From there, i can select a Failsafe Terminal, and that starts up okay. So now i've got a shell prompt. What can i do to try to get the system back to a working state at this point, or to diagnose the problem further??

---

### Post by sboisen on 2009-12-04
A few more details in case they're helpful:
[LIST]
[*]if i wasn't clear, i'm not booting from a CD or ISO, i downloaded the installer/upgrader (and i believe i have a working internet connection)
[*]lsb_release -a returns Ubuntu 9.04
[*]uname -r return 2.6.28-16-generic
[/LIST]

(i don't actually know what these mean, i'm just trying to provide information)

---

### Post by MelDJ on 2009-12-04
at the shell type gnome-desktop and see what happens

---

### Post by sboisen on 2009-12-04
File "/usr/lib/command-not-found", line 8, <module>
    import CommandNotFound
ImportError: No module named CommandNotFound

---

### Post by sboisen on 2009-12-05
I also tried [this suggestion]("http://www.ubuntu.com/getubuntu/releasenotes/904#python%20ImportError%20with%20systems%20upgraded%20before%20Ubuntu%209.04%20release%20candidate") for fixing Python import errors, but that didn't produce anything worthwhile.

Are there any other options i can try other than starting all over again with 8.04?

---

### Post by NormanFLinux on 2009-12-05
Do a fresh install. If its broken its more time-consuming to fix it than to start over.

Good luck.

---

### Post by sboisen on 2009-12-05
That's disappointing, but i really appreciate the pragmatic suggestion: thanks!

---

