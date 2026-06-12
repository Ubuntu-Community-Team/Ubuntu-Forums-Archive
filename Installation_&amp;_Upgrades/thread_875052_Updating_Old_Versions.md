---
title: "Updating Old Versions"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Carleas on 2008-07-30
Hi,

I inherited a poorly maintained Ubuntu server a little while ago, and I'm trying to get it up to speed.  It's currently running Edgy, and I'm trying to get it upgraded.  I have a few questions:

-First, how important is it that Edgy is up to date before I go to Feisty (the documentation recommends not going all the way at once, so I was going to do a few stages of upgrade, Edgy->Feisty->Gutsy->Hardy)?
-Second, if it is important, what do I put in sources.list to direct to the old versions.  I know the upgrade information has been moved, and I'm very green on this, so I don't know how to translate that knowledge into a proper sources.list file.
-Third, just to be sure, each version I want to upgrade to will require a new list in sources.list, right?  Is there a place where recommended sources.list files are available for each version?

Thanks, as I said, I'm green and looking to grow :)

---

### Post by wpshooter on 2008-07-30
My recommendation would be that you get rid of what you've got and install Hardy (or even better Gutsy) from scratch.

I'm sure there might be some disagreement/other opinions.

But IMO, if you go the update route, you are probably going to have a LOT of problems to solve along the way !!!

But good luck.

---

### Post by zvacet on 2008-07-30
If you can back up your data and settings then **wpshooter´s** advice is better way to do.But if you want to do upgrades you have to upgrade Edgy first.To do that you havwe to make some changes in your source list.

```
sudo nano /etc/apt/sources.list
```

and change **archive.ubuntu.com **to **old-releases.ubuntu.com ** Save file and close it.

```
sudo apt-get update && sudo apt-get upgrade
```

After that 

```
sudo apt-get install update-manager-core
```

```
sudo do-release-upgrade
```

Check if you have two sources list and if that is the case delete one with edgy repos amd leave one with Feisty ones.Also check that you have this line in source list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

To see how upgrade from Feisty to Gutsy read [this.]("https://help.ubuntu.com/community/GutsyUpgrades#Network upgrade for Ubuntu servers (recommended)") From Gutsy to Hardy [this.]("https://help.ubuntu.com/community/HardyUpgrades#Network upgrade for Ubuntu desktops (recommended)") When you come to Hardy check that you have [this lines]("http://doc.ubuntu.com/ubuntu/serverguide/C/extra-repositories.html") in your source list.Good luck!

---

### Post by Carleas on 2008-07-30
I think I may have to go with wpshooter's recommendation.  The thing was, I have a fuzzy understanding of how to run apt-get, and essentially no understanding of how to do a fresh install and get my website running as normal again.

zvacet, I updated my repositories and ran 'sudo apt-get update && sudo apt-get upgrade', but I can't run 'sudo apt-get install update-manager-core'.  I get this error:
```
The following packages have unmet dependencies:
  update-manager-core: 
Depends: python but it is not going to be installed
Depends: python-central (>= 0.5.6ubuntu2) but it is not going to be installed                   
Depends: python-apt (>= 0.6.16.2) but it is not going to be installed                       
Depends: lsb-release but it is not going to be installed                      
Depends: python-gnupginterface but it is not going to be installed
E: Broken packages
```

I also have a ton of packages kept back during apt-get upgrade:
```
The following packages have been kept back:
  dovecot-common libblkid1 libcairo2 libgd2-xpm libgnutls13 libxslt1.1
  mysql-client-5.0 mysql-server-5.0 openoffice.org-core
  openoffice.org-l10n-en-gb openoffice.org-l10n-en-za util-linux

```

Is there a way to get around this?  If not, how do I run a fresh install?  [-o<

---

### Post by zvacet on 2008-07-31
```
sudo apt-get -f install
```

---

### Post by Carleas on 2008-07-31
Nothing.  It seems to come down to libreadlin5, which needs to be >=5.2, but which I can only get 5.1-7build1.  I've uninstalled and reinstalled it, and 5.2 isn't available.  

This is my sources.list file.  I think I'm missing some repository, because mysql doesn't exist in these repositories either:
```
# Ubuntu supported packages
# GPG key: 437D05B5
deb http://security.debian.org/ stable/updates main
deb http://old-releases.ubuntu.com/ubuntu edgy main restricted
deb http://old-releases.ubuntu.com/ubuntu edgy-updates main restricted
deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://old-releases.ubuntu.com/ubuntu edgy universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://old-releases.ubuntu.com/ubuntu edgy-security universe multiverse
```

---

