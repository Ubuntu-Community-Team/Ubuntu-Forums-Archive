---
title: "Ubuntu can't be upgraded after unplugged during upgrading"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by bilgee0629 on 2012-04-07
today, I, accidentally unplugged my Ubuntu laptop and damaged update manager. Now there is a sign at top panel saying that
```
An error occurred, please run Package Manager from the right click menu or apt-get in a terminal to see what is wrong. The error message was: 'Error': BrokenCount > 0'. This usually means that your installed packages have unmet dependencies.
```I really need to get it working without reinstalling ubuntu.

PS: I'm using ubuntu 12.04 beta2 :tongue:

---

### Post by bilgee0629 on 2012-04-07
When I tried to upgrade like ```
 sudo apt-get -f upgrade 
```it gives an error that ```
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 e2fsprogs : PreDepends: e2fslibs (= 1.42-1ubuntu1) but 1.42-1ubuntu2 is installed
E: Unmet dependencies. Try using -f. 
```So I tried ```
 sudo apt-get -f install e2fsprogs 
``` . After that all upgrading started working properly.

---

