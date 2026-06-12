---
title: "Apt upgrade fails"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by myrdrahl on 2020-10-22
I got help earlier figuring out that my HDD was failing. So I cloned the drive and booted the system with the new drive. dmesg(that previously had loads of errors) now looks clean. However, I still cannot upgrade the packages with apt. I mean, it throws the very helpful error "bad message". I've tried this:

1. sudo apt install -f (this throw the same error)

```

sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following additional packages will be installed:
  linux-headers-5.4.0-52 linux-headers-5.4.0-52-generic linux-headers-generic linux-image-5.4.0-52-generic linux-image-generic
  linux-modules-5.4.0-52-generic linux-modules-extra-5.4.0-52-generic
Suggested packages:
  fdutils linux-doc | linux-source-5.4.0 linux-tools
The following packages will be REMOVED:
  linux-headers-4.15.0-43
The following NEW packages will be installed:
  linux-generic linux-headers-5.4.0-52 linux-headers-5.4.0-52-generic linux-headers-generic linux-image-5.4.0-52-generic
  linux-modules-5.4.0-52-generic linux-modules-extra-5.4.0-52-generic
The following packages will be upgraded:
  linux-image-generic
1 upgraded, 7 newly installed, 1 to remove and 557 not upgraded.
1 not fully installed or removed.
Need to get 0 B/74.2 MB of archives.
After this operation, 283 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 83639 files and directories currently installed.)
Removing linux-headers-4.15.0-43 (4.15.0-43.46) ...
dpkg: error processing package linux-headers-4.15.0-43 (--remove):
 unable to securely remove '/usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi/Makefile.dpkg-tmp': Bad message
Errors were encountered while processing:
 linux-headers-4.15.0-43

```

So, am I still lost, because there were some corrupted sectors on the old drive? It's quite frustrating, since the system seem to be running just fine.

---

### Post by Frogs Hair on 2020-10-22
> 1 upgraded, 7 newly installed, 1 to remove and 557 not upgraded.

It looks like you have many updates not installed. What's the output of the following?  ```
sudo apt update && sudo apt upgrade
```

---

### Post by myrdrahl on 2020-10-22
Oh, yes there are lots of uninstalled packages, which is part of problem I guess. I can't seem to get rid of that linux-headers-4.15.0.43(which is an old kernel or something, right?). I'm guessing it's related to the borked sectors on the old drive. 

Apart from listing all the packages, it outputs this:

551 upgraded, 120 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
Need to get 0 B/360 MB of archives.
After this operation, 607 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 83639 files and directories currently installed.)
Removing linux-headers-4.15.0-43 (4.15.0-43.46) ...
dpkg: error processing package linux-headers-4.15.0-43 (--remove):
 unable to securely remove '/usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi/Makefile.dpkg-tmp': Bad message
Errors were encountered while processing:
 linux-headers-4.15.0-43
E: Sub-process /usr/bin/dpkg returned an error code (1)

Then thought I could perhaps reinstall that which seems to be broken:
$ sudo apt install linux-headers-4.15.0-43-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package linux-headers-4.15.0-43-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package 'linux-headers-4.15.0-43-generic' has no installation candidate

This might be relevant?
$uname -r
4.15.0-122-generic

---

### Post by ActionParsnip on 2020-10-22
Could try:
```

sudo mv /usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi/Makefile.dpkg-tmp ~/Makefile.dpkg-tmp
sudo apt-get --purge autoremove

```

if this doesn't work simply reverse the command and move it back in

HTH

---

### Post by ActionParsnip on 2020-10-22
I also found this which shows a similar issue
[https://askubuntu.com/questions/490844/unable-to-securely-remove-lib-modules-3-11-0-13-generic-build-not-a-directo](https://askubuntu.com/questions/490844/unable-to-securely-remove-lib-modules-3-11-0-13-generic-build-not-a-directo)

---

### Post by grahammechanical on 2020-10-22
Go to /usr/src and see if you have a folder for linux-headers-4.15.0-43. If you have that folder go to /drivers/pnp/pnpacpi and see if it has a Makefile. On my system the Makefile is not Makefile.dpkg-tmp. Just Makefile.

On an up-to-date Ubuntu 20.04 we should have two 5.4 Linux kernels. The 4.15 is no longer needed. It may have been removed from the 20.04 repositories. That would explain why you cannot re-install it.

Regards

---

### Post by myrdrahl on 2020-10-23
Thanks for your input! I've done some testing:

sudo mv /usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi/Makefile.dpkg-tmp ~/Makefile.dpkg-tmp
mv: cannot stat '/usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi/Makefile.dpkg-tmp': Bad message

That's unfortunate, so I tried this:
/usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi$ ls -l
ls: reading directory '.': Bad message
total 0

Maybe I can trick it into thinking there is a file there?
/usr/src/linux-headers-4.15.0-43/drivers/pnp/pnpacpi$ touch Makefile.dpkg-tmp
touch: cannot touch 'Makefile.dpkg-tmp': Bad message
Guess not! 

Upgrading  to 20.04 is what I'm trying to do, but it wont let me, because of this  issue. I can't seem to be able to forcefully install that package,  because it's been deprecated(obviously because it's so old). Beginning  to think that the only solution is to reinstall the system, but was  hoping there was a way around this.

---

