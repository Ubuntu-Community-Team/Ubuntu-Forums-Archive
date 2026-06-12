---
title: "update from 6.06 to 6.10RC"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by manfredell on 2006-10-20
sorry folks,


I'm doing this for the 1st time:



how do I update an Ubuntu 6.06 installation to the new 6.10RC?


I have internet connection and have downloaded the 6.10 CD's (standrd and alternate).


Thx in advance!!!

---

### Post by DC@DR on 2006-10-20
Hi,

If you want to have a clean install, then backup your important data, then start installing from the 6.10 CD you've downloaded. Just install it as in 6.06 you did before.

If you wanna upgrade from your current 6.06 to 6.10, hit Alt-F2 or any terminal and then issue this command :
```
gksu "update-manager -c -d"
```
It'll ask you if you'd like to upgrade to new distribution, i.e 6.10, just click yes and then there you go, on the way to Edgy :)

---

### Post by bswilson on 2006-10-20
You want to upgrade to a Release Candidate, but you didn't read **any** of the documentation, did you?

[http://www.ubuntu.com/news/EdgyReleaseCandidate](http://www.ubuntu.com/news/EdgyReleaseCandidate)

You sure you want to upgrade?

---

### Post by manfredell on 2006-10-20
Well I did read the comments. And yes I want to update. Why shouldn't I?

---

### Post by K.Mandla on 2006-10-20
I suppose bswilson's point was that, even though it's a release candidate, there's still the potential for an error to occur, or for something to become broken.

So long as you've backed up your data and you're willing to take the chance, it's not a problem.

I know there are a lot of people who use it already -- I've been using it for weeks now without too many issues. And once it receives the RC designation, it's probably safe to give it a shot. The final is only a week away, and the fixes that come in at this point should be minor.

I say go for it. ;)

---

### Post by manfredell on 2006-10-20
That was exactly my thought. I wouldn't install a beta but it's a RC (yes still a beta but...)

---

### Post by kondor on 2006-10-20
[http://www.ubuntu.com/news/EdgyReleaseCandidate]("http://www.ubuntu.com/news/EdgyReleaseCandidate")

You can peruse the above note. Also, it might be prudent to know how to reconfig Xserver, etc. in case something gets bashed. Also, new kernels will be installed so you may have to manually load some modules.

I updated 2 unbuntus to 6.10RC, one a whiz, the other a bit of work.

Good luck!

---

### Post by manfredell on 2006-10-21
Well I actually am NO Linux wiz...

Xserver reconfig? definitely not
manually load modules: don't know how.

So in nutshell: got for the RC or wait for the final? Or is the risk the same on both?

---

### Post by manfredell on 2006-10-22
Did the update: no problem.

---

### Post by bpalyshka on 2006-10-22
just updated xubuntu to 6.10


thanks for the info.  I love ubuntu and plan to use it religiously:mrgreen:

---

### Post by Unicast on 2006-10-22
Just upgraded here too - loving edgy already! :D

The only problem I've had is with some of the python stuff not updating through Adept Manager - sudo apt-get update / sudo apt-get dist-upgrade didn't work either!

However doing a few "sudo aptitude dist-upgrade" solved this issue.

Thanks to m94mni in [this thread.](http://www.ubuntuforums.org/showthread.php?t=237966)

---

