---
title: "I screwed up my package manager..."
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by lunaticHIGH on 2007-05-20
Newbie here: 
Went to download Auotmatix here: 
[http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html](http://www.ubuntugeek.com/install-popular-applications-in-ubuntu-feisty-fawn-using-automatix2.html)

it gave me error messages in the terminal. 

Now when i tried to go to Synaptic package manager, i get this: 

E: Type '"deb' is not known on line 37 in source list /etc/apt/source.list
E; The list of sources could not be read. 
Go to the repository dialog to correct the problem. 
E: _cache->open() failed, please report. 

I followed the instructions in the link to a "t." are they accurate? 
Repository dialog? 

Geez i need help.  ](*,)
Thanks.

---

### Post by taurus on 2007-05-20
There is something with line 37 of your /etc/apt/sources.list.  Can you post it here?

```
cat /etc/apt/sources.list
```

---

### Post by lunaticHIGH on 2007-05-20
how do i find line 37?? count? 

here's what i get... 

 cat /etc/apt/sources.list
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty restricted main

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates restricted main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security restricted main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”
“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main”



++ I have no idea how to read this... 
thanks for any help...

---

### Post by lunaticHIGH on 2007-05-20
also, i have no problem just removing this repository from my install - ill get the codecs somewhere else -

At this point,  I'm just looking to get back to square 1 

thanks again.

---

### Post by taurus on 2007-05-20
Edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and remove the last two lines from your repos.

```
“deb http://www.getautomatix.com/apt feisty main”
“deb http://www.getautomatix.com/apt feisty main”
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```
Just wondering why you need to install Automatix with Feisty since you can find anything you need in either Add/Remove, synaptic, apt-get, or aptitude.

---

### Post by lunaticHIGH on 2007-05-20
Hey great thanks so much for the help.

To answer your question:

In that original article (my first post) i had dl'ed all these codecs expecting to get a one size fits all for all the things that i would need.  The pursuing problems made Automatix's more defined DL structure (IE breaking it down to codecs, not jsut media/sound) appealing based on the problems i had with a 'one size fits all solution' 

but obviously, going to a random, non popular, non supported sources has its um, er.. drawbacks...

thanks for all of the help.

---

### Post by taurus on 2007-05-20
If you need codecs for your media, here's a guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

