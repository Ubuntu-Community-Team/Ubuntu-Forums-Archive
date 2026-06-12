---
title: "Ubuntu does not upgrade in terminal"
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by abhishekkhandal on 2013-02-10
I'm trying to install any new upgrades available for ubuntu 12.10,though the GUI prompted about some updates but I accidentally cancelled it,and when I tried to install them through terminal I receive errors :

>abhishek@ubuntu:~$ sudo apt-get upgrade
>* No device configured for user "abhishek".
>[sudo] password for abhishek: 
>Reading package lists... Error!
>E: Encountered a section with no Package: header
>E: Problem with MergeList /var/lib/apt/lists/packages.medibuntu.org_dists_quantal_free_i18n_Translation-en
>E: The package lists or status file could not be parsed or opened.
>abhishek@ubuntu:~$ 

How to correct it,and how to correctthat "no device configured" ,I am the administrator and I don't know how did it started prompting "no device configured",it started few weeks ago when I updated ubuntu as the software updater prompted.
Also,how to remove or delink bad sources from software center?
here's the update log -> [http://pastebin.com/j0J0UVyN](http://pastebin.com/j0J0UVyN)

---

### Post by abhishekkhandal on 2013-02-10
The updates/upgrades can be installed easily through Software updater only when its prompted automatically ,but in terminal...

---

### Post by mörgæs on 2013-02-10
[http://ubuntuforums.org/showthread.php?t=1978554](http://ubuntuforums.org/showthread.php?t=1978554)

---

### Post by abhishekkhandal on 2013-02-11
> **mörgæs said:**
> [http://ubuntuforums.org/showthread.php?t=1978554](http://ubuntuforums.org/showthread.php?t=1978554)
Thanks,it worked.

---

