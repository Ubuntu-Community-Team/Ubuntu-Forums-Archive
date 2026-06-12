---
title: "Update via remote"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by iamgeniusrnti on 2011-11-25
A while back I installed KUbuntu 10.04 LTS on my wife's computer.  I am away (military) and I do maintenance on it from time to time via SSH and when necessary, XVNC.  The nice thing about this OS is you could install, walk away and not think about it for years.  It takes care of itself and doesn't complain very much.

This morning I was checking up on it and just out of curiosity I unamed it and saw it was still running 10.04 LTS.  Having not bothered with her computer much, I neglected to stay on top of the Ubuntu news.  So I jump into the forums and read that the newer releases have a new desktop?  WOuldn't it be nice to surprise the wife with a new look?

So I ran update-manager -d (after having to apt-get it) and it sees 12.04 as the next LTS upgrade.  My question is, if I push that button that is teasing me and pull the trigger, what are the odds the computer will self install and smoothly reboot without any hitches?  And is there a way I can command line it and avoid having the XVNC running?  Something like sudo apt-get install update && apt-get something something something?

Thanks!

---

### Post by iamgeniusrnti on 2011-12-10
Bump.  I'm sorry but I'd still like to know if I could do this remotely via SSH. Oddly, the 12.04 LTS prompt went away and it thinks it's running the latest and greatest (of course, it is an LTS)  Anyway, I changed the update manager prompt from LTS to normal and I was just going to upgrade from 10.04 LTS to 10.10 and then take it to 11.  So I went here: [https://help.ubuntu.com/community/MaverickUpgrades#Network_Upgrade_for_Kubuntu_Desktops_.28Recommended.29](https://help.ubuntu.com/community/MaverickUpgrades#Network_Upgrade_for_Kubuntu_Desktops_.28Recommended.29)

But when I go in via SSH and do-release-upgrade, I get a warning about the possibility of death and apocalypse if I continue via SSH.  Is this a common procedure with little risk or should I head its warning and wait till I get home? 

Thank you for your valuable time.

---

### Post by azmyth on 2011-12-10
I'd wait until you got home. If you ran it in a ssh shell your connection would have to stay open for a long time or you could try running in the background. If I was to try it, I'd login to ssh and then use the screen command incase your connection got dropped.

[http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/](http://www.rackaid.com/resources/linux-screen-tutorial-and-how-to/)

---

