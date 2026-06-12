---
title: "Can't update php to version 5.3.10-1ubuntu3.6 on 12.04"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by lex0r on 2013-06-03
Hi,
I spent hours looking for my problem over internet, trying various solutions but got no result.
In brief, I decided to install php sqlite extension, and found that it depends on php5-common of version 5.3.10-1ubuntu3.6. This version is the latest one available in security/updates areas. Of course I checked the sources and they are fine:

```
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted


deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted


deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu/ precise-security restricted main multiverse universe
```

The proof that package is available for precise is here:
[http://www.ubuntuupdates.org/package/core/precise/main/security/php5](http://www.ubuntuupdates.org/package/core/precise/main/security/php5)

I tried all of the possible apt-get tricks to clear/clean/repair/autoremove/-f etc. that can be easily googled - all in vain.
I'm always getting this:

```
$ sudo apt-get install php5
[sudo] password for lexor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 php5 : Depends: libapache2-mod-php5 (>= 5.3.10-1ubuntu3.6) but 5.3.10-1ubuntu3 is to be installed or
                 libapache2-mod-php5filter (>= 5.3.10-1ubuntu3.6) but it is not going to be installed or
                 php5-cgi (>= 5.3.10-1ubuntu3.6) but it is not going to be installed or
                 php5-fpm (>= 5.3.10-1ubuntu3.6) but it is not going to be installed
        Depends: php5-common (>= 5.3.10-1ubuntu3.6) but 5.3.10-1ubuntu3 is to be installed
E: Unable to correct problems, you have held broken packages.

```
Could anyone hint me at solution, please?

---

### Post by ajgreeny on 2013-06-03
Have a look at [https://launchpad.net/~ondrej/+archive/php5](https://launchpad.net/~ondrej/+archive/php5) which should give you the version you need, in fact even newer than the minimum that you seem to need.  Instructions for how to enable the ppa are at that link.

Good luck.

---

### Post by lex0r on 2013-06-03
> **ajgreeny said:**
> Have a look at [https://launchpad.net/~ondrej/+archive/php5](https://launchpad.net/~ondrej/+archive/php5) which should give you the version you need, in fact even newer than the minimum that you seem to need.  Instructions for how to enable the ppa are at that link.

Good luck.
Thanks for quick reply. My problem is however deeper than your solution :) I strongly need version 5.3.x, not 5.4. The PPA you proposed has been for some time on my sources.list, but I refused it because of the version. What I really want to understand is why on earth a package that is officially built for precise can't be installed on precise?

---

