---
title: "Unable to install or remove anything- dependency problem"
date: 2012-07-02
forum: Installation &amp; Upgrades
---

### Post by pedja1 on 2012-07-02
Here is the problem:
```
pedja@pedja-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following packages will be upgraded:
  fglrx-amdcccle
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/5883 kB of archives.
After this operation, 1863 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have tryed everything i can think of
> sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo apt-get -f remove
Nothing helps
And also this error appears whenever i try to install or remove any program, and when using Synaptic Package Manager or Ubuntu Software Center

Please hel, i dont want to reinstall whole system

---

### Post by SlugSlug on 2012-07-02
maybe try 

sudo apt-get install xorg-driver-fglrx

---

### Post by pedja1 on 2012-07-02
> **SlugSlug said:**
> maybe try 

sudo apt-get install xorg-driver-fglrx

it tells me that xorg-driver-fglrx doesn't have installation candidates and to try fglrx-updates xorg (or something like that, not at home right now, can't check exactly what)
but when I try that same error as in first post

---

### Post by SlugSlug on 2012-07-02
sudo aptitude reinstall fglrx-amdcccle

---

### Post by pedja1 on 2012-07-02
> **SlugSlug said:**
> sudo aptitude reinstall fglrx-amdcccle

will try when I get home

---

### Post by SlugSlug on 2012-07-02
may also be worth checking you have enabled  proprietary drivers,

a quick google can guide you on that

---

### Post by jmfal on 2012-07-02
Run this in a terminal:

```
  sudo dpkg --configure  -a    
```

And try to update/upgrade.

---

### Post by houseworkshy on 2012-07-02
As you've had a previous failed install "sudo apt-get purge fglrx-amdcccle" may be worth trying as a preliminary.

---

### Post by pedja1 on 2012-07-03
> **SlugSlug said:**
> sudo aptitude reinstall fglrx-amdcccle

this worked, thanks

---

