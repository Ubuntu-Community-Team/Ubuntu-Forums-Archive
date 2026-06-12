---
title: "[SOLVED] Hardy apt-get update segmentation fault"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by lymatas on 2008-04-29
Hello,

I have upgraded one computer from Dapper to Hardy. After upgrade there is a problem
with apt-get / aptitude.
If I enable universe repository
(deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe) in
sources.list, I'm getting segfault during apt-get update:

..
Gauti:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/main Sources [14B]
Gauti:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/restricted Sources [14B]
Gauti:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Packages [14B]
Gauti:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/universe Sources [14B]
Gauti:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Packages [14B]
Gauti:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-updates/multiverse Sources [14B]
Gauta 7488kB iš 1min45s (70,7kB/s)
Segmentation faultsts... 68%

I cannot use universe. If i disable it, apt-get update works ok.

How it can be repaired?

Thank You.

---

### Post by quibbler on 2008-04-29
It maybe a corrupted apt cache, open a terminal and remove the .bin files in /var/cache/apt:

from terminal:

sudo rm /var/cache/apt/*.bin
sudo apt-get -update
sudo apt-get -upgrade

---

### Post by lymatas on 2008-04-29
> **quibbler said:**
> It maybe a corrupted apt cache, open a terminal and remove the .bin files in /var/cache/apt:

from terminal:

sudo rm /var/cache/apt/*.bin
sudo apt-get -update
sudo apt-get -upgrade

No luck:

# rm /var/cache/apt/*.bin
# apt-get -update
E: Command line option 'p' [from -update] is not known.
# apt-get update
Spauskite [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-lt
Spauskite [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release.gpg
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Translation-lt
Spauskite [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Translation-lt
Ign [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Translation-lt
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy Release
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates Release
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/main Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/restricted Packages
Gauti:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/universe Packages [4297kB]
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy/multiverse Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/main Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/restricted Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/universe Packages
Spauskite [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) hardy-updates/multiverse Packages
Gauta 4297kB iš 32s (132kB/s)
Segmentation faultsts... 66%
#

Problem isn't in apt-cache.

Vilmantas

---

### Post by Hotwheelz79 on 2008-04-29
Hi lymatas,
I posted here about a simalar issue see if it works for u.
[http://ubuntuforums.org/showthread.php?t=773788](http://ubuntuforums.org/showthread.php?t=773788)

Thanks.

:-)

---

### Post by mrcorey on 2008-05-05
I am encountering the same problem.  I can apt-get updates and the apt-get upgrade command fetches the files, but it segfaults as soon as its time to install.  If I install the packages individually from the apt cache with dpkg, it works.  There's a lot out there about this problem, but it all points to the same solution, which was mentioned already above by quibbler.  That does not work for me either.  Apt, aptitude, and everything it relies on is broken, it seems.

Any gurus out there who can help us out? Tell us what kind of debugging info you'd need (and perhaps how to obtain it).

After thinking about it for a bit, I don't have this problem.  Mine's different.

---

### Post by lymatas on 2008-05-12
Solved.

It's needed to increace apt's cache limit in /etc/apt/apt.conf or simply delete this file.

Now apt and aptitude works perfectly.

---

### Post by Nawaf on 2009-10-05
I have the same problem with Jackalope. Thanks to quibbler it's solved.

---

### Post by tgroff on 2011-05-25
Same problem with Lucid 10.04, quibbler's suggestion fixed the problem, thanks!

---

