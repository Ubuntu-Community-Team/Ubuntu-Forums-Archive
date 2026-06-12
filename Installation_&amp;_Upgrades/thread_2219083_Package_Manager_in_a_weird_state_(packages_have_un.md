---
title: "Package Manager in a weird state (packages have unmet dependencies)"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by Cosmologicon on 2014-04-22
Ubuntu's only allowing 1024x768 resolution on my 1920x1080 monitor, but I don't think that's the core problem.

There's a red circle icon in my menu bar that says:> An error occurred, please run Package Manager from the right-click menu or apt-get in a terminal to see what is wrong. The error message was: ' Error: BrokenCount > 0'. This usually means that your installed packages have unmet dependencies

[Here's the output from apt-get install]("http://pastebin.com/LnPAZ6Ms")
[Here's the output from apt-get install -f]("http://pastebin.com/GEMCed1z")
[Here's the output from apt-get autoremove]("http://pastebin.com/xYvkEe1Y")
[Here's the output from apt-get autoremove -f]("http://pastebin.com/mJmx0G26")

Any suggestions for the next step? I have a package called panda3d which has caused me a lot of headaches, but I don't have any reason to think this is related.

---

### Post by ian-weisser on 2014-04-23
The problem seems clearly explained in the system error messages you posted:
> dpkg: error processing /var/cache/apt/archives/libsdl2-2.0-0_2.0.3ppa3precise1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libSDL2-2.0.so.0', which is also in package libsdl2 2.0.1ppa1precise1


Two different PPA packages are trying to install the same file.
They are incompatible - you must uninstall one PPA package and delete that PPA's repository.

---

### Post by Cosmologicon on 2014-04-23
Thanks! Followup dumb question, how do I know which PPA?

I commented out what I suspected was the offending line from my sources.list file ([new version here]("http://pastebin.com/HWWMTGug")) and removed what I suspected was the offending package (panda3d-runtime), but that was just a wild guess, and I get the same error.

---

### Post by ian-weisser on 2014-04-23
Disabling the PPA isn't enough; the offending package is already on your system and marked for install.

> **ian-weisser said:**
> you must uninstall one PPA package **and** delete that PPA's repository.

---

### Post by Cosmologicon on 2014-04-23
I'm sorry, I don't understand. Which of those two steps are you saying I didn't do? And, since I'm obviously misunderstanding it, can you rephrase the missing step?

---

### Post by ian-weisser on 2014-04-24
I'm sorrier, I just re-read your post; you did indeed say you did both steps and still get the error.

dpkg doesn't know which PPA you got the offending package from. It only knows which two packages conflict:
libsdl2-2.0-0_2.0.3ppa3precise1_i386
libsdl2 2.0.1ppa1precise1  (That space may be a typo in your original post - package names don't have spaces)

You can try using apt-cache to trace the dependency chains to figure out which PPA application you installed that depends upon libsdl2
```
apt-cache rdepends libsdl2-2.0-0
```
You may get nowhere doing this detective work, or you may discover the application that caused the problem.
If you discover the application, uninstall it. And autoremove all dependencies.

If it were me, I would instead focus on getting your system back to a working state - your unresolved package conflict means you're not getting updates and security fixes.

1) Disable *all* PPAs. All of them. 

2) Tell the system to stop trying to install the packages that cannot install due to the conflict: icedtea-6-jre-cacao icedtea-6-jre-jamvm libsdl2-2.0-0
```
sudo dpkg --set-selections
icedtea-6-jre-cacao deinstall
 icedtea-6-jre-jamvm deinstall
libsdl2-2.0-0 deinstall
```

3) See if updates work without the conflict.
```
sudo apt-get update && sudo apt-get upgrade
```

4) If that doesn't fix your problem, then you might need to uninstall the existing version of libsdl2...and the packages that depend upon it:
```
sudo apt-get uninstall libsdl2
```

---

### Post by Cosmologicon on 2014-04-24
Awesome, that did it! I started by removing the icedtea packages (step 2) and that worked for me. Thanks so much!

---

