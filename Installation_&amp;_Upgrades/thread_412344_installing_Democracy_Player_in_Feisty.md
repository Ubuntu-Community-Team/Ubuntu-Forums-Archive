---
title: "installing Democracy Player in Feisty"
date: 2007-04-18
forum: Installation &amp; Upgrades
---

### Post by fakie_flip on 2007-04-18
Hello! I want to install Democracy Player in Feisty, but it doesnt seem to be working. I followed the guide for installing for Ubuntu, but the repo is for Edgy and apt gives me this error.

```
chris@ubuntu:~$ sudo apt-get install democracyplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  democracyplayer: Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is to be installed
                   Depends: mozilla-dev but it is not installable
                   Depends: mozilla-psm but it is not installable
E: Broken packages
chris@ubuntu:~$ 
```

---

### Post by Marcos.Rufino on 2007-04-20
Hey my friend. It seems to be easier than I thought it would be!!

I've also tried to install Democracy Player via its website, unsuccessfully. I had tried the prebuild package for Ubuntu and also the tarball. I came across the same error message that yours. 

BUT, I could install Democracy easily using the Add/Remove programs (in the Applications menu)!! It solved all the python dependencies.

That Add/Remove thing is wonderful. We should take a care look at it.

---

### Post by jfernyhough on 2007-04-20
Hmm... I think your Add/Remove is installing the older version (0.9.2.1-2.1ubuntu2) from the Ubuntu repo, not the newest (0.9.5.1-1ubuntupcf) from the Democracy repo (deb [http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/democracy/linux/repositories/ubuntu) edgy/).

I presume the problem is down to the package being for edgy, not feisty. I have the exact same thing, and it's annoying my Ubuntu version is older then the Windows version. :D

My advice is to hang fire for a couple of days until the Democracy people can repackage for feisty.

---

### Post by nami on 2007-05-19
Still no Democracy Player for feisty fawn?

---

### Post by macabro22 on 2007-05-20
That sux!

---

### Post by nami on 2007-05-21
I don't know any easy way to install the latest version, but Version 0.9.2.1 can be easily installed with the following 3 commands :KS

> sudo aptitude install democracyplayer
sudo aptitude -f install
sudo aptitude install libxine-extracodecs

---

