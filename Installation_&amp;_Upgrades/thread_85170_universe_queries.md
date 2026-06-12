---
title: "universe queries"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by scoorocks on 2005-11-01
i do not have an internet connection at home. hence i download all the packages for my ubuntu from outside..i would like to know how can i download all the packages that a particular package depends on(e.g. Anjuta IDE)without clicking on all the individual ones and downloading them one by one i.e. can i download all the packages that a package depends on in one click from universe or some other place?

---

### Post by Kyral on 2005-11-02
You could try

```
sudo apt-get install <package> -d
```

---

### Post by scoorocks on 2005-11-02
the command works if i'm on ubuntu of course..but the place where i have access to the internet does not run ubuntu currently..so i download things directly from packages.ubuntu on the net..any suggestions to my original query?

---

### Post by SickTwist on 2005-11-02
I wish I could help but I don't know a solution. Perhaps somebody else will. It's a complicated circumstance.

Normally, Ubuntu takes care of all the dependencies automatically. Sometimes that means downloading them, sometimes it doesn't (because they are already installed). This dependency checking occurs recursively for each package, it's dependencies, the dependencies' dependencies, etc. So selecting one package could result in 1 being installed or maybe 20 being installed, depending on the current state of your system. It would be very tedious to look at a package and look at all its dependencies manually to figure out what you would need to download at the other computer.

If you have access to broadband and a DVD burner, you might be better off downloading the Ubuntu DVD. I think that contains all of the packages in the main repository. That way, you'd have access to the entire repository without being dependent on the Internet.

---

### Post by scoorocks on 2005-11-02
hey thanx a lot..i'll try doin that..but tell me does the DVD contain packages that are on ubiverse and do not come along with the i386 ubuntu cd?..coz i thought the dvd too contains the same packages as the cd..anyways i'll try doin that..thanks

---

### Post by SickTwist on 2005-11-02
The CD is a subset of the DVD. I *think* the DVD is the entire main repository (not universe, multiverse, or restricted) but I'm not sure--sorry. I've never downloaded it. All I know is that it has many more packages than just the CD.

More ideas: Canonical ships CD's for free. *Maybe* they ship (or will ship in the future) DVD's for free also. Keep an eye open for that. Also, you might be able to buy an Ubuntu DVD from somewhere on the Internet and have it shipped to you. Just make sure it is also Ubuntu 5.10 Breezy Badger if that is what you are running.

Good luck with it!

---

### Post by SickTwist on 2005-11-03
I just ran across this thread and thought that you would be interested:

[Ubuntu DVD images for Main/Universe/Multiverse]("http://www.ubuntuforums.org/showthread.php?t=78549")

---

