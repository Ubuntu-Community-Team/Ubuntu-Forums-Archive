---
title: "Trying Again...Dapper Won't Upgrade"
date: 2006-11-21
forum: Installation &amp; Upgrades
---

### Post by mormonchess on 2006-11-21
Ok, let's try this again....

My Update Manager won't let me upgrade to Edgy.

Here is the error message:

"Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry."

And below it:

"Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)"



Ok, so could someone please share with me how to fix this problem?

---

### Post by mormonchess on 2006-11-21
I'm also getting this error message:

"W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718"



Does Linux really have to be baby-sat in order to keep it running optimally?:mad:

---

### Post by taurus on 2006-11-21
I would remove those repos from your /etc/apt/sources.list for now.  Just place a # in front of them...  Once everything is up and running, then put them back in by removing the # sign.

---

### Post by mormonchess on 2006-11-21
Ok.....I have no idea what you mean by "repos"...and I have no idea how to edit the list.

It won't even let me save the edited file.  

Ubuntu / Linux is way too frustrating.  I like it, and want it to work, but I feel that you have to take a special course just know how to use it.

---

### Post by taurus on 2006-11-21
Open a terminal, Applications -> Accessories -> Terminal, and type

```
gksudo gedit /etc/apt/sources.list
```
If you don't important stuff on your Dapper, why not do a fresh install of Edgy.  Fast and simple...  And if you have important on Dapper, back it up first!

---

### Post by mormonchess on 2006-11-21
Ok, well here is the fun error message I get when I follow your direction:



"~$ gksudo gedit /etc/apt/sources.list
(gedit:22185): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
"

---

### Post by FireWater on 2006-11-21
After installing Dapper, i decided to try Edgy.  I downloaded the Edgy CD (xubuntu-6.10-desktop-powerpc.iso) and installed it.  I used the /cdrom/cdromupgrade option to upgrade to Edgy and i get the error

Failed to add the cd
E:sub-process gpgv returned an error code (2), w: Signature verification failed for :/cdrom/dist/edgy/release.gpg

i tried burning the iso again this time @ 10x with the same results.  I downloaded the iso again... same story


imac g3 450 mhz

---

