---
title: "upgrade to intrepid from gutsy"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by talktorishav on 2008-08-31
Hello guys how can I update my gutsy to intrepid without updating to hardy.

When I do update manager -d it only gives option for hardy,

---

### Post by Partyboi2 on 2008-08-31
You need to upgrade one release at a time unless you are upgrading from dapper to hardy.
Intrepid is still in development so I would suggest not using it if you are wanting a stable system.

---

### Post by talktorishav on 2008-08-31
Wow So this means I have to waste 700 MB volume of data bandwidth and 1 hour while updagrding to hardy which I dont want. I just want to test Intrepid.

I use hardy all day on my laptop.
My home computer has Gutsy. Which I seldomely use. So its not updated to hardy yet. Now I decided to test Intrepid on it and I have to  upgrade to hardy first!!!

---

### Post by talktorishav on 2008-09-03
bump

---

### Post by irrdev on 2008-09-03
Your question has been answered. You **cannot** simply upgrade from Gutsy to Intrepid, but must follow the logical upgrade path from Gutsy->Hardy->Intrepid. Therefore, *please do not bump this thread again*. Really, downloading 1400mb is no big deal - any decent internet connection nowadays can easily handle this. If you are willing to simply install Intrepid with a clean install (using only 700mb), you can always download the daily live-CD builds from [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by Zeroangel on 2008-09-03
Would it be feasable, however, for him to back up his /home folder -- and then install a intrepid straight over it? He would always be able to restore his settings later on.

Failing that, one could always back up everything that is of importance (all documents, and none or few dot folders) and then start out with a fresh install.

IMO, it is more important anyways to start out fresh, you might lose a few hours to configuring and installing but at least you'll have a well oiled machine. (i've had programs go unstable or start to slow down due to upgrades not taking well with their old settings)

---

### Post by irrdev on 2008-09-03
> **Zeroangel said:**
> Would it be feasable, however, for him to back up his /home folder -- and then install a intrepid straight over it? He would always be able to restore his settings later on.

Failing that, one could always back up everything that is of importance (all documents, and none or few dot folders) and then start out with a fresh install.

IMO, it is more important anyways to start out fresh, you might lose a few hours to configuring and installing but at least you'll have a well oiled machine. (i've had programs go unstable or start to slow down due to upgrades not taking well with their old settings)
That's what I do. When I go to install Intrepid, I plan to actually create a separate partition for my home folder, thus saving me the extra effort of transferring my personal files over to my external hard drive in the future. However, either method works fine. 

I recently added an idea to Ubuntu Brainstorm, extending the Live-CD installer to include an "Upgrade" option which would automatically keep the home directory intact. You can vote on the idea here -> [http://brainstorm.ubuntu.com/idea/12651/](http://brainstorm.ubuntu.com/idea/12651/)

---

### Post by brundlelinux on 2008-10-31
If you just want to try Intrepid and not have to do the whole upgrade twice thing....

Download and burn the Intrepid ISO and then dual boot your system, leaving your Gutsy untouched.  When you're done tinkering with Intrepid, just run Gparted and nix it and give all your partition space back to Gutsy.  Don't forget to fix your GRUB when converting back.

---

