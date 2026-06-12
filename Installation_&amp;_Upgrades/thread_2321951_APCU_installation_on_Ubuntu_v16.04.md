---
title: "APCU installation on Ubuntu v16.04"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by athena2 on 2016-04-25
Hello,

When I tried to install APCU on my Ubuntu (16.04) setup, I got this error messages. How can I install it?

```
root@user:~# apt-get install php7.0-apcu php7.0-apcu-bc 
 Reading  package lists... Done
 Building dependency tree     
 Reading state information... Done
 E: Unable to locate package php7.0-apcu
 E: Couldn't find any package by glob 'php7.0-apcu'
 E: Couldn't find any package by regex 'php7.0-apcu'
 E: Unable to locate package php7.0-apcu-bc
 E: Couldn't find any package by glob 'php7.0-apcu-bc'
 E: Couldn't find any package by regex 'php7.0-apcu-bc'
```

---

### Post by QIII on 2016-04-25
Hello!

Do you have the Universe repo activated?  Please see [this]("http://packages.ubuntu.com/xenial/php-apcu").  It appears that the package name is simply php-apcu in the Xenial Universe repo.

May I ask why you are running as root?  [This]("https://help.ubuntu.com/community/RootSudo") wiki article may be of interest to you.

---

### Post by Frogs Hair on 2016-04-25
Is it possible the package names have changed ? Though I find a number of php7 packages is synaptic the first one php7.apcu is not there. I do see a php7.0-bcmath package.

---

### Post by athena2 on 2016-04-25
Hello QIII,

Since I am new to Ubuntu (and in general to Linux), I am not sure what does "activating Universe repo" mean? In the link you gave, there is no information on how to activate a repo.  And when I tried installing php-apcu instead on php7.0-apcu, I got the following errors.  I will follow the recommendations in the link you gave on running as root. Thank you.


```
root@user:~# apt-get install php-apcu php-apcu-bc
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package php-apcu-bc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'php-apcu-bc' has no installation candidate

```

---

### Post by athena2 on 2016-04-25
Hello,

Thank you. When I check the available version of php-apcu I get the following. It seems that my Ubuntu installation is not aware this installation library?

```
root@user:~# apt-cache policy php-apcu
php-apcu:
  Installed: 5.1.3+4.0.10-1build1
  Candidate: 5.1.3+4.0.10-1build1
  Version table:
 *** 5.1.3+4.0.10-1build1 500
        500 http://us.archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by athena2 on 2016-04-28
Hello QIII,

Based on your suggestion I activated the universal repo, then tried to install php-apcu. It worked. Thank you.  Then I tried php-apcu-bc. But this one failed.  So where is the problem? Thank you.

> **QIII said:**
> Hello!

Do you have the Universe repo activated?  Please see [this]("http://packages.ubuntu.com/xenial/php-apcu").  It appears that the package name is simply php-apcu in the Xenial Universe repo.

May I ask why you are running as root?  [This]("https://help.ubuntu.com/community/RootSudo") wiki article may be of interest to you.

---

### Post by QIII on 2016-04-28
Let's try to simulate the install of php-apcu on its own first.

 ```
sudo apt-get install -s php-apcu
```

Post the results.

---

### Post by flashydave on 2016-05-23
You could try downloading and installing php-apcu-bc_1.0.3-2_amd64.deb from one the yakkety mirrors using wget . 
It hasnt yet been back-ported to 16.04 but will install OK using dpkg -i

---

### Post by segfaulty2 on 2016-06-08
if you are not able to install **php-apcu-bc**, and you have the **apcu-extension** already installed, you can include this simple php-file:

[https://github.com/SegFaulty/php-apcu-bc](https://github.com/SegFaulty/php-apcu-bc)

wich will simulate the missing **apc_*** function by its **apcu_*** pendants

---

