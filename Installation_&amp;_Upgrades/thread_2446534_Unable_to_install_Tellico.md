---
title: "Unable to install Tellico"
date: 2020-07-02
forum: Installation &amp; Upgrades
---

### Post by rolfedavid on 2020-07-02
Hi, I have just upgraded from 18. to 20. Tellico that I use a lot is not working. I have tried to reinstall but get a message that there are unmet dependencies. can someone tell me what these dependences are? libkf5sane5 is only one of a package (tried installing via the terminal, and this file was mentioned). I have KDE frameworks and QT installed.

Many thanks in anticipation

---

### Post by ActionParsnip on 2020-07-02
What is the output of:
```

apt-cache policy tellico; lsb_release -a; uname -a

```
Thanks

---

### Post by rolfedavid on 2020-07-02
```
tellico:
  Installed: (none)
  Candidate: 3.2.3-1build1
  Version table:
     3.2.3-1build1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux david-Dell-DC051 5.4.0-40-generic #44-Ubuntu SMP Tue Jun 23 00:01:04 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by rolfedavid on 2020-07-02
Thanks ActionParsnip have now installed the LSB modules, still unable to install Tellico. output from your code is now.
tellico:
  Installed: (none)
  Candidate: 3.2.3-1build1
  Version table:
     3.2.3-1build1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
LSB Version:    core-11.1.0ubuntu2-noarch:security-11.1.0ubuntu2-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04 LTS
Release:    20.04
Codename:    focal
Linux david-Dell-DC051 5.4.0-40-generic #44-Ubuntu SMP Tue Jun 23 00:01:04 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by ActionParsnip on 2020-07-02
Ok, what is the output of:
```

sudo apt install tellico

```
Thanks

---

### Post by rolfedavid on 2020-07-02
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 tellico : Depends: libkf5sane5 (>= 4.3.4) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by rolfedavid on 2020-07-02
it would also seem that this hits the scanner software such as Sane, Vuescan, Document Scanner. These are listed on the software manager.

---

### Post by ActionParsnip on 2020-07-02
What is the output of:
```

apt-cache policy libkf5sane5 

```

Thanks

---

### Post by rolfedavid on 2020-07-02
libkf5sane5:
  Installed: (none)
  Candidate: 19.12.3-0ubuntu1
  Version table:
     19.12.3-0ubuntu1 500
        500 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/micha-ubuntu-libaqbanking-bionic.list:2 and /etc/apt/sources.list.d/micha-ubuntu-libaqbanking-bionic.list:3

---

### Post by rolfedavid on 2020-07-03
After installing upgrades the comp wouldn't boot up. Did a complete new install that fixed the problem. So all is well for the moment.
Many thanks ActionParsnip for your help.

---

