---
title: "java installation"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by selvavicto on 2010-02-13
evening i was installing sun-java6-jdk,at the time due to power problem the installation was broken ,again i was install i got this msg
   ''
""selva@selva-desktop:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jdk: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
selva@selva-desktop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?""
 i'm a new user 
ple help me.....

---

### Post by lukster91 on 2010-02-13
Hey there,

Have you tried typing in:

> sudo apt-get remove sun-java6-jdk

then 

> sudo apt-get install sun-java6-jdk

Might be all you need to do to get it working.

Alternatively, you should be able to install it through the Ubuntu Software centre, rather than through the terminal. If it says it's installed, try removing it, using the code i provided.

Best of luck.

---

### Post by lukster91 on 2010-02-13
Additional:

You could try doing:

> sudo apt-get install libnss3-dev 

and

> sudo apt-get install libnspr4-dev

They may get the files for you without doing this comand:

> sudo apt-get -f install

Make sure you type sudo.

---

