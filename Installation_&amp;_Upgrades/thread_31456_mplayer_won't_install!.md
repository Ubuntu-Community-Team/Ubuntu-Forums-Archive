---
title: "mplayer won't install!"
date: 2005-05-03
forum: Installation &amp; Upgrades
---

### Post by GazaM on 2005-05-03
I was running through the ubuntuguide yesterday trying to get everything that I wanted installed on my computer, but when I came to install mplayer (after I had w32codecs installed etc.) it came up with this error message:

> **Could not mark all packages for installation or upgrade** 
The following packages have unresolvable dependencies. Make sure that all required repositories are added and enabled in the preferences.

mplayer-386:
 Depends: libavcodeccvs but it is not going to be installed
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libfontconfig1 (>=2.3.0) but 2.2.3-4ubuntu7 is to be installed
 Depends: libpostproc0 but it is not going to be installed
  Depends: libvorbis0a (>=1.1.0) but 1.0.1-1 is to be installed
 Depends: libxvidcore4 but it is not going to be installed
 Depends: xmms but it is not going to be installed

I then checked that the repositories were set correctly and sure enough they were all there. But when I clicked OK to get out of the repository list it started to update package list as usual but the following error came up towards the end:

> The Following Problems Were Found On Your System:

W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907


I'm assuming the problems are linked and I would be greatful of any help with this issue.

---

### Post by Poul on 2005-05-03
i get same error message (first one) although i do not get the one about missing keys.

---

### Post by cutOff on 2005-05-03
Did you see this??

[http://ubuntuguide.org/#mplayer](http://ubuntuguide.org/#mplayer)

---

### Post by RyaninZion on 2005-05-03
I am assuming he did see that, as he clearly stated "I was running through the ubuntuguide."

I am also getting the same errors (first set) when trying to install mplayer as per the instructions in the ubuntuguide.

---

### Post by GazaM on 2005-05-03
[QUOTE=RyaninZion]I am assuming he did see that, as he clearly stated "I was running through the ubuntuguide."

I am also getting the same errors (first set) when trying to install mplayer as per the instructions in the ubuntuguide.[/QUOTE]
 RyaninZion the second set of errors doesn't come up when I try to install mplayer they come up when i exit the repository setup and it's trying to update the packages lists, I put those errors in as I thought they may be related to the problem in some way. The first set of errors are the ones I get when I try to install MPlayer as do you. Does anybody have any ideas on how to fix this problem? I'm assuming they didn't put MPlayer in the repository unless it would work!

---

### Post by cutOff on 2005-05-03
[QUOTE=RyaninZion]I am assuming he did see that, as he clearly stated "I was running through the ubuntuguide."

I am also getting the same errors (first set) when trying to install mplayer as per the instructions in the ubuntuguide.[/QUOTE]
As it is said in the guide, you need to do:

```
sudo apt-get -t hoary install mplayer-386
sudo apt-get -t hoary install mplayer-fonts
sudo apt-get -t hoary install mozilla-mplayer
```
You shouldn't use Synaptic to do this.

---

### Post by cutOff on 2005-05-03
To fix the second stage of errors:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
```

---

### Post by GazaM on 2005-05-03
[QUOTE=cutOff]To fix the second stage of errors:
```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
```[/QUOTE]
 Thanks cutOff, both pieces of advice worked perfectly!

---

### Post by GazaM on 2005-05-03
cutOff, your tips helped me install mplayer and get rid of the errors, but now that I check it mplayer keeps freezing up when I try to play anything in it, as does XMMS, and the ubuntu update manager says that libxvidcore4 (or something like that) and mplayer-386 have updates available, but I can't install them because of the same dependency issues as before!! Any ideas?

---

### Post by Majlo on 2005-05-03
I have the same problem.

---

### Post by addfritzie on 2005-05-03
I guess i have the same problem too. Please provide some help

---

### Post by cutOff on 2005-05-03
you must install the package which corresponds to your machine architecture. Uninstall mplayer-386 and choose that one that you need. 

To see the other ones.
```
$ sudo apt-cache search mplayer
```

---

### Post by RyaninZion on 2005-05-04
But I get the same error whether I use Synaptic or apt-get from the command line.  And I have tried installing both the 386 and 586 architectures.  Always the same dependency issue first pointed out by GazaM.

---

### Post by cutOff on 2005-05-04
[QUOTE=RyaninZion]But I get the same error whether I use Synaptic or apt-get from the command line.  And I have tried installing both the 386 and 586 architectures.  Always the same dependency issue first pointed out by GazaM.[/QUOTE]
Paste your sources.list please to take a look.

---

### Post by RyaninZion on 2005-05-04
Hi cutOff, here is my sources.list file:

```

## deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://backports.ubuntuforums.org/backports hoary-backports main universe multiverse restricted
deb http://backports.ubuntuforums.org/backports hoary-extras main universe multiverse restricted

deb ftp://ftp.nerim.net/debian-marillat stable main
deb ftp://ftp.nerim.net/debian-marillat unstable main
deb ftp://ftp.nerim.net/debian-marillat testing main

``` 

Thanks for your help.

---

### Post by cutOff on 2005-05-04
Ok you should remove the second line and add the following instead:

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
```

---

### Post by arnieboy on 2005-05-04
[QUOTE=GazaM]cutOff, your tips helped me install mplayer and get rid of the errors, but now that I check it mplayer keeps freezing up when I try to play anything in it, as does XMMS, and the ubuntu update manager says that libxvidcore4 (or something like that) and mplayer-386 have updates available, but I can't install them because of the same dependency issues as before!! Any ideas?[/QUOTE]

uninstall mplayer with apt-get and follow my instructions to install mplayer from source on  [http://ubuntuforums.org/showthread.php?t=31061](http://ubuntuforums.org/showthread.php?t=31061)

---

### Post by RyaninZion on 2005-05-05
[QUOTE=cutOff]Ok you should remove the second line and add the following instead:

```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted
```[/QUOTE]

Thanks, cutOff.  That did the trick for me.  My mistake for not following the instructions closely enough and making sure my repository list was correct.

---

### Post by addfritzie on 2005-05-05
As I am still really new to this stuff one question: I can't find the uninstall apt-get commando anywhere. How do I uninstall my Mplayer?

---

### Post by Hieronymus on 2005-05-05
[QUOTE=addfritzie]As I am still really new to this stuff one question: I can't find the uninstall apt-get commando anywhere. How do I uninstall my Mplayer?[/QUOTE]

```

apt-cache search mplayer (to find the correct name of the mplayer package)
apt-get remove mplayer (for mplayer fill out the name of the package you just found. 

```

you can also use System >> Administration >> Synaptic Package Manager, search for mplayer, select package for removal and apply.

Good luck

---

### Post by addfritzie on 2005-05-05
Thanks, everyday i'm learning. I've got everything running now!

---

### Post by cutOff on 2005-05-05
Yoy will get more info about commands by running

$ man <command>

---

### Post by darranz on 2005-05-05
I have read the guide and this thread and the problem remains the same for me (mplayer frozen, update error). I've tried 386, 586 and k6-k7 (mine is k7). Here is my sources.list. Thanks


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Major bug fix updates produced after the final release of the
## distribution.
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

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

---

### Post by arnieboy on 2005-05-05
try and install it from source as pointed out in my post:
[http://www.ubuntuforums.org/showthread.php?t=31061](http://www.ubuntuforums.org/showthread.php?t=31061)
this will do the trick for you.

---

