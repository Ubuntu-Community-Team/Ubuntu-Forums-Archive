---
title: "Problem updating ubuntu"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by andymic on 2008-08-11
Hi all, I could use some help with updating.

Background:

My server is running in hosting centre who offer a number of LINUX distro's.
For Ubuntu they only offer 6.06 LTS which has been imaged on to my server.
My connection is SSH via PuTTY and WinSCP

Problem:

I am attepting to upgrade to 8.04 following this document [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

I have carried out the following steps:

enable the "dapper-updates" repository 

install the new "update-manager-core" package - dependencies include python-apt, python-gnupginterface and python2.4-apt. 

run "do-release-upgrade -d" in a terminal window

The repository I added was:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted

after which I did an update

when I run the do-release-upgrade -d I get the following errors:

Error during update

A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.

W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/binary-i386/Packages.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)
Hash Sum mismatch
, W:Failed to fetch
[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2)
Hash Sum mismatch
, E:Some index files failed to download, they have been ignored, or
old ones used instead.


Restoring original system state

Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done

Anybody have any idea of what's going on??

Thanks

Andy

---

### Post by Super-Fly on 2008-08-11
I had the same problem just last Friday (kept me in the office until 9:00pm trying to fix it). From what I can see it seems that 8.04 was moved from development to the regular repository. The -d at the end of "do-release-upgrade -d" tells the upgrade to pull from the development directory, which appears to be trying to pull 8.10, not 8.04 anymore. I haven't had a chance to test it yet, but supposedly if you remove the -d, it should update fine now. Someone please correct me if I'm wrong.

---

### Post by Super-Fly on 2008-08-11
I tested updating without the '-d' on a spare box, and it seems to work fine that way. The version, according to lsb-release is reporting as 8.04.1, which I hope is the right version.

---

### Post by andymic on 2008-08-11
Superfly.

Thanks for that.  I think you're right

I did the upgrade without the -d and I've got a bit further.

I still have an error though (see below)

Invalid package information

After your package information was updated the essential package
'ubuntu-standard' can not be found anymore.
This indicates a serious error, please report this bug against the
'update-manager' package and include the files in
/var/log/dist-upgrade/ in the bugreport.


Restoring original system state

Aborting
Reading package lists: Done
Building dependency tree: Done
Building dependency tree: Done
Building dependency tree: Done


Can anyone offer any insight into this?

---

### Post by andymic on 2008-08-12
FYI

This is now a confirmed bug in Launchpad

---

