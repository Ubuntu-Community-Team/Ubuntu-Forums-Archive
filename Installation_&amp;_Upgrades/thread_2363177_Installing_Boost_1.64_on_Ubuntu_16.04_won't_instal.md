---
title: "Installing Boost 1.64 on Ubuntu 16.04 won't install Boost above 1.58"
date: 2017-06-07
forum: Installation &amp; Upgrades
---

### Post by tomer20014 on 2017-06-07
No matter what I do I can't uninstall boost and reinstall it higher than Boost 1.58. I'm aiming at version 1.64 and I am installing from a tar file I downloaded.

Firstly I uninstall everything like this

```
sudo apt-get --purge remove libboost-dev libboost-doc
sudo apt-get --purge remove libboost-dev
sudo apt-get --purge remove libboost-all-dev
sudo apt autoremove
```

Then I follow these steps

I download the file from here [https://dl.bintray.com/boostorg/release/1.64.0/source/:boost_1_64_0.tar.bz2](https://dl.bintray.com/boostorg/release/1.64.0/source/:boost_1_64_0.tar.bz2)

...then i untar it with

```
tar xvjf boost_1_64_0.tar.bz2
cd boost_1_64_0
```

then I Get the required libraries, main ones are icu for boost::regex support:

```
sudo apt-get update
sudo apt-get install build-essential g++ python-dev autotools-dev libicu-dev build-essential libbz2-dev libboost-all-dev
```

^^^^^ I'm guessing that this line is what makes it install 1.58 instead of the 1.64 version

Then I  do Boost's bootstrap setup:

```
./bootstrap.sh --prefix=/usr/local
```

Then I build it with

```
./b2
```

and eventually install it with

```
sudo ./b2 install 
```

and then when I check the version with 

```
dpkg -s libboost-dev | grep 'Version'
```

it is always 1.58...

---

### Post by steeldriver on 2017-06-07
Yes it is the addition of libboost-all-dev to the installed dependencies that is pulling 1.58 back in

HOWEVER, unless you use something like checkinstall, dpkg will not be aware of software installed from source (it will show it as uninstalled, once you drop libboost-all-dev from the apt-get install command)

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

That's not necessarily a problem - since anything using the boost libraries will have other ways of locating them (pkg-config, cmake etc.)

---

### Post by Efwis on 2017-10-01
sorry to revive this thread, but how would you use checkinstall with a ./b2 install process

---

### Post by arghavanmh on 2018-06-22
I have installed using the method you have mentioned here but i cannot find bootstrap.sh. Do you know the problem?

---

