---
title: "Upgrading from 8.04 to 10.04..."
date: 2010-03-03
forum: Installation &amp; Upgrades
---

### Post by riph72 on 2010-03-03
Hello all,

Seeing as we're not far away from my first major upgrade of Ubuntu, I'm wondering what is the recommended way of doing this, i.e. clean install, or upgrade of my current system (assuming the latter is even an option)?

Regards,
Richard.

---

### Post by yogesh.girikumar on 2010-03-03
Hi,


       It depends. If you want to retain your old systems configuration and look & feel, go for an upgrade. If you simply want a faster installation and want a hassle free setup go for a fresh install.


       A clean install is faster and hassle free but all your settings like your wallpaper and themes will be gone. It will also remove any additional software that you installed, like vlc player, any third party software etc. You'll have to install additional packages later on.


       An upgrade is a bit slower and leaves behind some obsolete files. But all your settings will be preserved. This also takes longer since each and every package that you installed manually needs to be upgraded too.


       Either way, have a backup of all your important files.


       See: [http://www.online-blogger.net/2009/11/09/ubuntu-karmic-koala-clean-install-vs-upgrade/](http://www.online-blogger.net/2009/11/09/ubuntu-karmic-koala-clean-install-vs-upgrade/)
       

HTH,

---

### Post by mkvnmtr on 2010-03-03
Many users ues a seperate home partition and do a reinstall of the root partition and leave the home untouched. This will save your settings but you have to reinstall your apps.Although I have had upgrades work several times I like the reinstall method best.
As stated a back of your home is important.

---

### Post by slakkie on 2010-03-03
> **yogesh.girikumar said:**
> 
       See: [http://www.online-blogger.net/2009/11/09/ubuntu-karmic-koala-clean-install-vs-upgrade/](http://www.online-blogger.net/2009/11/09/ubuntu-karmic-koala-clean-install-vs-upgrade/)


In response to the blog posting, I have a different view: [http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/](http://blog.opperschaap.net/2010/01/06/maintaining-ubuntu-upgrade-vs-reinstall/)

Ext4 might be the only reason to freshly install 10.04, otherwise 8.04 to 10.04 should be painless.

---

### Post by tommcd on 2010-03-03
I always do clean installs myself. This is clearly the most fail safe and trouble free method of getting the latest (and hopefully greatest) versions of Ubuntu. There is certainly nothing wrong with trying the dist-upgrade method though. This is obviously the more convenient way to go. If it works ok and there are no problems post upgrade then all is well.
However, I have seen a great many people in these forums spend many days or even many weeks struggling to solve problems with failed upgrades though. IMO these people would be much better off just doing a clean install and be done with it. To spend several weeks trying to fix a multitude of ill defined problems that so many people seem to have with dist-upgrades is counterproductive at best. Just breakdown and do a clean install already!
I believe the reason many people have problems with dist-upgrades is because they have so many third party packages and repos added to their system. This includes the ppa repos. Trying to drag all that third party stuff along for the ride when doing a dist-upgrade seems to be a recipe for disaster.
Note that it is recommended to remove third party software when doing dist-upgrades:
[https://help.ubuntu.com/community/CleanUpgrade](https://help.ubuntu.com/community/CleanUpgrade)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
How many people remove third party software before upgrading? Not many I would think.

It was possible to upgrade 6.06 LTS to 8.04 LTS. It should also be possible to do a dist-upgrade from 8.04 LTS to 10.04 LTS if anyone wants to go that route.

---

### Post by sam.reader on 2010-03-03
If you want a glitch free OS installed in your PC I strongly urge you to make a clean install
The reason I am recommending you to go fro a fresh install is I had some serious problems when I did change from 8.10 to 9.10 and lost a whole lot of data.
SO make a good decision.

---

### Post by riph72 on 2010-03-03
Hi everyone,

Thanks for the feedback.  I think I'll go for the clean install.  Seeing as I prefer the LTS versions, so won't be doing it more than every two years anyway, it's worth the extra hassle of starting from scratch.  A clean install every two years isn't too big a deal to me.

I've never trusted Windows with the upgrade route, so I might as well stick to this thinking for Linux too!

Regards,
Richard.

---

### Post by tommcd on 2010-03-03
> **riph72 said:**
> 
Thanks for the feedback.  I think I'll go for the clean install.  Seeing as I prefer the LTS versions, so won't be doing it more than every two years anyway, it's worth the extra hassle of starting from scratch.
Good choice.
Understand that doing a clean install of Ubuntu becomes easier the more you do it. It is a skill that you learn from practice, just like anything else in life. Many people seem to needlessly fear doing a clean install. If you managed to do it once, you can do it a thousand times. The first time will always be the steepest end of the learning curve.

---

