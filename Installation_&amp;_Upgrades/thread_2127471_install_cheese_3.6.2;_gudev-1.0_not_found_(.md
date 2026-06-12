---
title: "install cheese 3.6.2; gudev-1.0 not found :("
date: 2013-03-20
forum: Installation &amp; Upgrades
---

### Post by hillberry on 2013-03-20
hi! so i've been trying to install cheese 3.6.2 on ubuntu 12.04 32-bit and i've worked around everything else except now whenever i hit ./configure on the package, it always always ends like this: 

*checking for gudev-1.0... configure: error: gudev-1.0 not found*

so when i try putting "sudo apt-get install gudev-1.0" i get this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'gir1.2-gudev-1.0' for regex 'gudev-1.0'
Note, selecting 'libgudev-1.0-0' for regex 'gudev-1.0'
Note, selecting 'libgudev-1.0-dev' for regex 'gudev-1.0'
Note, selecting 'gir1.0-gudev-1.0' for regex 'gudev-1.0'
gir1.2-gudev-1.0 is already the newest version.
libgudev-1.0-0 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgudev-1.0-dev : Depends: libglib2.0-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

and when i try "sudo apt-get install libgudev-1.0-dev" this happens:

```
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgudev-1.0-dev : Depends: libglib2.0-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

i am really lost :( what do i do now?

---

### Post by varunendra on 2013-03-20
Welcome to the forums hillberry! :)

Usually such errors mean that the software list is outdated and the ones it is looking for no longer exist in the repositories. Please try -
```
sudo apt-get update
sudo apt-get dist-upgrade
```
Then retry installing cheese from the repositories.

---

