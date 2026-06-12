---
title: "Unable to install php8.2-intl on Ubuntu 23.10"
date: 2024-01-20
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2024-01-20
My website depends upon the internationalization feature but when I try to install it I get:

```
$ sudo apt-get install php8.2-intl
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 php8.2-intl : Depends: php8.2-common (= 8.2.10-2ubuntu1) but 8.2.14-1+ubuntu22.04.1+deb.sury.org+1 is to be installed
E: Unable to correct problems, you have held broken packages.

```
I have the following repositories defined:

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-updates multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) mantic-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) mantic-security multiverse
deb [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_12.x](https://deb.nodesource.com/node_12.x) focal main
deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_12.x](https://deb.nodesource.com/node_12.x) focal main
deb [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_12.x](https://deb.nodesource.com/node_12.x) focal main
deb-src [signed-by=/usr/share/keyrings/nodesource.gpg] [https://deb.nodesource.com/node_12.x](https://deb.nodesource.com/node_12.x) focal main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-updates multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-backports main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lunar-security multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal-updates main restricted
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal-updates universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal-updates multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) focal-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
```

I tried to do $ sudo add-apt-repository ppa:ondrej/php but I got

```
Ign:5 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) mantic InRelease      
Err:6 [https://ppa.launchpadcontent.net/ondrej/php/ubuntu](https://ppa.launchpadcontent.net/ondrej/php/ubuntu) mantic Release
  404  Not Found [IP: 185.125.190.80 443]
Reading package lists... Done
E: The repository 'https://ppa.launchpadcontent.net/ondrej/php/ubuntu mantic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
```

---

