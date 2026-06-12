---
title: "Just moved from Sabayon. Lucid Lynx question...."
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by newbieone on 2010-02-15
Quick question.  A little more familiar with gentoo based os's than debian.

When Lucid is released at end of April is it possible to upgrade os through a terminal command or do you have to do complete live cd install?

Also, do you recommend waiting for final release or upgrade now to the alpha?  Then, with each release upgrade until final is out.

Thanks for the knowledge.

---

### Post by Paddy Landau on 2010-02-15
Upgrade will be possible.

Run the update manager (System > Administration > Update Manager). At the top, when the final version is released, you will find an option right at the top to allow you to upgrade.

I recommend that you not only wait for the final release, but also wait a month or so for the biggest bugs to be ironed out. In other words, I suggest that you wait until the end of May.

Before you upgrade, **back up all your data!** Although the upgrade will have gone through thorough testing, it always carries an increased risk of fatal failure. In that case, you'll have to do a clean install and then restore all your data.

---

### Post by Julita on 2010-02-15
Please be aware that there can be dependency, hardware compatibility, etc issues after upgrade: the upgraded system sometimes is less functional than the one "clean installed."
May I ask why you have switched to Ubuntu? Sabayon is a great distro...

---

### Post by bodhi.zazen on 2010-02-15
> **newbieone said:**
> Quick question.  A little more familiar with gentoo based os's than debian.

When Lucid is released at end of April is it possible to upgrade os through a terminal command or do you have to do complete live cd install?

Also, do you recommend waiting for final release or upgrade now to the alpha?  Then, with each release upgrade until final is out.

Thanks for the knowledge.

Yes you may upgrade. I have upgraded my Laptop 8.04 -> 8.10 -> 9.04 -> 9.10 without any major problems (some minor fixes).

---

### Post by howefield on 2010-02-15
> **newbieone said:**
> Also, do you recommend waiting for final release or upgrade now to the alpha?

Agree with all Paddy Landau said, but would add there's nothing to stop you creating an extra partition and testing Lucid or running it through a virtual machine.

Whether you jump in now or wait till release day is down to how you view the risks and whether or not the machine you are using is production critical.

For me, I'll do a triple boot about the first Beta, then a clean install on the day of release :)

---

### Post by rrashkin on 2010-02-15
> I recommend that you not only wait for the final release, but also wait a month or so for the biggest bugs to be ironed out. In other words, I suggest that you wait until the end of May.

Consider the "Categorical Imperative" (attributable, I think, to Kant).  What would happen if everyone did that?

---

### Post by howefield on 2010-02-15
> **rrashkin said:**
> Consider the "Categorical Imperative" (attributable, I think, to Kant).  What would happen if everyone did that?

If is a big word for one that has only two letters, (and you can attribute that to me :P) ... and it isn't going to happen. Ever. ;)

---

### Post by bwhite82 on 2010-02-15
Synaptic is the graphical method of upgrading but I have upgraded via 'apt-get' with each new release (including Lucid) with no problems:

> sudo apt-get dist-upgrade

---

### Post by bodhi.zazen on 2010-02-15
> **Soldierboy said:**
> Synaptic is the graphical method of upgrading but I have upgraded via 'apt-get' with each new release (including Lucid) with no problems:

Update Manger is the "official" advised or supported method of upgrading, even with server editions.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

And from 
[https://help.ubuntu.com/community/Upgrades#The%20Debian%20way%20of%20upgrading]("https://help.ubuntu.com/community/Upgrades#The%20Debian%20way%20of%20upgrading")

> Please be aware that this method is valid, yet not officially advised by  the Ubuntu developers. 
You may upgrade with apt-get , aptitude, or probably synaptic, but upgrading is more reliable with update manager.

---

