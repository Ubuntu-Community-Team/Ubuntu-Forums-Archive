---
title: "Upgrading from Ubuntu 6.06 to 6.10"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by tjl30 on 2007-03-25
Well I wanted to upgrade my ubuntu 6.06 to ubuntu 6.10 but I got the following error

```

W: GPG error: http://www.debian-multimedia.org sid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907

```

then I got this 

```

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/source/Sources.bz2 Sub-process bzip2 returned an error code (2)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/source/Sources.bz2 Sub-process bzip2 returned an error code (2)

```

Then I changed my /etc/apt/sources.list to this:

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
deb http://us.archive.ubuntu.com/ubuntu dapper main restricted 
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu dapper universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

```

Then tried to upgrade again, this time I got another error

```

Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.bz2 Sub-process bzip2 returned an error code (2)

```

---

### Post by Matt Yun on 2007-03-25
1.  Don't use the Marillat ([http://www.debian-multimedia.org](http://www.debian-multimedia.org)) repositories with Ubuntu.  Marillat is intended for Debian, and although most of those packages should work with Ubuntu, you will undoubtedly encounter package conflicts by trying to mix it in.  Otherwise, if you really, really want Marillat, follow the directions on the [FAQ on adding their GPG signature]("http://www.debian-multimedia.org/faq.html") to your system.

2.  Whenever you change your /etc/apt/sources.list file, you must run **apt-get update** before doing anything else.  The error message you got 'Failed to fetch http://security.ubuntu.com/ubuntu/dists/edgy-security...', after you had changed all of your sources to the dapper repos, suggests that you didn't run apt-get update first.

3.  I don't think that you can upgrade to Edgy, then downgrade to Dapper again, at least not without a lot of problems.  Try changing your sources.list entries back to Edgy (comment out the non-Ubuntu repos for now), then run apt-get update && apt-get dist-upgrade.

---

### Post by zvacet on 2007-03-25
gpg --keyserver hkp://subkeys.pgp.net --recv-keys 07DC563D1F41B907
gpg --export --armor 07DC563D1F41B907  | sudo apt-key add -

```
sudo aptitude update
```
```
sudo aptitude upgrade
```


```
gksu "update-manager -c" 
```

---

### Post by tjl30 on 2007-03-25
O thanks, I edited my sources.list but for got to use sudo apt-get update. I now have Ubuntu/Kubuntu 6.10!

---

### Post by mattbuntu on 2007-03-26
ZVACET you are awesome... you just solved a problem that had 
 been irking me forever.  Listen to this man and his replies.  LOL.

 -Dapper as ever

---

