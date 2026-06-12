---
title: "python : Depends: python-minimal"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by alhaines on 2011-01-13
I'm using 10.10 and have started getting this update error!
[SIZE=1]
Could not initialize the package information

An unresolvable problem occurred while initializing the package information.[/SIZE] [SIZE=1]

Please report this bug against the 'update-manager' package and include the following error message:[/SIZE] [SIZE=1]

'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'[/SIZE] 

so I thought I need to fix a broken pkg

sudo dpkg --configure -a
sudo apt-get install -f

no dice!

sudo apt-get install -f
[SIZE=1]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 python : Depends: python-minimal (= 2.6.6-2ubuntu2) but 2.6.6-2ubuntu1 is installed
 python-dev : Depends: python (= 2.6.6-2ubuntu1) but 2.6.6-2ubuntu2 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies[/SIZE]

I try to remove either (python, python-dev) and it wants to remove half my system!

Why is it that in order to make things easier for noobs we have to sacrifice perfection?
:confused::confused:

---

### Post by solar george on 2011-01-13
Try seeing what aptitude -f install does, aptitude is often smarter than apt when dealing with broken packages.

---

### Post by solar george on 2011-01-13
Try seeing what aptitude -f install does, aptitude is often smarter than apt when dealing with broken packages.
EDIT: so apparently the forums are easily confused about if I've posted sucessfully. damm them.

---

### Post by alhaines on 2011-01-15
Thanks for the attempt but I don't like it's solution, 'remove 586 packages"?!?!
It appears that an app I must have installed killed my system.
I mean it runs but I can't update anything because of this conflict.

I just got it running really nice! Three weeks is the longest I've been able to keep Ubuntu 10.xx functional without an update error! 

python is needed by most everything !?! :<

What now?

9.04 worked best but I guess theres no going back now.
 
Why is it that in order to make things easier for noobs we have to sacrifice perfection?

---

### Post by solar george on 2011-01-15
OK it looks to me like you've had an interrupted upgrade of the python packages (they should all be upgraded at once to avoid this kind of situation).
I think the best thing to do now would be to download the packages files (see below) manually (put them all in a new directory with no other debs) the install them with
```
sudo dpkg --force-depends -i *.deb
sudo apt-get -f install
sudo apt-get dist-upgrade
```
I think you'll need the following files (assuming you're using 32bit ubuntu);
[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python-defaults/python-minimal_2.6.6-2ubuntu2_all.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python-defaults/python-minimal_2.6.6-2ubuntu2_all.deb)
[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python2.6/python2.6-minimal_2.6.6-5ubuntu1_i386.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python2.6/python2.6-minimal_2.6.6-5ubuntu1_i386.deb)

---

### Post by alhaines on 2011-01-15
ubuntu-10.10-desktop-amd64

---

### Post by solar george on 2011-01-15
> **alhaines said:**
> ubuntu-10.10-desktop-amd64

in that case the second link should be;
[http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python2.6/python2.6-minimal_2.6.6-5ubuntu1_amd64.deb](http://www.mirrorservice.org/sites/archive.ubuntu.com/ubuntu//pool/main/p/python2.6/python2.6-minimal_2.6.6-5ubuntu1_amd64.deb)


EDIT: wrt your sig you might be interested in [clementine]("apt://clementine") which is meant to be like amarok 1.4 but programmed using newer libraries

---

### Post by dino99 on 2011-01-15
try cleaning the cache first, and deactivate the non trusted sources if any (ppa) into synaptic

sudo rm /var/cache/apt/archives/*

then update upgrade again

---

### Post by solar george on 2011-01-15
> **dino99 said:**
> try cleaning the cache first, and deactivate the non trusted sources if any (ppa) into synaptic

sudo rm /var/cache/apt/archives/*

then update upgrade again

The python versions in question come from the official -updates repo not from any ppa's so the disabling of ppa's shouldn't make any difference.

The correct way to clean the package cache is using apt-get clean.

Apart from that your solution may well work, so long as apt doesn't insist on fixing broken packages before it will do anything else (which IIRC it does) in which case you will manually have to force the installation of one of the broken dependancies (as per my instructions).

---

### Post by alhaines on 2011-01-20
Hate to say it but failure all around!

Thanks for your help but no go for my UB10.10

I pulled 10.10 from system and am back to UB9.10 because it was more stable for me.

good thing I never store any data on /

I have my OS on hd in drive tray, when crash occurs and it always does, I just put in new HD and server back up after reboot!  :>

Now that work has slowed down I guess I'll redo that HD in my sandbox with clean UB 10.10  or maybe UB 11.01 which I hear is beta testing!

Thanks again all!

---

### Post by solar george on 2011-01-20
Good luck, all I can say is that I've never seen that problem before so I think there's a high chance you won't encounter it ever again.

---

