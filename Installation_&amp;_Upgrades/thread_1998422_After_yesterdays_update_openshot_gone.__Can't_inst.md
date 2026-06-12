---
title: "After yesterdays update openshot gone.  Can't install"
date: 2012-06-06
forum: Installation &amp; Upgrades
---

### Post by rulymo21 on 2012-06-06
Here is what it says:

penshot: Depends: python-mlt but it is not going to be installed
          Depends: python (>= 2.5) but 2.7.3-0ubuntu2 is to be installed

---

### Post by rulymo21 on 2012-06-06
[I]Here is what it says: 
 
penshot: Depends: python-mlt but it is not going to be installed 
          Depends: python (>= 2.5) but 2.7.3-0ubuntu2 is to be installed 			[/I]

---

### Post by LiamOS on 2012-06-06
Have you tried installing python-mlt and python?

If not, consider running
```
$ sudo apt-get install python python-mlt3 
```
as that should allow you to install openshot.

---

### Post by rulymo21 on 2012-06-06
Didnt work.  Here is what I have:

E: Package 'python-mlt3' has no installation candidate
ruly@ruly:~$ sudo apt-get install python python-mlt3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-mlt3 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-mlt5:i386 python-mlt4:i386 python-mlt5 python-mlt4

E: Package 'python-mlt3' has no installation candidate

---

### Post by oldfred on 2012-06-06
Merged duplicate threads, Please do not create duplicates.

---

### Post by rulymo21 on 2012-06-07
Sorry.  Should of read the rules before creating a thread.  I happen to have Ubuntu 12.04 on all of my business  computers and we are down media production.

Again Sorry, 

Raul

---

### Post by klasik on 2012-06-11
i have same problem:

The following packages have unmet dependencies:
openshot: Depends: python (>= 2.5) but 2.7.3-0ubuntu2 is to be installed

---

### Post by klasik on 2012-06-11
any ideas how to fix that?

---

### Post by sarga on 2012-07-29
Hi, 

This is how I installed openshot with the same issue.

sudo add-apt-repository ppa:jonoomph/openshot-edge
sudo apt-get update
sudo apt-get install openshot openshot-doc


[https://answers.launchpad.net/openshot/+faq/1850](https://answers.launchpad.net/openshot/+faq/1850)

---

