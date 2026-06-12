---
title: "Can't install lib64expat1"
date: 2013-04-20
forum: Installation &amp; Upgrades
---

### Post by nehaljwani on 2013-04-20
```

wani@tester:~/exiv2-trunk/trunk/build$ uname -a
Linux tester 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux



wani@tester:~/exiv2-trunk/trunk/build$ sudo apt-get install lib64expat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 lib64expat1:i386 : Depends: libc6-amd64:i386 (>= 2.14) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

---

### Post by matt_symes on 2013-04-20
Hi

The first thing we should look at is your sources as these dependency siiues are generally caused by incorrect sources.

Open a terminal and please post the output of

```
grep -r "^[^#]" /etc/apt/sources.list{,.d/*}
```

Kind regards

---

### Post by nehaljwani on 2013-04-20
```
wani@tester:~/exiv2-trunk/trunk/build$ grep -r "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal main restricted
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates main restricted
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal universe
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates universe
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal multiverse
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-updates multiverse
/etc/apt/sources.list:deb http://in.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:deb-src http://in.archive.ubuntu.com/ubuntu/ quantal-backports main restricted universe multiverse
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security main restricted
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security universe
/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list:deb-src http://security.ubuntu.com/ubuntu quantal-security multiverse
/etc/apt/sources.list:deb http://extras.ubuntu.com/ubuntu quantal main
/etc/apt/sources.list:deb-src http://extras.ubuntu.com/ubuntu quantal main
grep: /etc/apt/sources.list.d/*: No such file or directory
wani@tester:~/exiv2-trunk/trunk/build$ 

```

---

### Post by matt_symes on 2013-04-20
Hi

You have no sources.list.d directory  ?

Can you post the output of

```
ls -l /etc/apt/sources.list.d/
```

so i can double check.

I'll take a look at you sources.

Kind regards

---

### Post by nehaljwani on 2013-04-20
```

wani@tester:~/exiv2-trunk/trunk/build$ ls -l /etc/apt/sources.list.d/
total 0

```

---

### Post by matt_symes on 2013-04-20
Hi

You sources are fine so as a test, i though i would install it on my system. I am using quantal like you. I get the same issue.

```

matthew-S206:/home/matthew % sudo apt-get install lib64expat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 lib64expat1:i386 : Depends: libc6-amd64:i386 (>= 2.14) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
matthew-S206:/home/matthew % 

```

The problem seems to be with the package and it's dependencies itself as i don't think i have done anything to my system that would stop it installing.

I'll investigate further.

Kind regards

---

### Post by matt_symes on 2013-04-20
.

---

