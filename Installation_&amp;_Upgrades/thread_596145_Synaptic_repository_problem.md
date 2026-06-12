---
title: "Synaptic repository problem"
date: 2007-10-29
forum: Installation &amp; Upgrades
---

### Post by aldav on 2007-10-29
I have been using Gutsy with no problem until now. The problem appeared trying to acquire packages from the repository. Synaptic reports the following error:

----------------------------------------------
**Could not download all repository indexes**

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz:) 503 Service Unavailable
[http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz:) 503 Service Unavailable
[http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 503 Service Unavailable
[http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 503 Service Unavailable

Any clues????

---

### Post by taurus on 2007-10-29
Maybe you want to edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and comment out those repos, [http://ubuntu.prod.uci.cu/ubuntu/](http://ubuntu.prod.uci.cu/ubuntu/), by placing a # in front of them.  Save it and then run

```
sudo apt-get update
sudo apt-get upgrade
```
Otherwise, post your /etc/apt/sources.list here.

```
cat /etc/apt/sources.list
```

---

### Post by aldav on 2007-10-29
Those are the only repositories I can access, because Internet account is limited to 150mb a month, so I can only access local repositories.
This is my sources.list

**sources.list**
------------------------------------------------------------------------------------------------------------
## Major bug fix updates produced after the final release of the
## distribution.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty universe
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cu.archive.ubuntu.com/ubuntu/](http://cu.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ubuntu.prod.uci.cu/ubuntu/](http://ubuntu.prod.uci.cu/ubuntu/) gutsy main restricted universe multiverse

------------------------------------------------------------------------------------------------------------

When I typed "sudo apt-get update" on the console this is what I get:

---------------------------------------------------------------------------------------------------
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty Release.gpg
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/main Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/restricted Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/universe Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/multiverse Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy Release.gpg
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/main Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/restricted Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/universe Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/multiverse Translation-en_US
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty Release
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy Release
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/main Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/restricted Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/universe Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/multiverse Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/main Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/restricted Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/universe Packages
Ign [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/multiverse Packages
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/main Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/restricted Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/universe Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) feisty/multiverse Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/main Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/restricted Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/universe Packages
  407 Proxy Authentication Required
Err [http://ubuntu.prod.uci.cu](http://ubuntu.prod.uci.cu) gutsy/multiverse Packages
  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/main/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/universe/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/main/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/restricted/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz)  407 Proxy Authentication Required
Failed to fetch [http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz](http://ubuntu.prod.uci.cu/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz)  407 Proxy Authentication Required
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
---------------------------------------------------------------------------------------------------

I am behind a proxy, but everything worked fine hours before and I don't recall doing any changes in the Network Configuration.

---

### Post by aldav on 2007-10-29
Problem solved. Looks like I configured Synaptic to connect to the internet through the proxy, but the local repository does not requires one, so I changed it back to "Direct Connection to The Internet"

Thanks for the help anyway

---

