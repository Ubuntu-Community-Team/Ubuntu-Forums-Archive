---
title: "Apps won't get acces to JAVA RE"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by afk46 on 2010-04-22
Hello,

I just installed a game, TripleA, that is supposed to run great on Ubuntu using JAVA. I extracted the game to the recommended folder but when I try to start it in the the terminal, I get the following message.

sudo /home/"username"/.Games/TripleA/triplea_unix.sh
Exception in thread "main" java.lang.NoClassDefFoundError: games/strategy/engine/framework/GameRunner
Caused by: java.lang.ClassNotFoundException: games.strategy.engine.framework.GameRunner
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:319)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:264)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:332)
Could not find the main class: games.strategy.engine.framework.GameRunner. Program will exit.

I have JRE already installed via  Install and Remove Applications utility. Is there something else I should do? Installing JRE manually seemed a bit troublesome... Is it "safe", i.e. will the other apps that use java still work properly? 

Thanks for your help!

Jim

---

### Post by kbielefe on 2010-04-26
It's finding java just fine.  The problem is finding the libraries for the game, because you are using sudo and the script is expecting the first thing you type on the line to be the program itself.  Generally a bad idea to run as root unless you absolutely must anyway.  Typing the following *exactly *should work if you don't have some bizarre permissions issue:

```

cd /home/"username"/.Games/TripleA/
./triplea_unix.sh

```

---

