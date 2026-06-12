---
title: "Build Essential Install [Resolved]"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by anarchy305 on 2007-03-03
I am getting a bit frustrated with this, if anyone has any solutions then please let me know.

I am trying to build essential by typeing the below command for ubuntu Edgy:

sudo apt-get install build-essential

But get this error:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that the package is simply not installable and a bug report against that package should be filed. The following information may help to resolve the situation:

The following packages have unmet dependencies:
build-essential: 

Depends: libc6-dev but it is not going to be installed or libc-dev
                   
Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

So then I went off to [http://packages.ubuntu.com/edgy/allpackages](http://packages.ubuntu.com/edgy/allpackages) and downloaded:

libc6_2.4-1ubuntu12_i386.deb
libc6-dev_2.4-1ubuntu12_i386.deb
g++_4.1.1-6ubuntu3_i386.deb

And installed each one of them using the "package installer" and got the below messages for each one.

libc6_2.4-1ubuntu12_i386.deb "Error: A later version is already installed"
libc6-dev_2.4-1ubuntu12_i386.deb "Error: Dependency is not satisfiable: libc6"
g++_4.1.1-6ubuntu3_i386.deb "Error: cannot install 'g++-4.1"

I am using the below repositores which I obtained from [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy main restricted 
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy main restricted
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy universe multiverse 
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy universe multiverse
deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all 

deb-src [http://seveas.imbrandon.com](http://seveas.imbrandon.com) edgy-seveas all

# Ubuntu backports project
# GPG key: 437D05B5
deb [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse 

deb-src [http://jp.archive.ubuntu.com/ubuntu](http://jp.archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main 

deb-src [http://archive.canonical.com](http://archive.canonical.com) edgy-commercial main

Also I had a go at easyubuntu recommended by this post [http://ubuntuforums.org/showthread.php?t=372731&highlight=libc6-dev](http://ubuntuforums.org/showthread.php?t=372731&highlight=libc6-dev)

But still came out empty handed :(

Please help me get this sorted out.

Thanks

---

### Post by taurus on 2007-03-03
Try

```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by anarchy305 on 2007-03-03
Thanks for the quick reply.

Your solution did the trick :)

Thanks again.

---

### Post by jackobean on 2007-04-09
I have a similar problem, but the above resolution does not fix. Also running edgy, my outpu looks like this

```
jack@jack:/etc/apt$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```
and my sources list is
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu edgy main restricted 
deb http://au.archive.ubuntu.com/ubuntu edgy-updates main restricted
deb http://security.ubuntu.com/ubuntu edgy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu edgy universe multiverse 
deb http://au.archive.ubuntu.com/ubuntu edgy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu edgy-security universe multiverse

# Seveas' Ubuntu Packages
# GPG key: 1135D466
deb http://mirror2.ubuntulinux.nl/ edgy-seveas all 

# Ubuntu backports project
# GPG key: 437D05B5
deb http://au.archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse 

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb http://kubuntu.org/packages/kde-latest edgy main 

```
my reasons for doing this is because for some reason gcc is returning errors that headers are non existent.
```
gcc -g -O0   -c -o cpusched.o cpusched.c
cpusched.c:11:22: error: stdio.h: No such file or directory
cpusched.c:12:23: error: stdlib.h: No such file or directory
cpusched.c:13:23: error: string.h: No such file or directory
```

what to do?

---

