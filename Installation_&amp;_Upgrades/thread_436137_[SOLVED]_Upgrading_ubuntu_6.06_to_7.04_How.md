---
title: "[SOLVED] Upgrading ubuntu 6.06 to 7.04? How?"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by waggygee on 2007-05-07
I've been runing Ubuntu6.06 for a short time now (moved from WindowsXP) and was wondering to myself.... Is it possible to 'Upgrade'  my 6.06 to 7.04 without loosing the infomation on my harddisk and if it is possible. Would I need to download the entire 7.04 or could it some how 'supplement' the 6.06 already on the harddrive? (I would prefer the 2nd, as I have a download limit)

---

### Post by bulldog on 2007-05-07
If you want to upgrade,I don't think it's wise,if possible at all,to go straight to Feisty.
You have to upgrade to Edgy first and the do the upgrade to Feisty.

I would recommend to backup your data and do a fresh install of Feisty,it would be much quicker,and the chances you'll get errors are decreased considerable for that matter

---

### Post by rkillcrazy on 2007-05-07
> **waggygee said:**
> I've been runing Ubuntu6.06 for a short time now (moved from WindowsXP) and was wondering to myself.... Is it possible to 'Upgrade'  my 6.06 to 7.04 without loosing the infomation on my harddisk and if it is possible. Would I need to download the entire 7.04 or could it some how 'supplement' the 6.06 already on the harddrive? (I would prefer the 2nd, as I have a download limit)

I've only been using Ubuntu for about a year but I've upgraded a couple times.  I'm pretty sure you have to go from 6.06 to 6.10 to 7.04.

...Not saying you didn't but always try to search before posting...  This will help you get answers faster.
This is a "sticky" post in this forum: [https://help.ubuntu.com/community/EdgyUpgrades]("https://help.ubuntu.com/community/EdgyUpgrades")
"Googling" found this: [http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")

In short, you make sure you have internet access &  open a terminal and run:
```
gksu "update-manager -c"
```

It may prompt you for a password...

It should give you a little window, telling you there's an update to be had.  Get it.  After that's done and you go through a reboot, you should do it again to go from 6.10 to 7.04.

I've also used:
```
gksu "update-manager -c -d"
```

However, I don't recall what that does differently.  Furthermore, I've read that you should get any & all updates (for the current OS) before upgrading it.  I'm sure your 6.06 install has been kept up to date, right!? :) 



Give that a whirl and see what you get...

---

### Post by zvacet on 2007-05-08
Download Feisty Cd is fastest and easyest way in your situation.if you have separate home partition your data will be safe.if you don´t have it,make one.
[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Topsiho on 2007-05-08
You say you have a download limit. Then downloading a Feisty CD is far better then first upgrade to Edgy and after that to Feisty. When upgrading a lot of hundreds of MiB's are downloaded, being all or almost all of them the new packages for the new version.

That way you end up with downloading almost twice the amount of data doing the double upgrade. Which is not what you really want.

On top of that, doing a fresh install is almost always the wise thing to do. If you don't want to lose your own data and configurations, it is necessary to have your /home directory on a separate partition, which you do NOT format during the new install....

Good luck.

Topsiho

---

### Post by rkillcrazy on 2007-05-08
Yes, I agree with a lot of these other ideas regarding the use of the 7.04 disk and doing a clean install.  If it were several months after the release of 7.04, it may be better to do it the way I first outlined.  I say that because even after you do an install with the disk, you'll still have to hit the web for updates.  The nice thing about a web install is you will always get the latest packages and once you're done with the install, there will be little or no downloading of updates.  I know that if I plan on installing 6.10, I'll grab the [minmal CD]("https://help.ubuntu.com/community/Installation/MinimalCD").  It's a small download and it downloads the rest of the packages during the install.  However, like I said before, at least you won't have to get all the updates after the install.

Nonetheless, if you don't have many apps that you wish to hang onto, there's no real reason to do an upgrade.  I'm a network & systems admin for my company and we deal with WinXP & 2K3.  We don't do upgrades unless we feel as though we'll have trouble getting back random software that the client doesn't have CDs for.

05-08-07
0947 EDT

---

### Post by Topsiho on 2007-05-10
I think using the minimal CD is a great suggestion. I did not know it exists, and fortunately I now do :).

And the suggestion to only upgrade if this has become necessary is a sound one too, but for us hobbyists it is not so attractive :)

However, using the ninimal CD is not a good idea, just as the possibility to upgrade from the previous version, if you have more than one computer to install the new version on, I think. In that case you better download the complete CD-image and install from that. That way you download the files only once.

If the version is around for some time already (say several months) then indeed you'll have to update a lot files, that's quite true. That can be in the order of hundreds of MiB's....

Topsiho

---

### Post by originaluoc on 2007-05-10
Hello guys I have a similar problem. When I am trying to upgrade from 6.06 to 7.04 (I dont feel confortable enought to upgrade through clean install process to 7.10) the synaptic package manager appears the following messages:

The following problems were found on your system:

W: GPG error: [http://packages.kirya.net](http://packages.kirya.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EEFB43B2FBABB737
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://deb.opera.com](http://deb.opera.com) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: GPG error: [http://deb.opera.com](http://deb.opera.com) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791


Can anybody help me please?

---

### Post by Topsiho on 2007-05-10
> **originaluoc said:**
> Hello guys I have a similar problem. When I am trying to upgrade from 6.06 to 7.04 (I dont feel confortable enought to upgrade through clean install process to 7.10) the synaptic package manager appears the following messages:

The following problems were found on your system:

W: GPG error: [http://packages.kirya.net](http://packages.kirya.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY EEFB43B2FBABB737
W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: GPG error: [http://deb.opera.com](http://deb.opera.com) sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://deb.opera.com](http://deb.opera.com) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791
W: GPG error: [http://apt.cerkinfo.be](http://apt.cerkinfo.be) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A35A4E6EF00175CA
W: GPG error: [http://deb.opera.com](http://deb.opera.com) sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 033431536A423791


Can anybody help me please?

These are all "foreign" repositories the upgrade program does not know about and that were added by you (or someone else?). So I suggest you first remove them and then do the upgrade. If you have done this you can always add them again. If you want to, for adding repositories, and then with signatures that can not be verified is a risk you should not want to take :)

Topsiho

---

