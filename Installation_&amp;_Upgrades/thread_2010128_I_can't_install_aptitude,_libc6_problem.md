---
title: "I can't install aptitude, libc6 problem"
date: 2012-06-25
forum: Installation &amp; Upgrades
---

### Post by jorddu on 2012-06-25
Hello, I have some issues with my server and I saw everywhere that I need aptitude to solve them.

I have this result :

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: aptitude-common (= 0.6.8-1) but it is not going to be installed
            Depends: libapt-pkg4.12 (>= 0.9.3) but it is not going to be installed
            Depends: libboost-iostreams1.49.0 (>= 1.49.0-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
            Depends: libept1.4.12 but it is not going to be installed
            Depends: libsigc++-2.0-0c2a (>= 2.0.2) but it is not going to be installed
            Depends: libxapian22 but it is not going to be installed
            Recommends: aptitude-doc-en but it is not going to be installed or
                        aptitude-doc
            Recommends: apt-xapian-index but it is not going to be installed
            Recommends: libparse-debianchangelog-perl but it is not going to be installed
 libc6 : Depends: libc-bin (= 2.13-0ubuntu13) but 2.13-33 is to be installed
 libc6-dev : Depends: libc6 (= 2.13-33) but 2.13-0ubuntu13 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---------

After I execute this command :

sudo dpkg --configure -a

I have this result :

dpkg: dependency problems prevent configuration of libc6-dev:amd64:
 libc6-dev:amd64 depends on libc6 (= 2.13-33); however:
  Version of libc6:amd64 on system is 2.13-0ubuntu13.
dpkg: error processing libc6-dev:amd64 (--configure):
 dependency problems - leaving unconfigured
Setting up php5-common (5.4.4-2) ...
dpkg: error processing php5-common (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of php5-cli:
 php5-cli depends on php5-common (= 5.4.4-2); however:
  Package php5-common is not configured yet.
dpkg: error processing php5-cli (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-imap:
 php5-imap depends on php5-common (= 5.4.4-2); however:
  Package php5-common is not configured yet.
dpkg: error processing php5-imap (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libapache2-mod-php5filter:
 libapache2-mod-php5filter depends on php5-common (= 5.4.4-2); however:
  Package php5-common is not configured yet.
dpkg: error processing libapache2-mod-php5filter (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-mysql:
 php5-mysql depends on phpapi-20100525; however:
  Package phpapi-20100525 is not installed.
  Package libapache2-mod-php5filter which provides phpapi-20100525 is not configured yet.
  Package php5-cli which provides phpapi-20100525 is not configured yet.
 php5-mysql depends on php5-common (= 5.4.4-2); however:
  Package php5-common is not configured yet.
dpkg: error processing php5-mysql (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libstdc++6-4.5-dev:
 libstdc++6-4.5-dev depends on libc6-dev (>= 2.13-5); however:
  Package libc6-dev:amd64 is not configured yet.
dpkg: error processing libstdc++6-4.5-dev (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5-gd:
 php5-gd depends on phpapi-20100525; however:
  Package phpapi-20100525 is not installed.
  Package libapache2-mod-php5filter which provides phpapi-20100525 is not configured yet.
  Package php5-cli which provides phpapi-20100525 is not configured yet.
 php5-gd depends on php5-common (= 5.4.4-2); however:
  Package php5-common is not configured yet.
dpkg: error processing php5-gd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of g++-4.5:
 g++-4.5 depends on libstdc++6-4.5-dev (= 4.5.3-12); however:
  Package libstdc++6-4.5-dev is not configured yet.
dpkg: error processing g++-4.5 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libc6-dev:amd64
 php5-common
 php5-cli
 php5-imap
 libapache2-mod-php5filter
 php5-mysql
 libstdc++6-4.5-dev
 php5-gd
 g++-4.5

Can someone help me? I realy don't know how to solve this.

---

### Post by coffeecat on 2012-06-25
A few questions:

Do you have a Debian repository enabled? Debian's aptitude package requires the package aptitude-common, but Ubuntu's does not - aptitude-common is not listed as a dependency of Ubuntu's aptitude package and there is no aptitude-common in the Ubuntu repos that I can find.

What version of Ubuntu are you running? If Precise, the Ubuntu repo version of aptitude is 0.6.6-1ubuntu1, whereas you seem to be trying to install the later 0.6.8-1.

Did you try running 'apt-get -f install'?

Is there a particularly good reason given for using aptitude for your server problems?

---

### Post by jorddu on 2012-06-25
Hello, thanks for the answer,

I don't know if I have a Debian repository, how can I know this?

My version of Ubuntu is : 
Linux version 2.6.36-xenU-4814-x86_64 

When I do a "apt-get -f install" my console display this error:

Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-33_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I need aptitude because apt-get install fail for installing some package and I read on the net that aptitude is better for this.

---

### Post by coffeecat on 2012-06-25
> **jorddu said:**
> I don't know if I have a Debian repository, how can I know this?

You would know if you enabled a non-Ubuntu repository in the past, which you might have done for the non-standard kernel you are running (see below). Anyway, post the output of these two commands:

```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```

> **jorddu said:**
> My version of Ubuntu is : 
Linux version 2.6.36-xenU-4814-x86_64 

That's the kernel you are running, not the version of Ubuntu, and it is not a standard Ubuntu kernel as far as I can make out. For the Ubuntu version, post the output of this:

```
cat /etc/lsb-release 
```

> **jorddu said:**
> When I do a "apt-get -f install" my console display this error:

Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.13-33_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Let's see what repositories you have before we go any further with this.

> **jorddu said:**
> I need aptitude because apt-get install fail for installing some package and I read on the net that aptitude is better for this.

"Read on the net." Hmmmm. I suspect that what you read has more to do with the personal prejudices of the writer than any rational reason for preferring aptitude. It certainly used to be said that aptitude was better for dependency resolution, but I doubt that is true any more, and if apt-get fails to install packages then there is an underlying problem that needs fixing - such as you have now. I suspect your underlying problem could be repository conflicts, but let's see those outputs.

---

