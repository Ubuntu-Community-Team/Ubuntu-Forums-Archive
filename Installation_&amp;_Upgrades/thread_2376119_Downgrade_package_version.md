---
title: "Downgrade package version"
date: 2017-10-30
forum: Installation &amp; Upgrades
---

### Post by rodrigodlima on 2017-10-30
Hi all,

As a security team issue, I need to be able to downgrade packages that have been updated. But I'm having problems with some versions of packages that are no longer in the repositories.
For example, I installed a new server Ubutnu Xenial (16.04 LTS)  with a ISO media. The package wget installed was 1.17.1-1ubuntu1.2. Then, I update wget to version 1.17.1-1ubuntu1.3. When I tried to downgrade the wget for version 1.17.1-1ubuntu1.2, this version doesn't exists more.

# apt-cache policy wget
wget:
  Installed: 1.17.1-1ubuntu1.2
  Candidate: 1.17.1-1ubuntu1.3
  Version table:
     1.17.1-1ubuntu1.3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
 *** 1.17.1-1ubuntu1.2 100
        100 /var/lib/dpkg/status
     1.17.1-1ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages



# apt-cache policy wget
wget:
  Installed: 1.17.1-1ubuntu1.3
  Candidate: 1.17.1-1ubuntu1.3
  Version table:
 *** 1.17.1-1ubuntu1.3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     1.17.1-1ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages


# apt-get install wget=1.17.1-1ubuntu1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Version '1.17.1-1ubuntu1.2' for 'wget' was not found

There is a way to install the last version for this package from some repository?

---

### Post by deadflowr on 2017-10-30
Look to see if the package is actually in your own system archive folder
look in /var/cache/apt/archives

---

### Post by ian-weisser on 2017-10-30
Older versions of packages are archived at launchpad.net.
It's not a repository - you will need to download the package manually instead of using apt.

---

