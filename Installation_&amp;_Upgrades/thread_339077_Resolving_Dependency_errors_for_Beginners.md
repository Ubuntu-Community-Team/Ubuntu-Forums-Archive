---
title: "Resolving Dependency errors for Beginners"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by Tdonohue on 2007-01-15
How can a newbie learn to resolve dependency errors?  Any suggestions/fixes that I search for seem to be specific to a certain error that someone is requesting help for.

3 days into my Ubuntu experience, I had a complete working system, except for wi-fi. programs and codecs downloaded flawlessly through synaptic.  Then I tried to install VMware and got one of those "...subprocess post-installation script returned error...".  Now nothing will install or uninstall.  This is a problem many people have had, but I just can't seem to find how to fix it.  All the posted threads seems to have a different way to do it.

Before I do a complete reinstallation, I would like to learn how to fix it.  Obviously, chances are high that I will run into this problem in the future, and I can't answer it by reinstalling everytime. 

Any help regarding my question are to helping resolve my error would be appreciated!

---

### Post by aysiu on 2007-01-15
I don't know if this applies to your particular situation, but dependency errors usually stem from conflicting repositories.

I would [get a fresh set of repositories](http://www.psychocats.net/ubuntu/sources) and then ```
sudo aptitude update
sudo aptitude install vmware-player
```

---

### Post by teaker1s on 2007-01-15
also in synaptic preferences you can set recommended files as dependencies-this stops all the dependency issues provided the required dependencies are in repositories.

just be careful if you uninstall anything synaptic doesn't remove something you need

---

