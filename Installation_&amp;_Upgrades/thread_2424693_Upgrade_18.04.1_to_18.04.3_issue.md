---
title: "Upgrade 18.04.1 to 18.04.3 issue"
date: 2019-08-13
forum: Installation &amp; Upgrades
---

### Post by Deon_Oosthuizen on 2019-08-13
I have to servers stuck on 18.04.1. Several other server that was on 18.04.2 updated fine to 18.04.3.

Servers are used for LAMP platforms with very simplistic solutions deployed. Very little customization was done form basic install.

I have done DuckDuckGo searching and have tried every thing I could find on possible updating the servers.

These may be servers that was upgraded from 16.04 to 18.04 last year.

The servers are located behind a proxy, but get normal updates without an issue.

How can I help to figure out what the issue(s) could be? Thank you in advance for your support.

```
lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:        18.04
Codename:       bionic
```

Server 1:
```
uname -r
4.15.0-36-generic
```

Server 2:
```
uname -r
5.0.0-23-generic
```

Both report:
```
cat /etc/os-release
NAME="Ubuntu"
VERSION="18.04.1 LTS (Bionic Beaver)"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu 18.04.1 LTS"
VERSION_ID="18.04"
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
VERSION_CODENAME=bionic
UBUNTU_CODENAME=bionic
```

---

### Post by deadflowr on 2019-08-13
What are the base-files versions?
```
apt policy base-files
```
updated version should be
10.1ubuntu2.6
original would be
10.1ubuntu2
not sure what the base-files was for the 18.04.1 point release was though. most likely neither of those.

Server 1 seems to be running a little bit older kernel version.
Is that running the livepatch utility? (current kernel version should be 4.15.0-55)

(Server 2 is running the current hwe stack kernel (5.0.0-23, so that looks fine)

---

### Post by Deon_Oosthuizen on 2019-08-13
Yes, server 2 is very strange as the kernel is up to date, but it is showing version .1

apt policy base-files
base-files:
  Installed: 10.1ubuntu2.2
  Candidate: 10.1ubuntu2.2
  Version table:
 *** 10.1ubuntu2.2 100
        100 /var/lib/dpkg/status

apt policy base-files
base-files:
  Installed: 10.1ubuntu2.2
  Candidate: 10.1ubuntu2.2
  Version table:
 *** 10.1ubuntu2.2 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security/main amd64 Packages
        100 /var/lib/dpkg/status
     10.1ubuntu2 500
        500 [http://za.archive.ubuntu.com/ubuntu](http://za.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic/main amd64 Packages

---

### Post by Impavidus on 2019-08-13
18.04.1, .2 and .3 are most importantly different live disk images. For an installed system those numbers only tell you it's up-to-date compared to those live disk images, but going from 18.04.1 to .2 to .3 on your installed system is just a regular upgrade of the type you get almost every day. It's not a release upgrade or something fancy. So, you don't get the regular upgrades. Not all of them at least.

Can you check your software sources?```
cat /etc/apt/sources.list
```Maybe the bionic-updates repository is disabled.

---

### Post by deadflowr on 2019-08-13
You seem to have the -security repositories enabled but not the -updates repositories.
Not all updates are security related.

To enable you can add a line with the -updates entry to the bionic sources.list file like
```
deb http://us.archive.ubuntu.com/ubuntu bionic**-updates** main restricted universe multiverse
```

(I'm not sure if you have any of the other repos beside main, but this just a general idea of what it would look like.)


^Ninja'd

---

### Post by Deon_Oosthuizen on 2019-08-14
Thank you for that advice and support.

Here is my sources.list this is the same for both the working and these two stubborn servers.

deb [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) bionic main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) bionic-updates main restricted
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) bionic universe
deb-src [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) bionic-updates universe

---

### Post by Impavidus on 2019-08-14
You've got some source code repositories enabled (which most people never use), but your binary sources are incomplete. There are some optional things, but I'll show you what's enabled on my system (replacing my mirror with yours and my release with yours. I assume the mirrors are identical):```
# You probably want to keep these
deb  http://za.archive.ubuntu.com/ubuntu/ bionic main restricted
# And add the updates repository
deb http://za.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

# Maybe you want these, for other (optional) software
deb http://za.archive.ubuntu.com/ubuntu/ bionic universe multiverse
# Idem for updates
deb http://za.archive.ubuntu.com/ubuntu/ bionic-updates universe multiverse

# Maybe you want to enable backports, maybe not. On servers it may be better to be conservative and not include them.
deb http://za.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

# And security. You probably want this one.
deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# And these if you want universe and multiverse
deb http://security.ubuntu.com/ubuntu bionic-security universe multiverse
```

---

### Post by Deon_Oosthuizen on 2019-08-16
Thank you very much, that resolved the issue. I thus need to learn more about setting up the sources.list.

---

