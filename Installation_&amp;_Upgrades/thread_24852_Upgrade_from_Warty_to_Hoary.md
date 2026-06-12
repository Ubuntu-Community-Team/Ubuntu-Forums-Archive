---
title: "Upgrade from Warty to Hoary"
date: 2005-04-08
forum: Installation &amp; Upgrades
---

### Post by chris_andrew on 2005-04-08
Hi, all.

Can I upgrade from Warty to Hoary by just changing my /etc/apt/sources.list?

I've downloaded the Hoary image, but would rather do it a 'clever' way if possible.

Thanks,

Chris.

---

### Post by audax321 on 2005-04-08
Yes, all you have to is change all references from warty to hoary. Then go to terminal and do:

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by chris_andrew on 2005-04-08
audax321,

Thanks, I read a previous post and found out that I needed to copy a Ubuntu reference /etc/apt/souces.list file.

I am doing the update now, but it's very slow.  Instead of using mirrors in the states, is it possible to change them to UK mirrors (or Europe, even)?

Thanks,

Chris.

Current file:

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

# Skype

deb [http://www.bootsplash.de/files/debian](http://www.bootsplash.de/files/debian) unstable main

---

### Post by audax321 on 2005-04-08
I'd like to say yes, but I'm not sure if the packages have any differences in terms of settings for locales...  :-?

---

### Post by chris_andrew on 2005-04-08
Thanks for all your help.

Cheers,

Chris.

---

