---
title: "Kubuntu-desktop installation problem"
date: 2007-09-10
forum: Installation &amp; Upgrades
---

### Post by anator on 2007-09-10
I have just installed ubuntu feisty fawn in a hp laptop (new) with vista. I am unable to install kubuntu using the command 

sudo apt-get install kubuntu-desktop

It shows the following error

-------------------------------------------------------------

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "kubuntu-desktop"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly cinstalled, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

-------------------------------------------------------------

I have tried including everything beryll,dapper in the source list but it won't work. Right now my source list is the following

[PHP]
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
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

# Kubuntu.org bleeding edge KDE
# GPG key: DD4D5088
deb http://kubuntu.org/packages/kde-latest feisty main 

# Kubuntu.org bleeding edge Koffice
# GPG key: DD4D5088
deb http://kubuntu.org/packages/koffice-latest feisty main 

# Canonical Commercial packages
# GPG key: 437D05B5
deb http://archive.canonical.com feisty-commercial main 

[/PHP]


Can someone help me in installing kubuntu. Also when I searched for "kubuntu-desktop" in synaptic it was not there.

Please help.

---

### Post by maybeway36 on 2007-09-10
1st thing: try ```
sudo apt-get update
```

---

### Post by strabes on 2007-09-10
PLEASE use aptitude when installing meta packages like kubuntu-desktop. It will make removal FAR easier. Run this:```
sudo aptitude update && sudo aptitude install kubuntu-desktop
```

---

### Post by anator on 2007-09-10
Thanks for ur comments

@maybeway36
I have tried the update still won't work

Even the sudo aptitude update && sudo aptitude install kubuntu-desktop produces the same problem.

However I observed the following when I took an update. In the console I get

-------------------------------------------------------------------------

Hit [http://kubuntu.org](http://kubuntu.org) feisty/main Packages                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release             
Ign [http://kubuntu.org](http://kubuntu.org) feisty/main Packages                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages[B]
Err [http://kubuntu.org](http://kubuntu.org) feisty/main Packages
  404 Not Found[/B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages

---------------------------------------------------------------------------


Is the highlighted entry the problem?

Please help me out here.

---

### Post by anator on 2007-09-10
I have got a new source list from here
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

Still the problem won't go:confused:

I want to avoid downloading the kubuntu dvd but that seems to be the only option.

I saw one more entry with the same problem but no resolution. So if anyone out there knows about this please post ur thoughts and/or solutions.

---

