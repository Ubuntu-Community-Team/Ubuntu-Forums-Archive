---
title: "help"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by larrypinsupplync@msn.com on 2006-11-21
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by taurus on 2006-11-21
Let's have a look at your /etc/apt/sources.list.  Open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here...

```
cat /etc/apt/sources.list
```

---

### Post by adamkane on 2006-11-21
Pick at least a two word title for your threads.

---

### Post by larrypinsupplync@msn.com on 2006-11-21
larry@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
larry@ubuntu:~$

---

### Post by taurus on 2006-11-21
If I were you, I would make my /etc/apt/sources.list to look something like this!

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted
deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe
deb-src http://security.ubuntu.com/ubuntu breezy-security universe

```
Then, run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by larrypinsupplync@msn.com on 2006-11-21
how do i access my sources list? then can i just copy/paste what you posted?

---

### Post by taurus on 2006-11-21
Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.lisst
```

---

### Post by larrypinsupplync@msn.com on 2006-11-21
(gedit:9365): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
larry@ubuntu:~$

---

### Post by taurus on 2006-11-21
Then use nano instead...

```
sudo nano -Bw /etc/apt/sources.list
```
When you are done, hold down <Ctrl> while pressing x to exit.  Don't forget to tell it to save it as sources.list...

To be sure, before you run that last two commands from my previous post, look in /etc/apt/sources.list to make sure you have saved the changes.

```
cat /etc/apt/sources.list
```

---

### Post by larrypinsupplync@msn.com on 2006-11-21
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main$

## Uncomment the following two lines to fetch updated software from the network# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe main restricted

^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell



it didn't open a new window this time. this just came up in the terminal

---

### Post by taurus on 2006-11-21
Yes, nano is a text base editor so just use your arrow keys to navigate around...

---

### Post by larrypinsupplync@msn.com on 2006-11-21
ok, that worked, but... I still get the same error message when i try to start the package manager

---

### Post by taurus on 2006-11-21
Did you remember to run "sudo aptitude update" after you saved the changes?

---

### Post by larrypinsupplync@msn.com on 2006-11-21
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
66% [Connecting to us.archive.ubuntu.com (1.0.0.0)]

thats all it will do

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
50% [Connecting to us.archive.ubuntu.com (1.0.0.0)]

then it just stops

---

### Post by taurus on 2006-11-21
Maybe you need to edit your /etc/apt/sources.list again and remove the "us" from all those lines...  Then see if you can update it first with

```
sudo aptitude update
```

---

### Post by larrypinsupplync@msn.com on 2006-11-21
larry@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
66% [Connecting to archive.ubuntu.com (1.0.0.0)]


no change

---

