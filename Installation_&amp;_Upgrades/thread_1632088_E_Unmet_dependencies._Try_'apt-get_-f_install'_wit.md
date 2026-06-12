---
title: "E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a soluti"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by ethanpk on 2010-11-27
I've been trying to install java and this is what i get when I put the command "sudo apt-get install sun-java6-jre sun-java6-plugin"

ethankelley@ubuntu:~$ sudo apt-get install sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 sun-java6-jre : Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not going to be installed or
                          ia32-sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not going to be installed
 sun-java6-plugin : Depends: sun-java6-bin (>= 6.22-0ubuntu1~10.10) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

how can I fix this

---

### Post by deanjm1963 on 2010-11-27
When you added the partner repository did you "update", either through synaptic or apt-get update? More often or not if the repositories aren't refreshed it can't find the packages.

---

