---
title: "Error during update. Failed to fetch. . ."
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2006-06-02
I get this error when I try to upgrade Breeze to Dapper: "Error during update. Failed to fetch  [http://archived.ubuntu.com/unbuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archived.ubuntu.com/unbuntu/dists/dapper/multiverse/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)." 

The note also says it is likely a network  problem. How should I proceed?

---

### Post by meng on 2006-06-02
Looks like there's difficulty with your machine making the connection to the repository. Are you having any difficulty connecting to the internet?

---

### Post by lakelovers on 2006-06-02
Have DSL with no problems connecting.

---

### Post by meng on 2006-06-02
[QUOTE=lakelovers]I get this error when I try to upgrade Breeze to Dapper: "Error during update. Failed to fetch  [http://archived.ubuntu.com/](http://archived.ubuntu.com/)**unbuntu**/dists/dapper/multiverse/binary-i386/Packages.gz Sub-process gzip returned an error code (1)." 

The note also says it is likely a network  problem. How should I proceed?[/QUOTE]

I just noticed, there is a spelling mistake. Fix the repos/source list, then it should work.

---

### Post by lakelovers on 2006-06-02
[QUOTE=meng]I just noticed, there is a spelling mistake. Fix the repos/source list, then it should work.[/QUOTE]

That's my misspelling when I wrote the post. 

However, I get this addtional note when I try the update from the terminal: Some updates require the removal of further software. Use the function "Mark All Upgrades" of the package manager "Synaptic" or run "sudo apt-get dist-upgrade" in a terminal to update your system completely. When I run "sudo apt-get dist-upgrade" I get this in return:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  cpp cpp-4.0 libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Does this have an effect on the upgrading proprocess?

By the way, I'm impressed at the speed of your responses. It's very much appreciated.

Jerry

---

### Post by meng on 2006-06-02
Yeah I was perplexed by the kept back problem too. I "cheated" and used synaptic to choose the kept back packages - I was then told that some other installed packages would be replaced by newer packages (with similar but different names) that were dependencies of the kept-back packages.

So you could select those packages with synaptic, although I suspect that
sudo apt-get install cpp cpp-4.0 libc6-dev
would also work.

I'm fast because I'm hovering around with nothing better to do than browse forums.

---

### Post by lakelovers on 2006-06-02
Meng. . .
Seems as though I'm going in circles. I tried "sudo apt-get install cpp cpp-4.0 libc6-dev" and this is what I got. I also tried Synaptic, and got basically, the same thing. I don't know how to satisfy those dependencies.

The following packages have unmet dependencies:
  cpp-4.0: Depends: gcc-4.0-base (= 4.0.3-1ubuntu5) but 4.0.1-4ubuntu9 is to be installed
  libc6-dev: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.5-1ubuntu12.5.10.1 is to be installed
E: Broken packages

---

### Post by meng on 2006-06-02
I assume all relevant up-to-date repositories are enabled. Can you not upgrade to 4.0.3 and 2.3.6 respectively? I was able to, here's my sources.list, note I commented out many repos:

```

## All officially supported packages, including security- and other updates

# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu backports
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
# deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# kubuntu.org packages for the latest KDE version (packages, GPG key: DD4D5088)
# deb http://kubuntu.org/packages/kde-latest dapper main

# Penguin Liberation Front (PLF)
# deb http://theli.free.fr/packages/dapper/ ./

# Dapper PLF repository (not yet available)
# deb http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free
# deb-src http://packages.freecontrib.org/ubuntu/plf/ dapper free non-free

# Compiz (packages, GPG key: 31A5F97FED8A569E)
# deb http://www.beerorkid.com/compiz/ dapper main
# deb http://xgl.compiz.info/ dapper main aiglx
# deb http://compiztools.free.fr/debian unstable main

# Gaim 2 Beta 3
deb http://people.ubuntu.com/~seb128/deb ./

# Skype
# deb http://download.skype.com/linux/repos/debian/ stable non-free

# Wine Dapper
# deb http://wine.lowvoice.nl/apt dapper main

# Official Wine
deb-src http://wine.budgetdedicated.com/apt dapper main
deb http://wine.budgetdedicated.com/apt dapper main
```

---

### Post by lakelovers on 2006-06-02
My source list seems to be completely different. I'll post it here but I don't know how to get the scrolling window with the list as you have. How do you do that? I'm going to shut down for tonight and tackle this in the morning. It's about 10 p.m, central time here in east texas. Thanks for your help. If you can add anything at this point I'll pick it up in the morning.  Jerry

---

### Post by meng on 2006-06-02
Good night and good luck with everything.

[ code ]
[ /code ]

without the spaces of course, will separate code/text into a scrollable windowlet.

---

### Post by lakelovers on 2006-06-03
Menge. . . Here's my source list. If I were to replace mine with yours would that work?
```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu breezy main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu breezy-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://archive.ubuntu.com/ubuntu breezy multiverse
 deb-src http://archive.ubuntu.com/ubuntu breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

 deb http://security.ubuntu.com/ubuntu breezy-security universe
 deb-src http://security.ubuntu.com/ubuntu breezy-security universe

 deb http://security.ubuntu.com/ubuntu breezy-security multiverse
 deb-src http://security.ubuntu.com/ubuntu breezy-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ breezy free non-free



```

