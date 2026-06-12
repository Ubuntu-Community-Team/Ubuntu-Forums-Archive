---
title: "Upgrading Ubuntu"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by shubham1 on 2011-10-17
[http://ubuntuforums.org/showthread.php?t=1856403](http://ubuntuforums.org/showthread.php?t=1856403)
[http://ubuntuforums.org/showthread.php?t=1853345](http://ubuntuforums.org/showthread.php?t=1853345)
[http://ubuntuforums.org/showthread.php?t=1841384](http://ubuntuforums.org/showthread.php?t=1841384)
these are the links to my thread which are unsloved these shows i am trying to upgrade to ubuntu 11.10from so many times
i have used update manger but it does not work and pleas do not tell me about it
i have used
sudo apt-get upgrade
sudo apt-get update
sudo apt-get dist-upgrade
and then worked and still not upgraded

---

### Post by Lars Noodén on 2011-10-17
You have to update APT's /etc/apt/sources.list to point to the new distro before dist-upgrade can work.  Is it pointing to the version you want?

---

### Post by shubham1 on 2011-10-17
> **Lars Noodén said:**
> You have to update APT's /etc/sources.list to point to the new distro before dist-upgrade can work.  Is it pointing to the version you want?
i opened it using a terminal it comes with a blank file what to enter

---

### Post by Lars Noodén on 2011-10-17
> **shubham1 said:**
> i opened it using a terminal it comes with a blank file what to enter

I spelled it right in the subject but wrong in the body of the post.  It should be 

/etc/apt/sources.list

---

### Post by shubham1 on 2011-10-17
> **Lars Noodén said:**
> I spelled it right in the subject but wrong in the body of the post.  It should be 

/etc/apt/sources.list
which line where what to write

---

### Post by Lars Noodén on 2011-10-17
Make a backup copy of the file then edit it.  Find all instances of "natty" and replace them with "oneiric".  It will occur on many lines.  Then run apt-get update then apt-get dist-upgrade.

---

### Post by shubham1 on 2011-10-18
> **Lars Noodén said:**
> Make a backup copy of the file then edit it.  Find all instances of "natty" and replace them with "oneiric".  It will occur on many lines.  Then run apt-get update then apt-get dist-upgrade.
shubham@workspace:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by shubham1 on 2011-10-18
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/

---

### Post by shubham1 on 2011-10-18
when i tired after some time apt-get update is started

---

### Post by shubham1 on 2011-10-18
done apt-get update tried apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 ia32-libs : Recommends: ia32-libs-multiarch but it is not installable
             Breaks: nspluginwrapper (< 1.4.4-0ubuntu2) but 1.2.2-0ubuntu9 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

---

### Post by Lars Noodén on 2011-10-18
Hmm.  All I can say is that is how I often upgrade Ubuntu.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by shubham1 on 2011-10-18
> **Lars Noodén said:**
> Hmm.  All I can say is that is how I often upgrade Ubuntu.

```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
why that error is comming it has came after i changed the file

---

### Post by Lars Noodén on 2011-10-18
Are the only changes "natty" to "oneiric" ?

---

### Post by shubham1 on 2011-10-18
should i use upgrade -d ?

---

### Post by shubham1 on 2011-10-18
yes only did that nothing elas
should i use upgrade -d

---

