---
title: "Problem downloading updates from many reposetories"
date: 2010-04-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-18
Failed to bring [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (110: Connection timed out)
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.

why is that and what can i do about it?

---

### Post by sparker256 on 2010-04-18
> **aviramof said:**
> Failed to bring [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (110: Connection timed out)
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.

why is that and what can i do about it?

I used the following command with no trouble about 30 minutes ago on this side of the world.

sudo aptitude update && sudo aptitude safe-upgrade

It updated fine for me.

Bill

---

### Post by IanW on 2010-04-18
Medibuntu's repo seems to be down at the moment. Try again tomorrow.

---

### Post by aviramof on 2010-04-18
ok thanks for the info i don't know about tomorrow but maybe in the a few hours.

and if we are already talking about updates there hasn't been a lot in the past day or so does anyone knows why?

---

### Post by clive littlewood on 2010-04-18
Hi

I've had 50 to 60 updates over the last 2 days !!!!

Clive

---

### Post by brucemartin on 2010-04-18
> **aviramof said:**
> Failed to bring [http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11). - connect (110: Connection timed out)
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2](http://packages.medibuntu.org/dists/lucid/non-free/i18n/Translation-he.bz2)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/lucid/non-free/binary-i386/Packages.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Failed to bring [http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz](http://packages.medibuntu.org/dists/lucid/non-free/source/Sources.gz)  Unable to connect to packages.medibuntu.org:http:
Some index files failed to download, they have been ignored, or old ones used instead.

why is that and what can i do about it?

here is a fix: [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by wojox on 2010-04-18
> **brucemartin said:**
> here is a fix: [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

Cool, I was having the same problem. Thanks for the link. :P

---

### Post by aviramof on 2010-04-18
why replace wouldn't the previous address would return eventually?

---

### Post by executorvs on 2010-04-18
they are working on fixing the problem. a bug was filed at [https://bugs.launchpad.net/medibuntu/+bug/565810](https://bugs.launchpad.net/medibuntu/+bug/565810) so just be patient and it'll be back soon.

---

### Post by brucemartin on 2010-04-18
> **aviramof said:**
> why replace wouldn't the previous address would return eventually?

the mirror will also continue to work...

---

### Post by vin0 on 2010-04-18
i'm having this problem as well and wanted to replace my packages.medibuntu.org repo with one of the mirrors posted.  only problem is when i check my /etc/apt/sources.list, it isn't listed, but when i do apt-get update i get:

> Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic Release.gpg                           
  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) karmic/non-free Translation-en_US
  Unable to connect to packages.medibuntu.org http:
Reading package lists... Done                            
W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/Release.gpg](http://packages.medibuntu.org/dists/karmic/Release.gpg)  Could not connect to packages.medibuntu.org:80 (88.191.82.11), connection timed out

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Failed to fetch [http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2](http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2)  Unable to connect to packages.medibuntu.org http:

W: Some index files failed to download, they have been ignored, or old ones used instead.how can i replace it and add the mirrors?  i originally added the repo by pasting the code under "adding the repository" on [this]("https://help.ubuntu.com/community/Medibuntu") page.[URL="https://help.ubuntu.com/community/Medibuntu"]
[/URL]

---

### Post by aviramof on 2010-04-18
just use gksu --desktop /usr/share/applications/software-properties-gtk.desktop /usr/bin/software-properties-gtk

and this repo is not default so it possible you didn't add it in the past just add it to sources.list and that it.

---

### Post by Uncle Spellbinder on 2010-04-18
The answer is here (from post #6):
> **brucemartin said:**
> here is a fix: [http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html](http://www.webupd8.org/2010/04/medibuntu-repository-down-what-to-do.html)

---

### Post by narnie on 2010-04-19
Now the problem is those sites are down, too. Must not be able to handle the traffic diverted from packages.medibuntu.org being down.

Any news as to what is wrong in the main mirrors?

Narnie

**Sorry, spoke too soon. They just have ping disabled. Just updated with one. Sorry.**

---

### Post by techstop on 2010-04-21
Looking forward to getting this fixed, it's been broken for a while now (and I've just installed a new mythbuntu).:(

---

