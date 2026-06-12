---
title: "gcc install fails on Ubuntu 14.04:  broken packages"
date: 2017-12-05
forum: Installation &amp; Upgrades
---

### Post by databaseman77 on 2017-12-05
I'm on Ubuntu 14.04 as verified by "lsb_release -a"
   Description:    Ubuntu 14.04.5 LTS


And I would like to install gcc but the install fails with warnings about broken packages:
   DZ> sudo -i
   R> apt-get update
   no errors
   Reading package lists... Done


   R> apt-get install gcc
   Reading package lists... Done
   Building dependency tree
   Reading state information... Done
   You might want to run 'apt-get -f install' to correct these:
   The following packages have unmet dependencies:
   gcc : Depends: cpp (>= 4:4.8.2-1ubuntu6) but it is not going to be installed
         Depends: gcc-4.8 (>= 4.8.2-5~) but it is not going to be installed
         Recommends: libc6-dev but it is not going to be installed or
                     libc-dev
   libgcc1 : Depends: gcc-4.9-base (= 4.9.3-0ubuntu4) but it is not going to be installed
   libstdc++6 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04.3) but it is not going to be installed
   E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


I found an online recommendation to edit /var/lib/dpkg/status and remove the sections referring to
two gcc package versions, but that had no effect.


What is the most efficient method to fix this issue?

---

### Post by Kirk Schnable on 2017-12-06
Not to preach the obvious here, but it says to run "apt-get -f install" in the error output.  I have had this fix things for me before.  Have you tried it?  What happens when you run that?

---

### Post by databaseman77 on 2017-12-08
The reason I was reluctant to run "apt-get -f install" was because it gave me an alarming prompt and told me to type "Yes, do as I say!"  It's only a development machine so I gave it a go.  Today, the machine won't even boot I guess because it doesn't have much of a kernel.  One of the system administrators is going to reimage the box.  I guess that's one way to fix an install problem!  ;-)  Apparently the computer had some severe install and dependency problems.  They should be fixed now.  Kind of funny actually.

---

