---
title: "can't upgrade in 14.10"
date: 2015-12-21
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2015-12-21
Never had this problem before. Any tips on what to do?

> pedro@pedro-schule:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
pedro@pedro-schule:~$ 

---

### Post by sudodus on 2015-12-21
The version 14.10 has passed end of life, and the repositories are no longer maintained. The previous version 14.04 has long time support, LTS, and is still maintained. The versions 15.04 and 15.10 have only 9 months support, which means that 15.04 will reach end of live in January (one month from now). The next version to be released, 16.04 will have long time support, LTS.

The rule of thumb is that the version released in April even years will have long time support, LTS:

8.04, 10.04, 12.04, 14.04, 16.04 ...

and the intermediate versions have only 9 months support.

Standard Ubuntu, Kubuntu and Ubuntu Server are supported for 5 years, so these 14.04 LTS flavours are supported until April 2019.

Lubuntu and Xubuntu are supported for 3 years, so these 14.04 LTS flavours are supported until April 2017.

I'm not sure about the other flavours. You can check at their own websites.

-o-

I suggest that you make a fresh installation of either 14.04.1 LTS or 15.10. Both of these versions can be upgraded to the next LTS release, 16.04, but you should wait until it is debugged for a few months and the first point release is published, 16.04.1 LTS

---

### Post by Pedroski55 on 2015-12-21
Thanks a lot! I did not know that 14.10 was not LTS. I'll hang on for 16.04. I also have 15.10, just all my work stuff is in the 14.10 version, which I thought was LTS.

---

### Post by kansasnoob on 2015-12-21
> **Pedroski55 said:**
> Thanks a lot! I did not know that 14.10 was not LTS. I'll hang on for 16.04. I also have 15.10, just all my work stuff is in the 14.10 version, which I thought was LTS.

You may not be running 14.10 because I see this in your OP:

> E: Problem with MergeList /var/lib/apt/lists/cn.archive.ubuntu.com_ubuntu_dists_**[COLOR="#FF0000"]trusty[/COLOR]**_main_i18 n_Translation-en

It's worth more investigating. Please post the output of:

```
lsb_release -a
```

If that shows Trusty (14.04*) then we should have a look at your software sources.

---

### Post by Pedroski55 on 2015-12-24
You are right, I was mistaken. I thought I had 14.10, but I actually have 14.04.3 The problem seemed to correct itself the next day. Maybe it was an internet connectivity problem. Sorry to have troubled you.

and MERRY CHRISTMAS!

```
pedro@pedro-schule:~$ lsb_release -a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch:core-4.1-amd64:core-4.1-noarch:cxx-3.0-amd64:cxx-3.0-noarch:cxx-3.1-amd64:cxx-3.1-noarch:cxx-3.2-amd64:cxx-3.2-noarch:cxx-4.0-amd64:cxx-4.0-noarch:cxx-4.1-amd64:cxx-4.1-noarch:desktop-3.1-amd64:desktop-3.1-noarch:desktop-3.2-amd64:desktop-3.2-noarch:desktop-4.0-amd64:desktop-4.0-noarch:desktop-4.1-amd64:desktop-4.1-noarch:graphics-2.0-amd64:graphics-2.0-noarch:graphics-3.0-amd64:graphics-3.0-noarch:graphics-3.1-amd64:graphics-3.1-noarch:graphics-3.2-amd64:graphics-3.2-noarch:graphics-4.0-amd64:graphics-4.0-noarch:graphics-4.1-amd64:graphics-4.1-noarch:languages-3.2-amd64:languages-3.2-noarch:languages-4.0-amd64:languages-4.0-noarch:languages-4.1-amd64:languages-4.1-noarch:multimedia-3.2-amd64:multimedia-3.2-noarch:multimedia-4.0-amd64:multimedia-4.0-noarch:multimedia-4.1-amd64:multimedia-4.1-noarch:printing-3.2-amd64:printing-3.2-noarch:printing-4.0-amd64:printing-4.0-noarch:printing-4.1-amd64:printing-4.1-noarch:qt4-3.1-amd64:qt4-3.1-noarch:security-4.0-amd64:security-4.0-noarch:security-4.1-amd64:security-4.1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
pedro@pedro-schule:~$ 
```

---

### Post by sudodus on 2015-12-24
I'm glad it works for you now :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

