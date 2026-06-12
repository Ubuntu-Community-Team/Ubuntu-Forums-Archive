---
title: "NO PUBKEY The following signatures couldn 't be verified"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by cccc on 2006-10-14
hi

during apt-get update I have the following problem:```

W: GPG error: http://packages.freecontrib.org dapper Release: The following sign atures couldn't be verified because the public key is not available: NO_PUBKEY F 120156012B83718
W: GPG error: http://deb.opera.com etch Release: The following signatures couldn 't be verified because the public key is not available: NO_PUBKEY 033431536A4237 91
W: You may want to run apt-get update to correct these problems

```
meine /etc/apt/sources.list
```

# cat /etc/apt/sources.list

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
#deb http://mirror3.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
#deb-src http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
deb http://packages.freecontrib.org/plf/ dapper free non-free

# Penguin Liberation Front (sources)
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
#deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
#deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

## kadu
deb http://www.kadu.net/download/binary/ubuntu/repo dapper main

## skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main

ubuntu@ubuntu:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://ch.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://ch.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Seveas' packages (packages, GPG key: 1135D466)
#deb http://mirror3.ubuntulinux.nl dapper-seveas all

# Seveas' packages (sources, GPG key: 1135D466)
#deb-src http://seveas.theplayboymansion.net/seveas dapper-seveas all

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
#deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
#deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
#deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
deb http://packages.freecontrib.org/plf/ dapper free non-free

# Penguin Liberation Front (sources)
#deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free
deb-src http://packages.freecontrib.org/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

# Bazaar-NG development (packages, GPG key: 1F44842D)
#deb http://people.ubuntu.com/~jbailey/snapshot/bzr ./

# Bazaar-NG development (sources, GPG key: 1F44842D)
#deb-src http://people.ubuntu.com/~jbailey/snapshot/bzr ./

## kadu
deb http://www.kadu.net/download/binary/ubuntu/repo dapper main

## skype
deb http://download.skype.com/linux/repos/debian/ stable non-free

## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.)
deb http://archive.canonical.com/ubuntu dapper-commercial main
```

---

### Post by Kateikyoushi on 2006-10-14
Executing these lines from terminal should fix the first one, replace the key to match the one opera uses and execute again.

```
gpg --keyserver subkeys.pgp.net --recv F120156012B83718
gpg --export --armor F120156012B83718 | sudo apt-key add -
```

---

### Post by cccc on 2006-10-14
thanks a lot !

this fixed this problem.

---

### Post by brash on 2006-10-21
Thanks very much, those two lines fixed the same problem that I had been struggling with :)

---

### Post by pirxx on 2008-02-07
Shanghei greets Tokyo and thanks for the fix.

---

