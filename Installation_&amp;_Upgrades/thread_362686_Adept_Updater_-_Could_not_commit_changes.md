---
title: "Adept Updater - Could not commit changes"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by ndefontenay on 2007-02-15
Good morning Communitty,

I'm updating my Edgy release with new patches.
It will fetch the headers, then when I press "Apply" button, I get the following error message in a popup:

There was an error commiting changes. Possibly there was a problem downloading some packages or the commit would break packages.

Fair enough! But how do I fix it?

When I perform the following:

```
sudo apt-get update
sudo apt-get upgrade
```

The patches are downloaded and installed.
I've also tried:

```
sudo apt-get -f install
```

It did fix a few package dependencies, but none has fixed adept update.

I'm lost for words.

edit:
I think it would be good to give the list of packages remaining to update shown all the time (I keep having the update icon all the time in my system tray)

linux-headers-2.6.17-11                               not installed install
linux-headers-2.6.17-11-generic                   not installed install
linux-headers-generic                                  upgradable  upgrade
linux-image-2.6.17-11-generic                      not installed install
linux-image-generic                                     upgradable  upgrade
linux-restricted-modules-2.6.17-11-generic    not installed install
linux-restricted-modules-generic                   upgradable  upgrade

none of these are shown at all in the commad line apt-get update/upgrade

---

