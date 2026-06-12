---
title: "Repositories HELP!!"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by emoguitarist06 on 2010-01-11
Everytime I run apt-get update I get this error:

**W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3135CD5C26C2E075**

Here is my /etc/apt/sources.list

> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) karmic-security multiverse

# Added by perfectbuntu - [www.category5.tv](www.category5.tv)
deb [http://le-web.org/repository](http://le-web.org/repository) stable main
deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) karmic main

---

### Post by raymondh on 2010-01-12
Have you tried adding the pubkey?  In terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3135CD5C26C2E075
```

And then try to update again.

Post back any errors or success.

Raymond

---

### Post by emoguitarist06 on 2010-01-12
> **raymondh said:**
> Have you tried adding the pubkey?  In terminal

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3135CD5C26C2E075
```

And then try to update again.

Post back any errors or success.

Raymond

YAY It worked! I'll try and memorize this terminal command to add pubkeys :)
Thank You!

---

### Post by Bartender on 2010-01-12
Hi, emo -
It's a two-part process when you're adding a new source like you did.  It's a little confusing the first time or two.

First part of the process is adding the repositories to your computer's list, like you did.

The second part of the process is importing that public key into the folder that stores them.

Ubuntu wants a public key for any repository that you add.  I did the exact same thing you did a few times.  Just added the repositories and didn't realize I had to add the key.

[Here's a link]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu") to a Launchpad blog that should help you to understand.  I'm on dialup so couldn't play the video...

---

### Post by raymondh on 2010-01-12
> **emoguitarist06 said:**
> YAY It worked! I'll try and memorize this terminal command to add pubkeys :)
Thank You!

well done and glad you got it working.

GPG is short for GNU PRIVACY GUARD.  It's role (in my terms) is to make sure you get the right files and .... it's authorized.... for security reasons.

Many ways to get around this problem, aside from the terminal command you now know.

1.  You can use the [Ubuntu Key Server which uses SKS]("http://keyserver.ubuntu.com:11371/")
2.  If the file is stored locally (in your HD, for example), you can use

```
sudo apt-get add *keynumbersfile*.gpg
```

3.  If the key is in an appropriate site (http or FTP), you can add it to your system using

```
wget -q -O - https://dl-*websitename*/linux/linux_signing_key.pub | sudo apt-key add -
```

Once again, congratulations and happy ubuntu-ing.

Raymond

---

### Post by emoguitarist06 on 2010-01-12
> **Bartender said:**
> Hi, emo -
It's a two-part process when you're adding a new source like you did.  It's a little confusing the first time or two.

First part of the process is adding the repositories to your computer's list, like you did.

The second part of the process is importing that public key into the folder that stores them.

Ubuntu wants a public key for any repository that you add.  I did the exact same thing you did a few times.  Just added the repositories and didn't realize I had to add the key.

[Here's a link]("http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu") to a Launchpad blog that should help you to understand.  I'm on dialup so couldn't play the video...

Thanks for the clarification. That is a great blog and video was pretty straight forward.

---

### Post by emoguitarist06 on 2010-01-12
> **raymondh said:**
> well done and glad you got it working.

GPG is short for GNU PRIVACY GUARD.  It's role (in my terms) is to make sure you get the right files and .... it's authorized.... for security reasons.

Many ways to get around this problem, aside from the terminal command you now know.

1.  You can use the [Ubuntu Key Server which uses SKS]("http://keyserver.ubuntu.com:11371/")
2.  If the file is stored locally (in your HD, for example), you can use

```
sudo apt-get add *keynumbersfile*.gpg
```

3.  If the key is in an appropriate site (http or FTP), you can add it to your system using

```
wget -q -O - https://dl-*websitename*/linux/linux_signing_key.pub | sudo apt-key add -
```

Once again, congratulations and happy ubuntu-ing.

Raymond


Are you saying that I can't always use

> sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3135CD5C26C2E075
and just replace the key with the key i get in my error message?

---

### Post by raymondh on 2010-01-12
> **emoguitarist06 said:**
> Are you saying that I can't always use


and just replace the key with the key i get in my error message?

you can use that anytime.  I was just giving you different options :)  Try them (for experience) next time you get a no pubkey error.


Raymond

---

### Post by emoguitarist06 on 2010-01-12
> **raymondh said:**
> you can use that anytime.  I was just giving you different options :)  Try them (for experience) next time you get a no pubkey error.


Raymond

Oh ok :)

---

