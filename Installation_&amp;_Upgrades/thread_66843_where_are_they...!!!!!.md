---
title: "where are they...!!!!!?????"
date: 2005-09-18
forum: Installation &amp; Upgrades
---

### Post by randlieb on 2005-09-18
what happened to real player 10, w32codecs and java runtime in synaptic? i re-installed ubuntu hoary and have loaded and reloaded and installed and apt geted the repositories until i'm blue in the face and they just aren't there anymore!!! what gives?????????????? they were all there when i first installed hoary a few weeks ago....

---

### Post by mcmuffy on 2005-09-18
Sounds like you forgot to add the backport repos.

---

### Post by XDevHald on 2005-09-18
[QUOTE=mcmuffy]Sounds like you forgot to add the backport repos.[/QUOTE]
 When posting a reply please provide the user with the information they need, this way it is done within one post :)

Open a terminal and type: [b]sudo gedit /etc/apt/sources.list

[/b]Then place the text provided at the bottom in your sources.list.

Once you're done, Save It and you're done, then sudo apt-get update & sudo apt-get upgrade. :)

 >  ## Backports
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/]("http://ubuntu-backports.mirrormax.net/") hoary-extras main universe multiverse restricted 

---

### Post by randlieb on 2005-09-18
thanks but backports already in the file. did find upon closer inspection 'universe' typed in twice and deleted the one not needed and went ahead and apt get again but alas......

i followed the instructions from the 'unofficial guide' just as with my first install.
--------------------------------------------------------------------------------------------------------------
here's what i get when i try to install java runtime....

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
-----------------------------------------------------------------------------------------------------------------
here's what i get when i try to install w32codecs....

Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate
---------------------------------------------------------------------------------------------------------------
here's what i get when i try to install realplayer (in synaptic it's realplayer 8...my previous installation it was 10!?)

This is the Real Player installer package, it does not actually contain   &#9474;
 &#9474; Real Player. You will need to go download Real Player by hand. Once you   &#9474;
 &#9474; have downloaded it you can proceed and tell the installer which           &#9474;
 &#9474; directory you put it in.                                                  &#9474;
 &#9474;                                                                           &#9474;
 &#9474; Would you like to run the Real Player installer now?