---

### Post by meng on 2006-06-03
You know what I would do first, rather than using my sources.list?
Replace all the instances of breezy with dapper in your sources.list.
This will likely allow you to access the latest versions of those other packages.

At some point you will probably want to comment out the cdrom repository. Could be done after you sort this problem out.

---

### Post by dglock on 2006-06-03
I am getting the same error message this morning!  Haven't changed any repositories since yesterday, must be some thing with one of the servers.

  don

---

### Post by lakelovers on 2006-06-03
I changed all the "breezy" references in the source list to "Dapper." Then did an update and got a whole bunch of error notations. Maybe I should comment out some of the lines.

```

#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://archive.ubuntu.com/ubuntu Dapper main restricted
deb-src http://archive.ubuntu.com/ubuntu Dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu Dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu Dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

 deb http://archive.ubuntu.com/ubuntu Dapper multiverse
 deb-src http://archive.ubuntu.com/ubuntu Dapper multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu Dapper-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu Dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu Dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu Dapper-security main restricted

 deb http://security.ubuntu.com/ubuntu Dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu Dapper-security universe

 deb http://security.ubuntu.com/ubuntu Dapper-security multiverse
 deb-src http://security.ubuntu.com/ubuntu Dapper-security multiverse

## PLF repositories, contains litigious packages, see http://wiki.ubuntu-fr.org/doc/plf
##deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ Dapper free non-free
##deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ Dapper free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
##deb http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ Dapper free non-free
##deb-src http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/ Dapper free non-free



```

---

### Post by lakelovers on 2006-06-03
I changed "Dapper" to "dapper" and the update worked most of the way with a few errors. Then I did an upgrade which installed some apps and ended with this message: 

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) Dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_Dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

---

### Post by meng on 2006-06-03
maybe you left behind a couple of "Dapper"s instead of "dapper"s?

---

### Post by lakelovers on 2006-06-03
I hope I haven't just hosed my system. I change a couple of "Dappers" that I missed to "dapper," did another update which went ok then did $sudo apt-get dist-upgrade, which went ok and is still going. It ask me to insert a CD (which I downloaded a day ago), and now there's a whole bunch of files being downloaded with "hours" of time listed. I certainly didn't want an install but rather an upgrade. Is there a way of stopping the process if I should?

**Edit**: Here's how the upgrade attempt ended: 

1122 upgraded, 226 newly installed, 72 to remove and 0 not upgraded.
Need to get 724MB/729MB of archives.
After unpacking 314MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)'
in the drive '/cdrom/' and press enter

**Second Edit** I guess after re-reading those directions the files are unpacking, so hopefully everything is okay, but it is sure taking a long time to unpack.

---

### Post by meng on 2006-06-03
I have my fingers crossed for you. At least if most of the packages are coming of the CDROM, the time will be spent configuring rather than downloading.

---

### Post by lakelovers on 2006-06-03
[QUOTE=meng]I have my fingers crossed for you. At least if most of the packages are coming of the CDROM, the time will be spent configuring rather than downloading.[/QUOTE]

It's still unpacking (6:00 pm) and only about 40% done. I'm really puzzled. Do you supposed I'm getting every app Dapper contains? Well, somtime tomorrow, I'll know. I'll blow my top if I've lost valuable files. Fortunately, I do have my files backed up, but not the whole system.

Jerry

---

### Post by Max Roswell on 2006-06-03
I'm getting the exact same error today.  Seems like tons of files are downloading, and then I see:

> Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found


Any idea what these are and why they're not there?  My net connection is fine, and I haven't edited a THING on this installation of Breezy.

---

### Post by doorman_54 on 2006-06-03
[QUOTE=Max Roswell]I'm getting the exact same error today.  Seems like tons of files are downloading, and then I see:



Any idea what these are and why they're not there?  My net connection is fine, and I haven't edited a THING on this installation of Breezy.[/QUOTE]



Same here budz....waiting :)

---

### Post by lakelovers on 2006-06-04
After unpacking a zillion files in my attempt to upgrade, my system is still intact but I still don't have the Dapper upgrade. Now there is an update alert for 512 updates and the Dapper Upgrade option is present. I clicked on the upgrade option and it is grinding away with nothing showing in the upgrade window. Something is whacky.
Any ideas?
Jerry

---

### Post by meng on 2006-06-04
Oh boy I'm afraid to say anything further because I don't want your system to get broken ...

---

### Post by lakelovers on 2006-06-04
[QUOTE=meng]Oh boy I'm afraid to say anything further because I don't want your system to get broken ...[/QUOTE]
 Menge. . . I appreciate your help. I rebooted and that cleared the "upgrade" window. Then I went to Synaptic and clicked on "Mark All Upgrades." Then I got the direction to insert the 6.06 CD, which I didn't. I started a new thread asking what I should do with this duplicate instruction. That's where I'm sitting at the moment.
Jerry

---

