---
title: "error upgrading from 7.04 to 7.10 using update manager: failed to fetch"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by mitchelljj on 2007-10-19
Hi,

I get an error when upgrading from 7.04 to 7.10 using update manager:

The error screen says: A problem occured during update.  This is usually some sort of network problem, please check your network connection and try again.:

Then within the window I get the following identical error showing up twice:
failed to fetch [http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/packages.bz2](http://archive.canonical.com/ubuntu/dists/feisty-commercial/main/binary-i386/packages.bz2) sub-process bzip2 returned an erros code

Note: I have tried the upgrade at least 5 times and each time it errors off at the same point even after it fetches a lot of files before this error.

I have attached the error screen

Thanks,

John

---

### Post by magnolia fan on 2007-10-25
I get the same error.  Anyone have any advice?

---

### Post by rebrain on 2007-10-29
Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'
- This is the message I get from Update manager whilte trying to upgrade to 7.10
Anyone has this kind of problem? I will appreciate any help
I tried to upgrade through graphical interface in UpdateManager and also through the console, it shows the same error.

---

### Post by redebord on 2007-10-29
I got the same error when running the upgrade from the update manager.  I removed WINE and then attempted the upgrade again.  No go...same error.  It looks like there is a communication error to the wine server?  Any assistance would be greatly appreciated.  Thanks in advance.

---

### Post by balcis on 2007-10-30
you must edit your sources.list by
```
sudo gedit /etc/apt/sources.list
```
and add a # sign to the lines in the error. may be, you know it just ignores the lines with # to look for updates..

---

### Post by voturin on 2007-10-30
I has the same problem.

During check update in update manager:

Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)


During upgrade to 7.10:

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.


Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


To use # in  /etc/apt/sources.list  don't help...

---

