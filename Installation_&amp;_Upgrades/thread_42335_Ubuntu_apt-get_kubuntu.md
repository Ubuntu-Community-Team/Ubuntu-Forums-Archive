---
title: "Ubuntu apt-get kubuntu"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by blind0wl on 2005-06-17
Hi,

First post, so be nice...have downloaded and installed Ubuntu, and now want to see what kubuntu has to offer without downloading another cd.  From what Ive seen, everyone is typing:

```
sudo apt-get install kubuntu-desktop
```

And Im getting an error:

```
Reading Package Lists... Done
Building Dependency Tree... Done
E: Couldn't find package kubuntu-desktop

```

Any help?  Ive uncommented most of the repositories in source.list with no help.

Cheers

Blindy

---

### Post by Trickyphillips on 2005-06-17
Use "sudo apt-get update" after uncommenting the lines in your sources.list. After that's done, try "sudo apt-get install kubuntu-desktop" to install KDE.

If you're still having problems, post your sources.list. :)

---

### Post by blind0wl on 2005-06-17
Got the same error, heres my sources.list:

```

 more /etc/apt/sources.list
#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by Trickyphillips on 2005-06-19
[QUOTE=blind0wl]Got the same error, heres my sources.list:

```

 more /etc/apt/sources.list
#deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted


## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu/ warty main restricted
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ warty universe
deb-src http://archive.ubuntu.com/ubuntu/ warty universe

deb http://security.ubuntu.com/ubuntu/ warty-security main restricted
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```[/QUOTE]
 Hi. Very sorry for the slow reply.

From the second line. it looks as if you're using an unstable version of Warty Warthog. Is this correct? If so, I think you should remove the following, as it's for Hoary:

```
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
```

I highly suggest upgrading to Hoary Hedgehog if possible. It's good to be up to date. If that's not an option, you should try using this as your sources.list, as recommended by the Ubuntu Guide: [http://ubuntuguide.org/4.10/sample/sources.list_extrarepositories](http://ubuntuguide.org/4.10/sample/sources.list_extrarepositories)

Hope this helps.

---

### Post by blind0wl on 2005-06-19
Wow...I only got the iso a couple of days ago, and uncommented most of the sources list and added the backports...to try and get kubuntu to be found.  After looking through the ubuntuguide and its repositories list, I realised I must have been getting old packages.

Am updating with a new sources.list and upgrading....will see if this solves my kubuntu issue.  I really would prefer not to download kubuntu seperately...as their really only WM's with a bit of customisation.

Will update as I progress :)

Thanks for pointing that out to me

---

### Post by Trickyphillips on 2005-06-19
[QUOTE=blind0wl]Wow...I only got the iso a couple of days ago, and uncommented most of the sources list and added the backports...to try and get kubuntu to be found.  After looking through the ubuntuguide and its repositories list, I realised I must have been getting old packages.

Am updating with a new sources.list and upgrading....will see if this solves my kubuntu issue.  I really would prefer not to download kubuntu seperately...as their really only WM's with a bit of customisation.

Will update as I progress :)

Thanks for pointing that out to me[/QUOTE]

You're welcome. :)

Tell me how it works out.

---

### Post by blind0wl on 2005-06-20
After upgrade to Hoary all the things I thought were supposed to work, suddenly did.  I thought Id downloaded Hoary originally, but had a look at my iso and found that indeed it was warty (which explains alot!!).  Have now been having font fun in KDE and a couple of xorg issues, which have been resolved.

Thanks again for the help.

---

### Post by Trickyphillips on 2005-06-20
[QUOTE=blind0wl]After upgrade to Hoary all the things I thought were supposed to work, suddenly did.  I thought Id downloaded Hoary originally, but had a look at my iso and found that indeed it was warty (which explains alot!!).  Have now been having font fun in KDE and a couple of xorg issues, which have been resolved.

Thanks again for the help.[/QUOTE]
 Congrats! I'm glad to see you got everything solved. 

Have fun with Hoary. :)

---

