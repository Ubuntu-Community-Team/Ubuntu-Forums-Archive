---
title: "Serious problem! System broken due to conflict!!"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by Biffy on 2005-10-17
Im kinda panicking now. :(

I was running hoary on my computer. Today i wanted to upgrade to Breezy. So i changed my reps to breezy and started the dist upgrade.

It was about a 1 gigabyte of packages that was downloaded. It started to upgrade my system and things where just fine. But about halfway through i get a error. Im sorry, but i just clicked on "OK". I rebooted my computer, and now X wont even start. I am not running GDM you see, i am running in runlevel 3 so Ubuntu starts without X, and if i want to start X, i simply type: startx

Ok, so startx gives me:

```
-bash: startx: command not found
```

So in text mode i first become root, then i type: apt-get update and that works fine. Then i typ: apt-get dist-upgrade

It seems i have a lot of broken packages due to dependency problems. They are many and not even by pressing shift +page up/page down i can see all of them. It will take like several hours to type down everything by hand. But i can see that there is a lot of KDE-packages, but also libarts, libdbus,libgdk,libgnome, lsb and so on. On the bottom of the screen, it says:

```
E: Unmet dependencies. Try using -f
```

What am i suppose to do now? I really dont want to reinstall Ubuntu.

---

### Post by Biffy on 2005-10-17
And BTW:

All thoose packages that cant be installed, after them, the term "but it is not installed" is displayed.

For example:

```
sim: Depends: kdelibs4c2 (4:3.4.1) But it is not installed
```

So it seems there are no problems with different versions.

---

### Post by Quirky on 2005-10-17
You can use a pipe and less i.e. "apt-get dist-upgrade | less" to see the packages, use up/down and q to quit. Or ">" the output to a file and open it in vim. But it's stories like these that scare the heck out of me :???: and the reaon why I'm still running Hoary... Remember to not rush into a drastic solution, walk away if neeed be and think it over (easier said than done at times, I know). Hopefull the problem is going to be an easy-to-fix broken package or two, sort those and the rest should work.

---

### Post by Biffy on 2005-10-17
Hey Quirky!

I fixed the problem. A guy on irc (apokrythos or something) said that the package "ubuntu-desktop" have to be installed before you dist-upgrade. This guy helped me a lot so a big THANK YOU to him.

Then, i installed some packages through aptitude so that i could install ubuntu-desktop. Then i installed it, and that kinda solved all the other dependencies. Then i just rebooted and everything was fine.

**So to all of you out there! Install ubuntu-desktop before upgrading to breezy!**

---

### Post by fractalvibes on 2005-10-17
What does Ubuntu-desktop get you?

When I did a find/replace of all instances of "hoary" with "breezy" (in the sources.list) and then the dist-upgrade - it seems that there may not be a breezy equivalent to all the hoary repositories?

fv

---

