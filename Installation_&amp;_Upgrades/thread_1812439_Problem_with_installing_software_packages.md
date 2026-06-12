---
title: "Problem with installing software packages"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by utpallab on 2011-07-26
Hello,
I am working with ubuntu 10.04. Whenever I try to install softwares packages, it just can not be done. The message comes like "Could not download all required files. Please check installation medium". And when I tried to install softwares available in the ubuntu software center, the installation process never proceeds.
Please suggest me a way to solve this problem.
Thanking you in advance:confused:

---

### Post by Peter09 on 2011-07-26
Have you enough free disk space?

---

### Post by 2F4U on 2011-07-26
Can you try to install with apt-get in a terminal? That would make the underlying error more visible than by using software center.

---

### Post by Peter09 on 2011-07-26
Good idea 2F4U
 
in a terminal run
 
```
 
sudo apt-get update

```
 
and if no errors
run
```
 
sudo apt-get upgrade

```
 
report any errors back here.

---

### Post by utpallab on 2011-07-26
Yes, I have tried with apt-get command in the terminal, and there is message like " Unable to fetch some archives". Can it be because of the internet connection problem?

---

### Post by Peter09 on 2011-07-26
Does it tell you what archives it cannot get?
 
It may be your sources file is not configured properley.

---

### Post by utpallab on 2011-07-26
I have run the command sudo apt-get update, and the error output file reads as

Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg
  Could not connect to 172.16.1.1:3128 (172.16.1.1). - connect (110: Connection timed out)
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Could not connect to 172.16.1.1:3128 (172.16.1.1). - connect (110: Connection timed out)
Err [http://ppa.launchpad.net/ubuntu-ha/lucid-cluster/ubuntu/](http://ppa.launchpad.net/ubuntu-ha/lucid-cluster/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Unable to connect to 172.16.1.1:3128:
Err [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/) lucid/main Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
  Could not connect to 172.16.1.1:3128 (172.16.1.1). - connect (110: Connection timed out)
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
  Unable to connect to 172.16.1.1:3128:
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
  Unable to connect to 172.16.1.1:3128:
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources
  Unable to connect to 172.16.1.1:3128:
Ign [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
  Unable to connect to 172.16.1.1:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  Unable to connect to 172.16.1.1:3128:
Err [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
  Unable to connect to 172.16.1.1:3128:

---

### Post by Peter09 on 2011-07-26
ARe you connected to the internet? 
 
If you are go to Update Manager and select the server you are downloading from, the option is there somewhere, select the best response.
 
Then try again.

---