Please visit [http://scopes.real.com/real/player/unix/unix.html](http://scopes.real.com/real/player/unix/unix.html) Select    &#9474;
  &#9474; 'Linux 2.x (libc6 i386) RPM'. Download it, and ensure permissions are    &#9474;
  &#9474; appropriate. It should be called rp8_linux20_libc6_i386_cs2_rpm. When    &#9474;
  &#9474; prompted, enter the directory you downloaded it to (defaults to /root).  &#9474;
  &#9474;                                                                          &#9474;
  &#9474; Real Player has been downloaded to where?  

....and yadayadayada...this looks like a VERY old installation script and i saw nothing of this when installing it on my first ubuntu installation.

does anyone know what's going on? these packages are NOT in my synaptic list. but a few weeks ago they were!!!!!! ](*,)

---

### Post by fortytwo on 2005-09-18
I noticed the same thing today, I can't find w32codecs in synaptic, and I've followed the 'adding more repositories' guide as well.

---

### Post by John.Michael.Kane on 2005-09-19
you can try this. it's what is working for me just copy and paste. 

```
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

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
``` 


hope it helps

---

### Post by fortytwo on 2005-09-19
[QUOTE=SD-Plissken]you can try this. it's what is working for me just copy and paste. 

```
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

## Backports
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
#deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted
``` 


hope it helps[/QUOTE]
 Something with the repository must be messed up...yours doesn't work for me either.

---

### Post by jhilgey on 2005-09-19
I get the same thing.  w32codecs is not found: 

here is just a simple search:

 sudo apt-cache search w32
libtk-tablematrix-perl - Table/matrix widget extension to Perl/Tk
mingw32 - Minimalist GNU win32 (cross) compiler
mingw32-binutils - Minimalist GNU win32 (cross) binutils
mingw32-runtime - Minimalist GNU win32 (cross) runtime
jamesh@lappy:~$

I'm using the same sources file as mentioned above. 

Thanks!

---

### Post by [pl]ice on 2005-09-19
i got mine from google :/  fresh rpm or something for debian, but it still doesn't have some codecs :(

---

### Post by John.Michael.Kane on 2005-09-19
do a fresh install then use this cd and it will install the codec's and others software you may need.. [http://ubuntuforums.org/showpost.php?p=150088&postcount=1](http://ubuntuforums.org/showpost.php?p=150088&postcount=1)

---

### Post by angrykeyboarder on 2005-09-19
[QUOTE=randlieb]what happened to real player 10, w32codecs and java runtime in synaptic? i re-installed ubuntu hoary and have loaded and reloaded and installed and apt geted the repositories until i'm blue in the face and they just aren't there anymore!!! what gives?????????????? they were all there when i first installed hoary a few weeks ago....[/QUOTE]

Whew! I thought it was just me. Yep. w32codecs is definetly among the missing.

So is [ubuntuguide.org]("http://ubuntuguide.org") for that matter.....

---

### Post by Fiyawerx on 2005-09-19
[QUOTE=angrykeyboarder]Whew! I thought it was just me. Yep. w32codecs is definetly among the missing.

So is [ubuntuguide.org]("http://ubuntuguide.org") for that matter.....[/QUOTE]

Yeah, guess today was a bad day to choose to re-install, I got it also, I also can't nslookup the mirrormax servers or ping, looks like some problems.

Same with the ubuntuguide, can't find an address for it.

---

### Post by XDevHald on 2005-09-19
Here is a thread with this topic already active: [http://ubuntuforums.org/showthread.php?t=66996&page=1&pp=10](http://ubuntuforums.org/showthread.php?t=66996&page=1&pp=10)

---

### Post by angrykeyboarder on 2005-09-20
[QUOTE=Steve Myers]Here is a thread with this topic already active: [http://ubuntuforums.org/showthread.php?t=66996&page=1&pp=10]("http://ubuntuforums.org/showthread.php?t=66996&page=1&pp=10")[/QUOTE]

Funny, I found little mention of Real Player, w32codes, Java or Ubuntu Backports in that thread... ;-)

---

### Post by DemiUrge8 on 2005-09-20
Well, okay. So what are we to do about having the w32codecs? I just did a fresh install too.

---

### Post by XDevHald on 2005-09-20
[QUOTE=angrykeyboarder]Funny, I found little mention of Real Player, w32codes, Java or Ubuntu Backports in that thread... ;-)[/QUOTE]
 Funny enough, you're right my apologies, and this was the wrong thread to have been posted in.

Thank You!

---

### Post by Vicsun on 2005-09-20
Posting to confirm I have the same problem. In the mean time, you can install java runtime environment the hard way:
[[IMG]http://img154.imageshack.us/img154/8270/screenshot6kj.th.png[/IMG]](http://img154.imageshack.us/my.php?image=screenshot6kj.png)
(posting a screenshot because ubuntuguide is down, and providing a link to google cache of a page is a pain)

This is for Warty Warthog but it should work for Hoary as well.

---

### Post by Fiyawerx on 2005-09-20
Here's a temporary solution someone posted in another thread.

[http://www.ubuntuforums.org/showthread.php?t=67279](http://www.ubuntuforums.org/showthread.php?t=67279)

---

Posted by NeoChaosX:

The mirrormax mirror is down. Try replacing all instances of it in /etc/apt/sources.list to [http://mirror.brianpuccio.net/ubuntu-backports-repository/](http://mirror.brianpuccio.net/ubuntu-backports-repository/)

----

it = the mirrormax repositories

---

### Post by angrykeyboarder on 2005-09-20
[QUOTE=Vicsun]Posting to confirm I have the same problem. In the mean time, you can install java runtime environment the hard way:

-snip-

(posting a screenshot because ubuntuguide is down, and providing a link to google cache of a page is a pain)

.[/QUOTE]

Naah, It's pretty simple really. ;)

[http://tinyurl.com/dvbwv]("http://tinyurl.com/dvbwv")

---

### Post by angrykeyboarder on 2005-09-20
[QUOTE=DemiUrge8]Well, okay. So what are we to do about having the w32codecs? I just did a fresh install too.[/QUOTE]

Uhh...

Get them elsewhere?

[ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb]("ftp://ftp.nerim.net/debian-marillat/pool/main/w/w32codecs/w32codecs_20050412-0.0_i386.deb")

[http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2]("http://www4.mplayerhq.hu/MPlayer/releases/codecs/essential-20050412.tar.bz2")

Or you could try adding the following to your sources.list file then get them via apt/Synaptic

deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") sarge main
deb [ftp://ftp.nerim.net/debian-marillat/]("ftp://ftp.nerim.net/debian-marillat/") etch main

Of course there is no guaurantee that mixing this Non-Ubuntu stuff with Ubuntu stuff won't destroy your hard drive and cause your CPU to melt down like the nuclear reactor at Three Mile Island...

---

### Post by mahalo-ubuntu on 2005-09-22
[QUOTE=Fiyawerx]Same with the ubuntuguide, can't find an address for it.[/QUOTE]

It still appears to be down...

I've been using Google's cache but I've recently found [majalah.com](http://www.majalah.com/) which has a copy of the English version.

-Mike

---

