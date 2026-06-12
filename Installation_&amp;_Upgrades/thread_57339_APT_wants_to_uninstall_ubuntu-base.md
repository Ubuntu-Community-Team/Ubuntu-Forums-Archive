---
title: "APT wants to uninstall ubuntu-base"
date: 2005-08-16
forum: Installation &amp; Upgrades
---

### Post by yellowhippy on 2005-08-16
Hi,

everytime I try to update my system, apt-get, synaptic and aptitude tell me that it wants to remove the ubuntu-base first. After that 750MB will be freed......
Any ideas. Is it possible that I hit a wrong button in aptitude? 

Thanks,
Chris

---

### Post by heimo on 2005-08-16
What does it say if you run this on terminal:
 ```
sudo apt-get update
sudo apt-get -s upgrade

```

---

### Post by yellowhippy on 2005-08-16
It says:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But when I try to use aptitude or synaptic it still wants to remove the base system.

Could it be that aptitide has its own configaration files where it stores the pending tasks. If so, can I reset atptitude?

Thanks
Chris

---

### Post by yellowhippy on 2005-08-16
If I run:
```

apt-get -s remove aptitude
```
I get:

```

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  aptitude ubuntu-base
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Remv ubuntu-base [0.43]
Remv aptitude [0.2.15.8-1ubuntu12]

```

---

### Post by heimo on 2005-08-16
Odd problem. Haven't seen before. This is probably useless, but I'd try to run
 ```
sudo dpkg --configure -a
#and maybe *careful! may mess up your system!*
sudo dpkg-reconfigure ubuntu-base
```

---

### Post by yellowhippy on 2005-08-16
No, didn't help. 
Can't I mark the base-system as importend to apt-get will leave it alone?

Thanks,
Chris

---

### Post by yellowhippy on 2005-08-16
Does the ubuntu-base depend on aptitude? Is there a way I could find out?

I tried to remove synaptic and it worked fine.

Thanks,
Chris

---

### Post by heimo on 2005-08-16
So does the apt-get want to remove ubuntu-base anymore? (If you try to install something.) Or is it just aptitude and Synaptic? Could you try to lock the version of ubuntu-base in Synaptic?

---

### Post by heimo on 2005-08-16
[QUOTE=yellowhippy]Does the ubuntu-base depend on aptitude? Is there a way I could find out?

I tried to remove synaptic and it worked fine.

Thanks,
Chris[/QUOTE]

aptitude is dependency of ubuntu-base and ubuntu-base is basicly just a meta-package, collection of dependencies for easy installation, it contains  only these files:
[http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ubuntu-base&version=hoary&arch=i386]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=ubuntu-base&version=hoary&arch=i386")
 > usr/share/doc/ubuntu-base/changelog.gz                [base/ubuntu-base]("http://packages.ubuntu.com/hoary/base/ubuntu-base")
usr/share/doc/ubuntu-base/copyright                [base/ubuntu-base]("http://packages.ubuntu.com/hoary/base/ubuntu-base") so, removing ubuntu-base package is not critical, but removing all the packages that are dependencies of ubuntu-base, is critical

---

### Post by yellowhippy on 2005-08-16
For some reason it seems to work now. I donn't know, I have changed nothing. Well we'll see for how long....Thanks for the help.

Chris

---

