---
title: "Problem with repositories???"
date: 2005-03-15
forum: Installation &amp; Upgrades
---

### Post by burki on 2005-03-15
hi every1,

i downloaded 5.04 (hoary) today and installed without a problem. the only problem is i cant add repositiories correctly.

my source list was this before

[B]# deb [http://hu.archive.ubuntu.com/ubuntu](http://hu.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://hu.archive.ubuntu.com/ubuntu](http://hu.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe[/B]


and i changed it totally to this because of the starter guide

[B]deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe[/B]


and after i do "sudo apt-get update" and getting this error...
[B]
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/B]

what dould i do to make it work correctly???

---

### Post by bored2k on 2005-03-15
First of all , you CAN NOT do that !
Hoary is the latest version, Warty wich the Guide repos is based on , are OLD, you would be downgrading yourself !

Open up synaptic package manager, select repositories, settings, select show unmarked and check them all, then clic add and check multiverse repositories. After that is done and saved, input your "marillat's" sources.


While upgrading, only one process can be on this, so you cant have terminal and synaptic work at the same time.

---

### Post by corefile on 2005-03-15
You are correct about fixing it so it does not down grade, but that still does not fix 

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

I don't know how to fix it, but it has something to do with not haveing the public key for that site

---

### Post by corefile on 2005-03-15
Ok found out how to fix this

Follow this 



[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)

2.3 MARILLAT:

Add the following repository to Synaptic:

   URI:            [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
   Distribution:   testing (use unstable here if you are using hoary)
   Section(s):     main

---

### Post by burki on 2005-03-16
ok here is what i did.

1st i put the old backed up sources.list in /etc/apt/ folder

then i checked the repositories and saw only "cd ubuntu 5.04 hoary hedgehog binary

then i got the key and followed all the transactions and nothing was wrong. then came to add in repositories but there it doesnt add.

then i tried to add a normal one and added one normal ubuntu hoary binary and one same but universe one and made a search and found the latest amsn.

did i do something wrong ? should i add more ???

---

### Post by Gary Powers on 2005-03-16
If we have upgraded to Hoary with a clean install from disk, which repositories should be listed in the "sources.list"?

Gary

---

### Post by burki on 2005-03-17
nomore help???

---

