---
title: "Problem with sources"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by claus on 2005-08-30
Hi,

I'm somewhat at loss with /etc/apt/sources.list. I tried to add some new sources in order not to get the 401 - Authorization required - anymore, but I don't seem to get the proper syntax for the additions, which are listed in Synaptic, like> [http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/main/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/universe/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/multiverse/binary-i386/Packages.gz:) 401 Authorization Required
[http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:](http://backports.ubuntuforums.org/backports/dists/hoary-extras/restricted/binary-i386/Packages.gz:) 401 Authorization RequiredMy current sources.list looks as follows:> ## Webarchive
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
 
## Updatequellen
deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted universe
 
## Backports
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted Could someone give me a clue?

THX,

Claus

---

### Post by John.Michael.Kane on 2005-08-30
Good luck getting help anytime soon..

---

### Post by Lord Illidan on 2005-08-31
[QUOTE=SD-Plissken]Good luck getting help anytime soon..[/QUOTE]

Don't mind this guy, he has some serious attitude problems... (Actually the post might be deleted by the time you read this thread)

Regarding your post, did you use the repositories from the Ubuntu Guide?

These types of repos are not legal repos, as far as I know..

> [http://backports.ubuntuforums.org/b...86/Packages.gz:](http://backports.ubuntuforums.org/b...86/Packages.gz:) 401 Authorization Required 

The ones in your current sources.list seems fine, you could however, use the ones from the ubuntu guide, I think there is a version for your nationality too...

Good luck with Ubuntu and I hope the arrogant guy above me hasn't alienated you from these forums..

---

### Post by John.Michael.Kane on 2005-08-31
Lord Illidan you answered this chaps post yet if i was to post my issues you would pass the post over ....

---

### Post by claus on 2005-08-31
[QUOTE=Lord Illidan]
The ones in your current sources.list seems fine, you could however, use the ones from the ubuntu guide, I think there is a version for your nationality too...

Good luck with Ubuntu and I hope the arrogant guy above me hasn't alienated you from these forums..[/QUOTE]
Not at all! ;-) Thanks for the link to the Ubuntu Guide! There's a very good explanation regarding the addition of repositories!

Claus

---

