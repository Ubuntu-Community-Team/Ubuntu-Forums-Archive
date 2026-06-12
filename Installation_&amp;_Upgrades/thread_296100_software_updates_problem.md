---
title: "software updates problem"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by eastern_strider on 2006-11-09
Hi,

I recently upgraded to Edgy from Dapper and everything went smoothly. However, now when I click the **Software Updates** button (which has an icon like a shining star) a message pops up saying:

> "Not all updates can be installed"
Run a distribution upgrade, to install as many updates as possible.

This can be caused by an uncompleted upgrade, unofficial software packages or by running a development version.

There is a also a button **Distribution Upgrade** at the bottom of this window. Clicking that will probably harm my system since I already upgraded to the new distribution.

Any suggestions?

---

### Post by an.echte.trilingue on 2006-11-09
> **eastern_strider said:**
> Hi,
I recently upgraded to Edgy from Dapper

I hope you mean Dapper to Edgy.

Anyway, In My Humble Opinion, the ubuntu update manager isn't ready for prime time yet. 

I would advise you to open a terminal, and type:

```
sudo gedit /etc/apt/sources.list
```

and make sure that you are looking at edgy's repositories and not dapper's.  Then,
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Hope that helps you!

---

### Post by eastern_strider on 2006-11-09
Hi,

Yes I mean I upgraded to Edgy.

Given that I already upgraded, is it really meaningful to do:

```
sudo aptitude update
sudo aptitude dist-upgrade
```

I thought these commands are used to upgrade to the new distribution, which I already did.

---

### Post by an.echte.trilingue on 2006-11-09
It can't hurt.  It looks like maybe you have broken dependancies when trying to upgrade.  In short, you probably don4t have a clean upgrade.

This can happen for a couple reasons:

1. You have something installed that does not exist/had a name change in the new dist, and that depends on some things in the old dist.  Those dependancies may have other dependancies, ad nauseum.  So, apt (upate-manager is another apt front-end) leaves the old versions installed to be safe.  This always happens to me with wine, for example.  I always have to remove it before an upgrade and re-install it afterwords.

2.  You did not update properly before upgrading.  This is why you need to make sure that your sources.list is proper.  Also, if you had other repositories such as multiverse enabled in Dapper, you should have it enabled for edgy.


You want to use apt-get update/dist-upgrade because:

1.  It will fix broken dependancies, if there are any.

2.  It will tell you which packages are causing hang ups in the upgrade.

3.  It won't damage anything, regardless of success or failure.

---

### Post by eastern_strider on 2006-11-09
I've made your suggestions and I think it solved my problem.

Thank you very much for this!
Oguz

---

### Post by an.echte.trilingue on 2006-11-09
I'm happy I could help!

Take care,
-mat

---

### Post by Handssolow on 2006-11-12
> **an.echte.trilingue said:**
> I hope you mean Dapper to Edgy.

Anyway, In My Humble Opinion, the ubuntu update manager isn't ready for prime time yet. 

I would advise you to open a terminal, and type:

```
sudo gedit /etc/apt/sources.list
```

and make sure that you are looking at edgy's repositories and not dapper's.  Then,
```
sudo aptitude update
sudo aptitude dist-upgrade
```

Hope that helps you!

Thanks. For the fast few days Update Manager was showing that there was an update ready for an ATI driver but I wasn't able to install it. Today the list had grown to 9 updates that I wasn't able to install. Following the advice, I used the terminal to install all 9 updates and the orange star has disappeared.

Before my success I did see an error screen reporting that I had duplicate entries of repositories, something I was more used to with Dapper. However, what should I do if I see this again. Where do I look for duplicate repositories entries?

Perhaps Update Manager isn't ready for prime time.

---

### Post by zetetic on 2006-11-13
Quote:
Where do I look for duplicate repositories entries?

Code:
sudo gedit /etc/apt/sources.list

Look there and delete any duplicated entries

Cheers
zetetic

---

