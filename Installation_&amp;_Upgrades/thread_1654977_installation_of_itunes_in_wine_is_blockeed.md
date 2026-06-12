---
title: "installation of itunes in wine is blockeed"
date: 2010-12-29
forum: Installation &amp; Upgrades
---

### Post by Cozze on 2010-12-29
I've installed wine and downloaded the itunes .exe file. When I try to install it using wine program loader I get following error message

Blocked: wine start/unix

The file '/home/cozze/.wine/dosdevices/c:/Program Files/iTunesSetup.exe' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

Anyone knows how I can solve this?

Tx, Cozze

---

### Post by prshah on 2010-12-29
When you launch programs using the GUI, the default program (called cautious-launcher) checks if the file has the executable bit set. If the exec-bit is not set, it will not allow to "run" the file. In this case, open your file manager of choice, navigate to the file, and then right click it and choose properties. In the "Permissions" tab, check to allow the file to be executed as a program.

Alternately (for ex, if the executable is on an CD/DVD), open a terminal and launch the program directly. In this case, open a terminal (Applications-Accessories-Terminal) and give the commands```
cd ~/.wine/dosdevices/c:/Program\ Files/
wine iTunesSetup.exe
```

---

### Post by MARP1961 on 2010-12-29
This should work and enable you to install iTunes. Please let us know how well iTunes works for you. I'm sure no one has been able to get it fully functioning in Ubuntu yet. Have you tried Rythmbox or Banshee? Both will work with iPods and Ubuntu One has a music store for online purchases.

---

### Post by Mark Phelps on 2010-12-29
BEFORE installing anything in Wine, you should first go to the WineHQ application compatibility page to see how well the app performs and to read the results other folks have found when testing it.

The page for iTunes is below:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")

As you can see, the results for recent versions of iTunes were either Garbage (won't work at all!) or Bronze (barely works).

---

### Post by Cozze on 2010-12-30
yes well, I managed to install it but it doesn't work like it should ... now I want to uninstall it and that doesn't work neither haha ... well keeps me going ... thanks for your advice lads.

---

