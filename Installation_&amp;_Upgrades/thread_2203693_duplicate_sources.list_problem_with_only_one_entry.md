---
title: "duplicate sources.list problem with only one entry in sources.list"
date: 2014-02-04
forum: Installation &amp; Upgrades
---

### Post by mmistroni on 2014-02-04
HI all
 i have upgraded to ubuntu 12.04 on my toshiba satellite
i keep on getting this exception when running apt-get update

Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) precise/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages)

the only non commented entry in my sources.list is this line

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main restricted universe multiverse

could anyone assist?

kind regards
 marco

---

### Post by Bashing-om on 2014-02-04
mmistroni; Sure !

We can help.

Post back the output -between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list

```
And we will see if we can identify that duplicate entry and advise how to remedy the situation.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mmistroni on 2014-02-06
hi
 here it is
```

marco@marco-laptop:~$ cat -n /etc/apt/sources.list
     1	#############################################################
     2	################### OFFICIAL UBUNTU REPOS ###################
     3	#############################################################
     4	
     5	###### Ubuntu Main Repos
     6	deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse
     7	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
     8	
     9	###### Ubuntu Update Repos
    10	# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
    11	# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
    12	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
    13	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
    14	
    15	###### Ubuntu Partner Repo
    16	# deb http://archive.canonical.com/ubuntu oneiric partner
    17	# deb-src http://archive.canonical.com/ubuntu oneiric partner
    18	
    19	###### Ubuntu Extras Repo
    20	# deb http://extras.ubuntu.com/ubuntu oneiric main
    21	# deb-src http://extras.ubuntu.com/ubuntu oneiric main
marco@marco-laptop:~$ cat -n /etc/apt/sources.list
     1	#############################################################
     2	################### OFFICIAL UBUNTU REPOS ###################
     3	#############################################################
     4	
     5	###### Ubuntu Main Repos
     6	deb http://archive.ubuntu.com/ubuntu precise main restricted universe multiverse
     7	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric main restricted universe multiverse
     8	
     9	###### Ubuntu Update Repos
    10	# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
    11	# deb http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
    12	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-security main restricted universe multiverse
    13	# deb-src http://uk.archive.ubuntu.com/ubuntu/ oneiric-updates main restricted universe multiverse
    14	
    15	###### Ubuntu Partner Repo
    16	# deb http://archive.canonical.com/ubuntu oneiric partner
    17	# deb-src http://archive.canonical.com/ubuntu oneiric partner
    18	
    19	###### Ubuntu Extras Repo
    20	# deb http://extras.ubuntu.com/ubuntu oneiric main
    21	# deb-src http://extras.ubuntu.com/ubuntu oneiric main
marco@marco-laptop:~$ ^C
marco@marco-laptop:~$ 

```

---

### Post by Bashing-om on 2014-02-06
mmistroni; Hello,

No problem there, what is the return from terminal command ?:
```

cat /etc/apt/sources.list.d/*.list

```
As the directory "sources.list.d" is an alternate source containing additional files.

[INDENT][INDENT]we still be looking
[/INDENT][/INDENT]

---

### Post by mmistroni on 2014-02-07
Hi
 apologies i thought i did :(
here it is
```

marco@marco-laptop:~$ cat /etc/apt/sources.list.d/*.list
# deb http://ppa.launchpad.net/eugenesan/java/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/eugenesan/java/ubuntu oneiric main
deb http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu precise main
deb-src http://ppa.launchpad.net/ferramroberto/sopcast/ubuntu precise main
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
# channel for the karmic (9.10) partner channel
# 
#:description:This channel contains the partner software for karmic
deb http://archive.canonical.com/ubuntu precise partner
# channel for the lucid (10.04) partner channel
# 
#:description:This channel contains the partner software for lucid
deb http://archive.canonical.com/ubuntu precise partner
## Please report any bug on https://bugs.launchpad.net/medibuntu/
# deb http://packages.medibuntu.org/ maverick free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx" disabled on upgrade to maverick
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"
# deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise
# deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu precise main # disabled on upgrade to precise
# Typesafe repository.
deb http://apt.typesafe.com/ unicorn main # Typesafe "unicorn" releases.
deb http://ppa.launchpad.net/venerix/pkg/ubuntu precise main
deb-src http://ppa.launchpad.net/venerix/pkg/ubuntu precise main
deb http://ppa.launchpad.net/webupd8team/java/ubuntu precise main
deb-src http://ppa.launchpad.net/webupd8team/java/ubuntu precise main

```

kind regards
 Marco

---

### Post by Bashing-om on 2014-02-07
mmistroni; Hey,

Got it !

see:
> 
#:description:This channel contains the partner software for karmic
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
//
#:description:This channel contains the partner software for lucid
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


Remove either one of those files, and all should be good.

[INDENT][INDENT]seek and ye shall find
[/INDENT][/INDENT]

---

