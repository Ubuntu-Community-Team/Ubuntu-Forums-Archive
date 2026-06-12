---
title: "planning on installing 14.04.1, questions about gaming"
date: 2015-02-05
forum: Installation &amp; Upgrades
---

### Post by vex2 on 2015-02-05
I downloaded the Ubuntu 14.04.1 ISO and am planning on installing it on an 8 core AMD FX8150 with 16GB RAM and a 2TB SATAIII hard drive. I hear there is this thing called "Play on Linux" which apparently allows me to play Windows games on Linux.  Does this count for Steam? (most of my games are on there) And what about World of Warcraft?  If I can get WoW and my Steam games working without huge amounts of technical BS, I'd never use Windows again.

Please help! Thanks! :)

---

### Post by TheFu on 2015-02-05
Welcome to the forums.

Any expectations that programs from a different OS will "just work" under Linux is flawed and will lead to disappointment.
Play-on-Linux is a front end to WINE. They do try to make things work, but don't expect miracles.

Steam games will work, if they are Linux. Check which are.

Linux is an OS that at the heart is made for computer people. Canonical is trying hard to hide that, and in many ways they do, until something unexpected happens. Then you'll need to open a shell, type some commands, and be a nerd.

So ... I've been runing different Linux distros since 1993 and I do almost everything on Linux these days ... except 3 things. Those require Windows. Attempts to get those programs working under WINE were successful until 2011 ... now they don't work and Windows is required - ok those programs "sorta work", but it isn't worth the hassle to me to bother.

If you want to game, you'll still likely need Windows to have an acceptable experience.

---

### Post by Mark Phelps on 2015-02-05
>  If I can get WoW and my Steam games working without huge amounts of technical BS, I'd never use Windows again.

If Windows gaming is a key reason for moving the Linux, then you've made a bad decision.  

Windows gaming is a lot more than just getting the game to run in Wine.  There are also concerns about overheating -- which are well-handled in Windows but not so well in Linux.  There are problems with Hybrid Graphics -- which again, are well-handled in Windows but not in Linux.  And there are concerns about video drivers -- which again, tend to be better handled in Windows.

POL is a front-end that simplifies installing stuff, but it does not contribute to actually running the games.

---

### Post by vex2 on 2015-02-05
Okay, thank you both for the feedback.  I've decided not to switch. I'm currently using Windows 7 64 Pro.  I've used Linux before and loved it, but my main PC use is gaming so it looks like Windows is going to stay on my system. :)

---

### Post by TheFu on 2015-02-05
> **vex2 said:**
> Okay, thank you both for the feedback.  I've decided not to switch. I'm currently using Windows 7 64 Pro.  I've used Linux before and loved it, but my main PC use is gaming so it looks like Windows is going to stay on my system. :)

You realize you don't have to choose 1 OS or the other. You can have both.
a) dual boot
b) virtualization

Linux doesn't hog disk storage, so with 20G of storage you can do almost anything except load huge games or develop java applications.  Plus, you can access NTFS data from Linux, so any media (video/movies/tv/music) can be available from Linux without duplicating the files.  For programs, those really need to be installed on a Unix file system which has a more central part in the OS than in Windows.  File and directory permissions are the core of Unix system security by design.

Virtualization is probably easier and less risky, but it will have some performance trade-offs if you like graphical "cheese". Gaming in a virtual machine doesn't work well for high-end graphics dependent games. OTOH, chess will work great in a VM. ;)

Many people use Linux for everything except gaming - they like the reduced virus attack vectors, greater security, and how user accounts are well compartmentalized.  Linux is extremely flexible, which is great or terrible, depending on your viewpoint. It is common for any task to have 20 different ways to accomplish it. This can be confusing to noobs.  Plus there are many things easily accomplished on Unix that are very difficult or impossible with GUI-centric OSes.  We can automate almost anything, for example. Unix was designed as a programming environment for end-users - and it shows.  It really is amazing what a 1-10 line script can accomplish on a Unix system.

---

### Post by vex2 on 2015-02-05
Almost all my PC is for is gaming and internet.  It's just not practical to install a dual boot and I have no real need for Linux, I just like it. lol

---

### Post by TheFu on 2015-02-05
> **vex2 said:**
> Almost all my PC is for is gaming and internet.  It's just not practical to install a dual boot and I have no real need for Linux, I just like it. lol

IMHO, internet alone is enough reason NOT to use Windows. It is a dangerous world out there and having a smaller attack surface, like Linux does, would be smart.

---

### Post by vex2 on 2015-02-05
> **TheFu said:**
> IMHO, internet alone is enough reason NOT to use Windows. It is a dangerous world out there and having a smaller attack surface, like Linux does, would be smart.
I do have a very good AV, and a nice malware scanner, I don't click weird links in e-mail, and I don't download anything from untrusted sources, so I'm not too worried.  But unless I know for certain that every game I have will run "perfectly" without hours of tweaking, I'm not going to put up the effort to switch....

---

### Post by TheFu on 2015-02-05
AV is only 50% effective on Windows.
There isn't really any AV needed for Linux (yet).

Malware isn't part of the linux ecosystem either. 

Pretty much all the non-game software is free, cryptographically signed by a person, so there isn't any hiding WHO did something bad. 

Software management is trivial for Ubuntu - not just for the OS, but for all software on the system loaded through a package manager. These are the main reasons I run Linux. I was tired of hassling with software updates all the time and being worried about getting hacked.

Gaming isn't the reason to run Linux, but everything else you do on a computer is.  You don't need to "switch" - use each OS for what it is good at doing, that's all.  OTOH, I can understand why learning something new would scare you.  When I switched my 80 yr old Mom to Linux, she was afraid too ... for about 10 minutes. Then she saw that most things she did were exactly the same, just without the added concerns. She got hacked before the switch. It was bad and I don't think it was her fault. She didn't do anything that any other reasonable person wouldn't also do.

---

### Post by mastablasta on 2015-02-06
> **vex2 said:**
> I do have a very good AV, and a nice malware scanner, I don't click weird links in e-mail, and I don't download anything from untrusted sources, so I'm not too worried.  But unless I know for certain that every game I have will run "perfectly" without hours of tweaking, I'm not going to put up the effort to switch....

Steam I increasing the number of their games that work in Linux. especially since Valve created SteamOS. but not all Windows games work on Linux or work well. in fact majority don't. which is why you are better of with windows. I guess I would say the same if someone wanted to run Linux compiled programs on windows. they would be disappointed with windows.

use what works best. you can also run Linux in virtualbox (e.g. only for internet). I do that on my old windows PC.

---

### Post by vex2 on 2015-02-06
> **mastablasta said:**
> Steam I increasing the number of their games that work in Linux. especially since Valve created SteamOS. but not all Windows games work on Linux or work well. in fact majority don't. which is why you are better of with windows. I guess I would say the same if someone wanted to run Linux compiled programs on windows. they would be disappointed with windows.

use what works best. you can also run Linux in virtualbox (e.g. only for internet). I do that on my old windows PC.
Windows it is then it seems. :D

---

