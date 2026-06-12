---
title: "I'm really doubtfull about how to upgrade to feisty."
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by jdarias on 2007-04-24
Hello.
One day a teacher told us very wisely: "If ain't broken, don't try to fix it!"
Well, my issue is: i have read a lot of sad and terror stories about upgrading from edgy to feisty, slow bootups, no boot at all, dual boot machines with windows screwed up (yet even more :D), netorking and hardware not being recognized, and the list goes and goes.
The thing is, my edgy installation works just fine!! so i'm very doubtful about jumping into dangerous waters here. The only issues i have are with some usb devices not being detected without removing the ehci_hcd module, but since it is a known bug in ubuntu and i have a dual boot pc i don't mind about it.
Would feisty have this fixed? What's the best way to upgrade? with a CD or downloading all the stuff with update-manager? Is it worthy?

---

### Post by Big Ed on 2007-04-24
I've just finished upgrading a desktop and a server to Feisty.  There were a few minor problems with both machines, but nothing too serious.

I did the network upgrade since that was recommended by the Ubuntu team.  I think that I would have been better off using a cd, since I'd downloaded them anyway and the Ubuntu servers were being hammered this weekend.  And they are likely still being hammered.  (I had problems connecting to download the packages.  No problem downloading the cd iso's though, must be on different servers.)

Yes, there have been lots of problem reports on the forum, but remember how many people are doing upgrades right now.  Most of them are having no problems at all.  It's only the people who run into difficulty that end up posting here.

I'm pretty pleased with Feisty on the desktop.  It's faster and cleaner.  On the server, well, no gui, so less of a difference.  But if Edgy is working for you, then you don't _need_ to upgrade.  If you decide to upgrade anyway, either use a cd or wait a few weeks until the Ubuntu package servers have had a chance to deal with the majority of the upgraders.

HTH,
Ed

---

### Post by jdarias on 2007-04-24
I'm getting it via bittorrent.
So i mount the iso, wich will be recognized as a new version  and do $gksu "update-manager -c" right? 
When it's all done, what happens with the software i've installed from the repositories in edgy after the installation?
Do these have to be updated as well? i mean for example azureus or tremulous, not the software that comes with the distro.

---

### Post by Big Ed on 2007-04-24
> **jdarias said:**
> I'm getting it via bittorrent.
So i mount the iso, wich will be recognized as a new version  and do $gksu "update-manager -c" right? 
When it's all done, what happens with the software i've installed from the repositories in edgy after the installation?
Do these have to be updated as well? i mean for example azureus or tremulous, not the software that comes with the distro.

Well, I meant that you should burn a cd.  I've never tried doing a dist-upgrade with a mounted iso file.  But you could always try it and see if it works.  Let us know.

Your other installed software will still be updated as new versions become available.  However, if Feisty has changed library versions that your software depends upon, then it will be upgraded at the same time.  That's one of the advantages of a dist-upgrade over a fresh install.

Ed

---

### Post by jdarias on 2007-04-24
> Well, I meant that you should burn a cd. I've never tried doing a dist-upgrade with a mounted iso file. But you could always try it and see if it works. Let us know.I'll better won't take the risk and burn the CD instead of mounting. What if i do an install later and the real CD's cannot be used? It happens to me that when i need to do something with the CDs during an install i can only use only one of the two drives i have. The other one never works. It'll be best for me to stick to that drive instead of a mounting point

---

### Post by jdarias on 2007-04-25
Bump to question: on the ubuntu homepage, they mention a upgrade method wich is done with the alternate CD. But i'm almost done downloading the normal CD! Can i follow that method with it?

---

### Post by Sef on 2007-04-26
> Bump to question: on the ubuntu homepage, they mention a upgrade method wich is done with the alternate CD. But i'm almost done downloading the normal CD! Can i follow that method with it?

The alternate cd is a text-based install.  The desktop cd is a gui install.   You would have to download the alternate cd to install that way.

---

### Post by jdarias on 2007-04-26
But can i upgrade with a desktop CD???:confused: :confused: :confused:

---

### Post by Sef on 2007-04-26
> But can i upgrade with a desktop CD???

The desktop CD installs Feisty on your computer.  If you only want to upgrade, go to System > Administration > Update Manager.  

**Back up** your files no matter what you install Feisty.  The clean install (with the desktop cd) has less problems than the upgrade.   Both can work well, and both can have problems.

---

### Post by jdarias on 2007-04-26
Can i upgrade with a desktop CD? just yes or no please. Sorry if i sound rude.
I cannot upgrade with update manager, i have a slow connection.

---

### Post by Big Ed on 2007-04-26
> **jdarias said:**
> Can i upgrade with a desktop CD? just yes or no please. Sorry if i sound rude.
I cannot upgrade with update manager, i have a slow connection.

Yes or no???   Hmm, maybe.  Give it a try.  Edit /etc/apt/sources.list to comment out everything but the cd and make sure the cd line reads feisty instead of edgy.  Then run

sudo apt-get update && sudo apt-get dist-upgrade

If that fails, try

sudo apt-get install upgrade-manager-core && sudo do-release-upgrade

I'm really not too sure that you will be successful with the install cd.  The upgrade web pages are pretty specific about using the alternate cd.  [https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

Then again, I would think that the same files will be available on both.

Ed

---

