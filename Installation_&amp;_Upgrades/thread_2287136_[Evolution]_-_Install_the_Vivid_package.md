---
title: "[Evolution] - Install the Vivid package"
date: 2015-07-17
forum: Installation &amp; Upgrades
---

### Post by Will_Moonen on 2015-07-17
Over the past few weeks I have tried numerous times to upgrade Evolution as part of 14.04-LTS / Unity.
There are several sites reporting that adding a certain Gnome3 repository, do an apt-get update and apt-get install will update Evolution to whatever latest release there is. However, for me, that doesn't do the trick.

I then tried Ubuntu-Gnome 14.04-LTS with the idea that since Evolution has a tied integration with Gnome, it might be easier.
But that didn't work either. I even tried some of the more experimental Gnome packages.

Until now, every attempt ends in a message like "You are running the latest version of Evolution".

 Meantime, Vivid is released. This seems to come with version 3.12 (as opposed to 3.10.4) – the launchpad package is called: 3.12.11-0ubuntu3.
Is there a way to upgrade with this version without doing a complete install of 15.04?

 Reason for this update is the performance improvements for EWS.
In addition, I'm (sort of) hoping that this update will also fix the I/O error messages and the connectivity issues with IMAP from Google..

---

### Post by Vladlenin5000 on 2015-07-17
Adding Gnome3 PPA might upgrade the Gnome specific packages (ex: Evolution) to the latest available in that PPA. However, if you really did it before as you just posted, then you did it wrong.
After adding that PPA, and as usual for all PPAs, you should use the following sequence:

```
sudo apt-get update
sudo apt-get **upgrade**
```


Now, considering that special PPA, it's always recommended to add:
```
sudo apt-get dist-upgrade
```



No need to do further installations. If you already have Evolution installed it'll be upgraded to the newest version in the PPA.

---

### Post by Will_Moonen on 2015-07-18
Thank you for the feedback.

> **Vladlenin5000 said:**
> Adding Gnome3 PPA might upgrade the Gnome specific packages (ex: Evolution) to the latest available in that PPA. However, if you really did it before as you just posted, then you did it wrong.

I'm not aware of doing anything wrong. So I would certainly appreciate your help here.

The Gnome 3 I'm talking about is added with:
```
sudo add-apt-repository ppa:fta/gnome3
``` 

I then tried the following sequence:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Nothing happened here.

I then tried:
```
sudo apt-get update
sudo apt-get install evolution
sudo apt-get upgrade evolution
sudo apt-get dist-upgrade evolution
```

All 3 commands with evolution in it came back with:
> evolution is already the newest version

I then tried the same on the Ubuntu/Gnome system (i.e. no Unity installed).
The result is exactly the same.

At this point and time, all Ubuntu desktop systems are still running Evolution 3.10.4.
Which is the version that comes with 14.04-LTS.

So yes, I'm definitely overlooking something here. I just don't know what it is... :-)
Any idea/suggestion?

---

### Post by Vladlenin5000 on 2015-07-18
The version at the repository is 3.16: [https://launchpad.net/~fta/+archive/ubuntu/gnome3](https://launchpad.net/~fta/+archive/ubuntu/gnome3)

---

### Post by Will_Moonen on 2015-07-18
> **Vladlenin5000 said:**
> The version at the repository is 3.16: [https://launchpad.net/~fta/+archive/ubuntu/gnome3](https://launchpad.net/~fta/+archive/ubuntu/gnome3)

Yes, correct. This seems to be the latest, stable version.

But I'm willing to settle for 3.12.11 if that makes things easier.
However, according to some reviewers, there are some issues when using with 14.04-LTS.

---

