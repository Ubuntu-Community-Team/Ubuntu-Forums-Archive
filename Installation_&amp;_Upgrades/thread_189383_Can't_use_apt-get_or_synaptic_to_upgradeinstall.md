---
title: "Can't use apt-get or synaptic to upgrade/install"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by d1zzy on 2006-06-05
Hi All

Every time I try to use Synaptic or apt-get to install or upgrade packages, I get an error about the server sending an invalid reply header :-k .

I can use wget to download the packages individually (aargh!) and my net connection's fine. I had a previous release of Ubuntu installed on the same machine, same network, that I could use synaptic/apt-get OK -- I just Don't Get It! :( Nothing appears to be different except for the fact that it's a new installation.

EDIT: I was able to run apt-get update whilst booted into the installation disk...

Any ideas out there?

Cheers

---

### Post by markh on 2006-06-05
Are you running a standard sources.lst, and could you post all the output from an apt-get update?

---

### Post by d1zzy on 2006-06-05
My sources.list is right off the disk, no modifications or anything:

```
deb http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ dapper-backports main restricted
universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe

```

Doing an apt-get update results in:

```
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Ign http://gb.archive.ubuntu.com dapper Release
Ign http://gb.archive.ubuntu.com dapper-updates Release
Ign http://gb.archive.ubuntu.com dapper/main Packages
Ign http://gb.archive.ubuntu.com dapper/restricted Packages
Ign http://gb.archive.ubuntu.com dapper/main Sources
Ign http://gb.archive.ubuntu.com dapper/restricted Sources
Ign http://gb.archive.ubuntu.com dapper-updates/main Packages
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Packages
Ign http://gb.archive.ubuntu.com dapper-updates/main Sources
Ign http://gb.archive.ubuntu.com dapper-updates/restricted Sources
Errhttp://gb.archive.ubuntu.com dapper/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Packages
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Sources
  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.7 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  The HTTP server sent an invalid reply header [IP: 85.133.25.8 80]
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by markh on 2006-06-05
Can you try temporarily changing gb.archive.ubuntu.com to archive.ubuntu.com and see if that syncs any better?

---

### Post by d1zzy on 2006-06-05
Yes, tried this too, same problem :(

---

### Post by markh on 2006-06-05
Hmm...Can you try ftp rather than HTTP? Maybe you have a proxy somewhere?

---

### Post by d1zzy on 2006-06-05
Well now I'm confused... but thanks! =D> 

Yes, changing the sources to ftp did work, but why can I download the packages from the same locations via http with wget?

---

### Post by markh on 2006-06-06
Hmm...you don't have a proxy entry in /etc/apt.apt.conf, do you?

---

### Post by d1zzy on 2006-06-06
[QUOTE=markh]Hmm...you don't have a proxy entry in /etc/apt.apt.conf, do you?[/QUOTE]

Mine says:
```
Acquire::http::Proxy "false";
```

So I commented that, then edited sources.list to restore the links' protocols back to http, followed by a sudo apt-get update, and it all works! :)

I wonder why (presumably) the installer put the setting in there in the first place? :-k 
From the apt.conf manual page, "false" doesn't look like a valid value for that setting, perhaps an installer script returned an unexpected value?

Thanks again,

---

### Post by ubuntu_demon on 2006-06-06
Maybe you can find out more by trying some tips as described here :
[http://www.ubuntuforums.org/showthread.php?t=188425](http://www.ubuntuforums.org/showthread.php?t=188425)

Post the errors you get. (Don't bother to change /etc/hosts if it looks good.)

Just in case : check for broken dependencies. Use this guide :
[http://www.ubuntuforums.org/showthread.php?t=186672](http://www.ubuntuforums.org/showthread.php?t=186672)

---

