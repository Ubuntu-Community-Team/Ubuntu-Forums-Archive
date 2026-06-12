---
title: "Intermediate Upgrade - 12.0.4.5LTS to 12.10"
date: 2015-06-21
forum: Installation &amp; Upgrades
---

### Post by jeff113 on 2015-06-21
Hello,

I attempted an upgrade from 12.0.4LTS to 14.0.4LTS and something went terribly wrong. The machine would not boot and would just sit at a blinking cursor. I did have a backup and restored the machine to it's original state. I would really like to get this machine up to 14.0.4 so I can run the latest version of Zimbra. I thought I might try some intermediate upgrades like 12.0.4 to 12.10 then 12.10 to 13.10, etc. but I'm not sure how I can do that from the command line.

Thanks in advance,

Jeff

---

### Post by howefield on 2015-06-21
Given that you have the good sense to have a backup, why not try a clean install with 14.04 - or 14.04.2 as it is now ?

---

### Post by Bashing-om on 2015-06-21
jeff113; Hello;

Though it can be done, it will be a long hard road following your method as 12.10, 13.04 and 13.10 are all End_Of_Life and have no direct support.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The better options are the lesser LTS-LTS (12.04 - 14.04) upgrade OR a clean fresh install of 14.04 .

Decide what you want to do, and we take this matter back up.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jeff113 on 2015-06-21
> **Bashing-om said:**
> jeff113; Hello;

Though it can be done, it will be a long hard road following your method as 12.10, 13.04 and 13.10 are all End_Of_Life and have no direct support.
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

The better options are the lesser LTS-LTS (12.04 - 14.04) upgrade OR a clean fresh install of 14.04 .

Decide what you want to do, and we take this matter back up.[INDENT][INDENT]it's 'buntu[INDENT][INDENT][INDENT]you can have it your way
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I see what you are saying about the EOL editions. LTS to LTS definitely looks like the way to go. I'm due to get new servers in a couple of months and will definitely have to do a clean install and move Zimbra then so I guess I will just stick it out a couple more months :-)

---

### Post by jeff113 on 2015-06-21
> **howefield said:**
> Given that you have the good sense to have a backup, why not try a clean install with 14.04 - or 14.04.2 as it is now ? With a clean install I'd have to move Zimbra over and I'm not quite ready to do that.

---

### Post by Bucky Ball on 2015-06-21
As mentioned, you can upgrade directly from 12.04 LTS to 14.04 LTS. You can leapfrog the interims with LTS to LTS upgrades. Open Software and Updates (or it might be Software Sources in 12.04) and in the updates tab, set it to notify you of LTS releases ONLY. Update and open Software Updater. You should see something across the top of that screen saying 14.04 LTS is now available (it might be on the Software and Sources screen, I haven't done this in some time). 

Update your machine the regular way and switch off any PPAs you have installed manually prior to doing the upgrade to 14.04 LTS. Good luck.

---

### Post by jeff113 on 2015-06-22
> **Bucky Ball said:**
> As mentioned, you can upgrade directly from 12.04 LTS to 14.04 LTS. You can leapfrog the interims with LTS to LTS upgrades. Open Software and Updates (or it might be Software Sources in 12.04) and in the updates tab, set it to notify you of LTS releases ONLY. Update and open Software Updater. You should see something across the top of that screen saying 14.04 LTS is now available (it might be on the Software and Sources screen, I haven't done this in some time). 

Update your machine the regular way and switch off any PPAs you have installed manually prior to doing the upgrade to 14.04 LTS. Good luck.Hello, what exactly is a PPA and how would I disable then re-enable the after the upgrade ?

Thanks

---

### Post by Bucky Ball on 2015-06-22
Software Settings> Other Software. Is there any repositories enabled in that tab other than 'Canonical Partners'? If there is, you probably manually installed them, but if you're asking what a PPA is, you probably haven't installed any. :)

---

### Post by jeff113 on 2015-06-22
> **Bucky Ball said:**
> Software Settings> Other Software. Is there any repositories enabled in that tab other than 'Canonical Partners'? If there is, you probably manually installed them, but if you're asking what a PPA is, you probably haven't installed any. :) Hi Bucky, remember I'm working strictly from the command line and I inherited this server from the previous admin so he might have added PPA

---

### Post by Bucky Ball on 2015-06-22
Oh, thanks for reminding me. In that case:

```
nano /etc/apt/sources.list
```

Have a look in there at what repos are installed. Anything that ends in '/ubuntu/archive/' and then mentions the name of your release is from the Canonical repos. When you see this part down the page:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner
```

... then if there's anything after that, you'll want to get rid of it, BUT ... if the previous owner diddled with this file by hand, they may have put things all over rather than in any order, or at least one that makes sense now, so check first. To edit the file and make the changes permanent, control+x then the command:

```
sudo nano /etc/apt/sources.list
```

You might want to make a backup of that file before you mess with it:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

---

### Post by jeff113 on 2015-06-22
> **Bucky Ball said:**
> Oh, thanks for reminding me. In that case:

```
nano /etc/apt/sources.list
```

Have a look in there at what repos are installed. Anything that ends in '/ubuntu/archive/' and then mentions the name of your release is from the Canonical repos. When you see this part down the page:

```
## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner
```

... then if there's anything after that, you'll want to get rid of it, BUT ... if the previous owner diddled with this file by hand, they may have put things all over rather than in any order, or at least one that makes sense now. To edit the file and make the changes permanent, control+x then the command:

```
sudo nano /etc/apt/sources.list
```

You might want to make a backup of that file before you mess with it:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

**Here's what my source.list looks like:**

```
# deb cdrom:[Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)]/ lucid main restricted

# deb cdrom:[Ubuntu-Server 10.04.3 LTS _Lucid Lynx_ - Release amd64 (20110719.2)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
```

---

### Post by Bucky Ball on 2015-06-22
Code tags for terminal output, please. See last link in my sig.

All of this:

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
```

... can go. Any repo with a # at the beginning of the line is not active. Everything else looks ok. All Precise repos. Looks like this was a 10.04 LTS release (thus the Lucid repos switched off) that has had a net upgrade to 12.04 LTS (Precise)! There you go. :)

You can leave it as it is until 2017, upgrade to 14.04 LTS til 2019, or clean install 14.04 LTS or an interim.

---

### Post by jeff113 on 2015-06-22
> **Bucky Ball said:**
> Code tags for terminal output, please. See last link in my sig.

All of this:

```
## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
```

... can go. Any repo with a # at the beginning of the line is not active. Everything else looks ok. All Precise repos. Looks like this was a 10.04 LTS release (thus the Lucid repos switched off) that has had a net upgrade to 12.04 LTS (Precise)! There you go. :)

Thanks Bucky. I guess the only thing left to do is give the 12.0.4.5LTS to 14.0.4.2LTS another try. I do have a backup so.......... BOMBS AWAY :-). I'll give it a go this weekend

THANK YOU

---

### Post by Bucky Ball on 2015-06-22
Cheers and good luck with it. ;)

---

### Post by jeff113 on 2015-06-22
> **Bucky Ball said:**
> Cheers and good luck with it. ;)


Thanks Bucky!  Appreciate all your help.

---

