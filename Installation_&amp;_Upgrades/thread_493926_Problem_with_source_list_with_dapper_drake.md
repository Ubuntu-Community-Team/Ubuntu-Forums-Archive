---
title: "Problem with source list with dapper drake"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by richard5579 on 2007-07-06
Hi I`m actually not new to ubuntu but have a problem with dapper drake my source list is:
```

# Automatically generated sources.list
# http://www.ubuntulinux.nl/source-o-matic
#
# If you get errors about missing keys, lookup the key in this file
# and run these commands (replace KEY with the key number)
#
# gpg --keyserver subkeys.pgp.net --recv KEY
# gpg --export --armor KEY | sudo apt-key add -

# Ubuntu supported packages (packages, GPG key: 437D05B5)
deb http://de.archive.ubuntu.com/ubuntu dapper main restricted
deb http://de.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu supported packages (sources, GPG key: 437D05B5)
deb-src http://de.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://de.archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://de.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://de.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Cipherfunk multimedia packages (packages, GPG key: 33BAC1B3)
deb ftp://cipherfunk.org/pub/packages/ubuntu/ dapper main

# Cipherfunk multimedia packages (sources, GPG key: 33BAC1B3)
deb-src ftp://cipherfunk.org/pub/packages/ubuntu dapper main

# Penguin Liberation Front (packages)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Penguin Liberation Front (sources)
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ dapper free non-free

# Bleeding edge wine packages (packages)
deb http://wine.budgetdedicated.com/apt dapper main

# Bleeding edge wine packages (sources)
deb-src http://wine.budgetdedicated.com/apt dapper main

# The Opera browser (packages)
deb http://deb.opera.com/opera etch non-free

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main


```
but if i want to download something it isn` working with synaptic nor with apt-get
eaven directly afterwards if i tell him to make an apt-get update he ingores or has a problem downloading
can you give me your source lists so i can adapt mine please help
berni

---

### Post by bapoumba on 2007-07-06
Please post the complete output to ```
sudo aptitude update
```
Plf do not maintain ubuntu repos any longer. You can use [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repos instead.

---

