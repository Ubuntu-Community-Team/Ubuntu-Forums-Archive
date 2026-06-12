---
title: "[SOLVED] How can I install make package onto Ubuntu Server without an internet connec"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by uoirej on 2008-05-20
Hello everyone.

I'm trying Ubuntu Server 8.04 as a possible platform for some intranet tools. Unfortunately, the tool's installer requires **make**, and it is not included by the Server installer by default.

Due to security implications, I'm unable to connect my experimental machine to the internet and download anything directly from any package repository, hence trying to do some kind of "offline" installation.

I've noticed that **make** is present in Ubuntu Desktop installation and tried to use the Desktop CD as a source for **apt-get**. The attempt failed:

```
uoirej@ubuntuserver:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [6c2e1c01c6884ef40fd349693334a953-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
This disc is called:
'Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)'
Copying package lists...gpgv: Signature made Wed 23 Apr 2008 05:03:24 AM MSD using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
Unmounting CD-ROM...
Repeat this process for the rest of the CDs in your set.

uoirej@ubuntuserver:~$ sudo mount /dev/cdrom /cdrom
mount: block device /dev/scd0 is write-protected, mounting read-only

uoirej@ubuntuserver:~$ sudo apt-get install make
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package make is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package make has no installation candidate
```

After a long manual examination of Ubuntu Desktop CD I was not able to find a .deb file for **make** package. However, it _is_ present in the Desktop installation:

```
uoirej@ubuntudesktop:~$ apt-cache showpkg make
Package: make
Versions: 
3.81-3build1 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/dpkg/status
                  MD5: 1428aa1a6d796cd9976fd652a369e702


Reverse Depends: 
  gcc,make
  ubuntu-desktop,make
Dependencies: 
3.81-3build1 - libc6 (2 2.5-0ubuntu1) make-doc (0 (null)) 
Provides: 
3.81-3build1 - 
Reverse Provides: 

```

The Server installation does know about it, but doesn't have it installed:

```
uoirej@ubuntuserver:~$ apt-cache showpkg make
Package: make
Versions:

Reverse Depends:
  dpkg-dev,make
  build-essential,make
Dependencies:
Provides:
Reverse Provides:
```

-----

Ok, so a major question: how can I install **make** onto Ubuntu Server 8.04 machine that does not have an internet connection to access internet repositories?

Two minor questions:

1. Where is **make** located on the Ubuntu Desktop installation CD?

2. What is the generic command sequence for installing packages from a CD? Is **apt-cdrom add** --> **mount** --> **apt-get install <package>** enough, or are there some other implications like specific cdrom mount point name or something?

---

### Post by renzokuken on 2008-05-20
to install make run

```
sudo apt-get install build-essential
```

---

### Post by dstew on 2008-05-20
Without internet access, the best way to install is to use the [nonetdebs]("http://nonetdebs.unixpod.com/") service. You make a text file of your current system status, and copy it to removeable media. Take it to an internet-connected computer, and upload it to nonetdebs. They give you a bunch of links to the packages you need or want to install. Copy the packages to the removeable media, and take it to your no-internet computer. Copy the packages onto the hard drive, and use dpkg to install them.

EDIT: The package you need to install is called **build-essential**. I am not sure it is on the Hardy CD. I know it was not on earlier distributions, you had to get it from the repositories.

---

### Post by zvacet on 2008-05-20
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by uoirej on 2008-05-21
Thanks everyone, it worked with just two commands:

```
sudo apt-cdrom add
sudo apt-get install build-essential
```

And yes, build-essential is present on Hardy Server installation CD.

---

