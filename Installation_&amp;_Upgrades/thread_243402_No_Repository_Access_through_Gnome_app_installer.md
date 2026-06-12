---
title: "No Repository Access through Gnome app installer"
date: 2006-08-25
forum: Installation &amp; Upgrades
---

### Post by mlitty on 2006-08-25
Hello,
  I've been using Debian variants for about five years now.  I was with Woody through Etch before migrating to Kanotix for fun.  I really liked Kanotix, but have become frustrated by the dangers associated with upgrading.  Because it's based in unmodified Sid, upgrading frequently breaks the whole system, as happened two nights ago.
  I happened to have an Ubuntu disk around and decided to give it a try.  It's 5.1, and I'm interested in a stable upgrade to 6.06.  Given my recent crash and burn with Kanotix, I'm a bit nervous.  I've been reading the forums for a pre-upgrade education.  As instructed, I used apt to upgrade the update-manager.  Then I manually updated the /etc/sources.list using 
> 
A clean Dapper sources.list
[http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2]("http://www.ubuntuforums.org/showpost.php?p=1090438&postcount=2")


I was looking at the Gnome App Installer.  I like that it shows me all of the possible and blocked apps, and suggests how to access the blocked ones using the "settings > Repositories" feature.  My problem is that when I click the Repositories button, nothing happens.  It's as if I don't have access.

I'm noticing that there are a number of unfamilliar files in /etc/apt/.  Normally I only see the source files, but there's some other stuff in the Ubuntu distro.  Any of that significant?

My /etc/apt/sources.list looks like this...

```

deb http://archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
## deb http://archive.ubuntu.com/ubuntu/ dapper universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
## deb-src http://archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
## deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
## deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

```

---

### Post by croak77 on 2006-08-25
First you need to get rid of the last two lines which contain Breezy repo. Second you might want to enable universe and multiverse. You will be quite limited with software if you don't. Third you don't really need the deb-src lines. Only if you want to recompile existing packages. Take a look at the wiki entry.

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by mlitty on 2006-08-25
Thanks for the tip.  I've followed your suggestions and am preparing to dist-upgrade to 6.06.  Wish me luck...

> **croak77 said:**
> First you need to get rid of the last two lines which contain Breezy repo. Second you might want to enable universe and multiverse. You will be quite limited with software if you don't. Third you don't really need the deb-src lines. Only if you want to recompile existing packages. Take a look at the wiki entry.

[https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

---

### Post by mlitty on 2006-08-28
Update:
  All went well, but for a little OO.o glitch I've mentioned elsewhere.  Very smooth, and I love the precompiled nvidia kernel modules!  nice touch.  A brief download and I'm playing my first game of tux racer, or what I assume is tuxracer.  It comes up as Planet Penguin Racer.  I've been hearing about tuxracer for years and just never tried it.  Lots-o-fun.

---

