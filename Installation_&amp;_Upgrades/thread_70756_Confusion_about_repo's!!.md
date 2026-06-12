---
title: "Confusion about repo's!!"
date: 2005-10-01
forum: Installation &amp; Upgrades
---

### Post by Panthios on 2005-10-01
Hi.
Few days ago, my sources.list didnt suddenly work. I then read in here that the backports has gone official supportet.
So I changed my sources.list
But now I can't find w32codecs.
Would someone, please for the last time, give me a 100% optimal sources.list?
Here is mine now:
```

deb http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary main restricted

deb http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted

deb http://dk.archive.ubuntu.com/ubuntu hoary universe
deb-src http://dk.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

---

### Post by codejunkie on 2005-10-01
[QUOTE=Panthios]Hi.
Few days ago, my sources.list didnt suddenly work. I then read in here that the backports has gone official supportet.
So I changed my sources.list
But now I can't find w32codecs.
Would someone, please for the last time, give me a 100% optimal sources.list?
Here is mine now:
```

deb http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary main restricted
deb http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://dk.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb http://dk.archive.ubuntu.com/ubuntu hoary universe
deb-src http://dk.archive.ubuntu.com/ubuntu hoary universe
deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted
deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main restricted universe multiverse
#deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
#deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```[/QUOTE]
it's not your sources.list file they were removed from all of the backports repos because of copyright restrictions you'll have get them from 
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) sid main

---

### Post by Leif on 2005-10-01
once you've installed what you need, make sure you remove marillat from your sources, to avoid any problems in the future.

---

### Post by Panthios on 2005-10-01
Thx for the answer.
I've added the ftp.nerim.net deb source to my sources.list an ran apt-get update:

```
W: GPG error: ftp://ftp.nerim.net sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: You may want to run apt-get update to correct these problems

```

Running update again, doesnt help on the problem.
I have once tried to get that key-thingy to work, but never found a soloution.

Help?

Best regards

---

### Post by Leif on 2005-10-01
try this :

```

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B90
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update

```

---

### Post by Panthios on 2005-10-01
Thanlk you again for a fast answer.
panthios@kubuntu:~$ gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B90
gpg: keyring `/home/panthios/.gnupg/secring.gpg' created
gpg: keyring `/home/panthios/.gnupg/pubring.gpg' created
gpg: skipping invalid key ID "1F41B90"
panthios@kubuntu:~$ gpg --armor --export 1F41B907 | sudo apt-key add -
gpg: WARNING: nothing exported
gpg: no valid OpenPGP data found.
apt-get update still gives the exact same error.

As I said, I have never got that gpg key to work ;-)

---

### Post by Leif on 2005-10-01
my mistake, sorry; the first line should be : 

```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```

missed the 7 at the end !

---

### Post by Panthios on 2005-10-01
[QUOTE=Leif]my mistake, sorry; the first line should be : 
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
```
missed the 7 at the end ![/QUOTE]

Yeah, why didnt I saw that? ;)
Thank you very much for your help - it works! :razz: 

Best regards from Denmark

---

