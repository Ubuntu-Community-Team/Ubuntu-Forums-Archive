---
title: "Hardy to Jaunty and KPackageKit"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by yedidyah on 2009-04-14
I know it is taboo to jump from hardy to Jaunty without going through Intrepid but I could NOT get Intrepid to do anything.

But now I got this problem with KPackageKit:

"The package list needs to be rebuilt.
This should have been done by the backend automatically."


I also need to figure out what programs are now not going to work.

whatever advice can be given is appreciated

---

### Post by tommcd on 2009-04-14
> **yedidyah said:**
> I know it is taboo to jump from hardy to Jaunty without going through Intrepid but I could NOT get Intrepid to do anything.

That is your problem right there. You are trying to do something that is not recommended.

Your options are:
1. You can dist-upgrade to Intrepid, and then dist-upgrade to Jaunty when Jaunty goes to stable in 9-10 days or so.
2. Do a clean install of Jaunty beta right now, or when Jaunty goes to stable (I would recommend the clean install option).

---

### Post by yedidyah on 2009-04-14
I could not find a link for Jaunty to burn to a disk only upgrades.

I understand it is not recommended but:

1) Intrepid _freezes_ at Aperature beyond 4 GB at start up (it cannot just be ignored as so many have suggested). No my friend I will not be ruining my system a third time on a path through Intrepid. First time shame on Intrepid, second time shame on me, third time back to windows.

2) If it is so taboo why does the Ubuntu web site actually have a link so you can jump from Hardy to Jaunty? I guess I understood that Ubunutu developers understood that there are some systems that WILL NOT work with Intrepid that is why they have the option for the Hardy to Jaunty jump.

[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04)

So back to my original question what needs to be done to correct the problem?

Problem with KPackageKit:

"The package list needs to be rebuilt.
This should have been done by the backend automatically."

---

### Post by tommcd on 2009-04-14
> **yedidyah said:**
> I could not find a link for Jaunty to burn to a disk only upgrades.
You can find many links for downloading Ubuntu 9.04 beta here:
[http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
And for Kubuntu 9.04 beta:
[http://releases.ubuntu.com/releases/kubuntu/9.04/](http://releases.ubuntu.com/releases/kubuntu/9.04/)
> **yedidyah said:**
> 
2) If it is so taboo why does the Ubuntu web site actually have a link so you can jump from Hardy to Jaunty? 
[https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/JauntyUpgrades/Kubuntu/8.04)

Well then, that is a very good question indeed! Elsewhere in the Ubuntu wiki you will find links that say:
> You can only directly upgrade to Ubuntu 9.04 Beta from Ubuntu 8.10 (see UpgradeNotes). 
See this:
[https://help.ubuntu.com/community/JauntyUpgrades](https://help.ubuntu.com/community/JauntyUpgrades)
So it seems there is a bit of a contradiction there. 
Personally, I always do clean installs; and that is what I would recommend rather than trying to fix a dist-upgrade from Hardy to Jaunty. A clean install is the easiest and most fail safe method for upgrading. If you have /home on a separate partition your data is safe.
> **yedidyah said:**
> 
So back to my original question what needs to be done to correct the problem?
Problem with KPackageKit:
"The package list needs to be rebuilt.
This should have been done by the backend automatically."
Some googleing has discovered that Kubuntu includes a new package manager called KPackageKit.
[http://packages.ubuntu.com/jaunty/kpackagekit](http://packages.ubuntu.com/jaunty/kpackagekit)
 See if you can open it and see if it gives you the option of rebuilding the package list. If you do not have KPackageKit, or it is broken, then try:
```
sudo apt-get install --reinstall kpackagekit
```

---

### Post by yedidyah on 2009-04-14
Thank you for the jaunty iso. I may go ahead and do that.

I really appreciate your help here is what happened when I typed the command into terminal:

E: Type 'sudo' is not known on line 56 in source list /etc/apt/sources.list
E: The list of sources could not be read.

Again thank you.

---

