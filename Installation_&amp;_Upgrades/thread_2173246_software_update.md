---
title: "software update"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by Ikenna_Onwuzuka on 2013-09-08
Hi, does anyone know how i can update a particular software/application without using the conventional "sudo apt-get update" on ubuntu 13.04 because i realised Canonical does not provide updates for some applications

---

### Post by ajgreeny on 2013-09-08
Software such as?

---

### Post by deadflowr on 2013-09-08
Do you mean upgrading to newer versions of said software?
(ala libreoffice 3.5> libreoffice 4.1)
Then yes, Ubuntu devs don't provide those for some software.
They like to freeze the versions per their version of Ubuntu.

Ubuntu devs will provide updates for any package you install through the default repositories.
And FYI, running apt-get update doesn't install any updates.It only refreshes the package list.
You need to run apt-get upgrade to actually update.

On 13.04 just run software updater. It automagically runs apt-get update and the lists the availble updates.Which you can then install by clicking OK, or something.

---

### Post by Buntu Bunny on 2013-09-08
If you've the software's PPA, then you should be able to sudo apt-get for updating your software list and upgrading packages.

---

### Post by Ikenna_Onwuzuka on 2013-09-09
@ajgreeny ubuntu swc has only librecad 1.0.2+nolibs-1build1 but i want upgrading it to 2.0.0 and I dont even know how to get the software's PPA to upgrade it

---

### Post by ajgreeny on 2013-09-09
You can try adding the ppa ([https://launchpad.net/~librecad-dev/+archive/librecad-daily](https://launchpad.net/~librecad-dev/+archive/librecad-daily)) to your software sources by following the instruction at the link.

Be warned that it is beta software, and a daily build, so there may be a few bugs, but it is worth a try.
```
sudo add-apt-repository ppa:librecad-dev/librecad-daily
```should do it for you, then update and upgrade.

---

### Post by Ikenna_Onwuzuka on 2013-09-10
I tried it and it worked like charm, thanks alot :D

---

### Post by ajgreeny on 2013-09-10
Wonderful!

Can you go to Thread Tools at the top of the thread and mark this problem as SOLVED.

---

