---
title: "Problem trying to upgrade from dapper to edgy to feisty"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by runoverbobby on 2007-06-09
(Kubuntu with KDE)

Earlier today I upgraded from Dapper to Edgy by changing my sources.list and using apt-get (which I just found out was probably a bad idea). I wasn't watching the terminal the entire time, so I didn't keep track of any unusual activity or failed installations :(

The first thing I noticed after rebooting to start using Edgy was that I now have 6 booting options instead of 3, and #4 is the one that leads to an OS instead of a command line. Maybe this is normal after upgrading? -EDIT: just discovered that option #5 works as well.

The Adept interface didn't automatically install with the Edgy upgrade, so I ran another apt-get and then started to fetch updates. Eventually a message came up which said something to the effect of "a new version of Kubuntu is available! upgrade?" I decided to go with this GUI installation.

Less than 30 seconds in, this came up:

"Failed to fetch [http://www.beerorkid.com/automatix/apt/dists/kubuntu/main/binary-i386/Packages.gz](http://www.beerorkid.com/automatix/apt/dists/kubuntu/main/binary-i386/Packages.gz) 302 Found" It also said that the issue is "usually due to network problems"

I have no idea what that means, but I have a feeling that I'm running Edgy with some vital components missing... or something like that. Sooo if any awesome person out there has a hunch as to what's going on, your help would be appreciated ;)

---

### Post by brownknight on 2007-06-09
I have read that there are issues with what you plan to do. It is better to do a clean install to Feisty.

---

### Post by runoverbobby on 2007-06-09
> **brownknight said:**
> It is better to do a clean install to Feisty.

do you happen to have a Howto link handy?

Also I'm still really confused as to why I now have 5 different Kubuntu boots in GRUB.

---

### Post by arnieboy on 2007-06-10
> **runoverbobby said:**
> (Kubuntu with KDE)

Earlier today I upgraded from Dapper to Edgy by changing my sources.list and using apt-get (which I just found out was probably a bad idea). I wasn't watching the terminal the entire time, so I didn't keep track of any unusual activity or failed installations :(

The first thing I noticed after rebooting to start using Edgy was that I now have 6 booting options instead of 3, and #4 is the one that leads to an OS instead of a command line. Maybe this is normal after upgrading? -EDIT: just discovered that option #5 works as well.

The Adept interface didn't automatically install with the Edgy upgrade, so I ran another apt-get and then started to fetch updates. Eventually a message came up which said something to the effect of "a new version of Kubuntu is available! upgrade?" I decided to go with this GUI installation.

Less than 30 seconds in, this came up:

"Failed to fetch [http://www.beerorkid.com/automatix/apt/dists/kubuntu/main/binary-i386/Packages.gz](http://www.beerorkid.com/automatix/apt/dists/kubuntu/main/binary-i386/Packages.gz) 302 Found" It also said that the issue is "usually due to network problems"

I have no idea what that means, but I have a feeling that I'm running Edgy with some vital components missing... or something like that. Sooo if any awesome person out there has a hunch as to what's going on, your help would be appreciated ;)
you are using a one year old sources.list.. just paste the results of the following:
```
cat /etc/apt/sources.list
```

---

### Post by brownknight on 2007-06-10
> **runoverbobby said:**
> do you happen to have a Howto link handy?

What I mean is reinstall Ubuntu and install Ubuntu Feisty Fawn - rather than upgrading from Dapper to Edgy to Feisty. You can [download]("http://www.ubuntu.com/getubuntu/download") and burn the Feisty .iso then install it.

---

