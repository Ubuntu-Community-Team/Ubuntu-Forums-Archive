---
title: "installing Thunderbird 1.0.7 ??? (Solved)"
date: 2005-11-17
forum: Installation &amp; Upgrades
---

### Post by jmejedi on 2005-11-17
How do you install Thunderbird 1.0.7 on Breezy ??? I am trying to run "thunderbird" inside the thunderbird folder which is what is extracted after extracting the .tar.gz for the thunderbird download from Mozilla.

Thank you for your time,

JME

---

### Post by yesplease on 2005-11-17
Why dont you use synaptic?

Edit: I installed thunderbird 1.07 with synaptic. Synaptic shows information about the version you will install and its dependent packages and recommended packages ( and installs all that stuff if you want it). 

btw, great tutorial Aysiu

---

### Post by aysiu on 2005-11-17
Open a terminal and type ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
```

Let us know if you don't know where the terminal is.
Synaptic (previously mentioned) is the graphical version of apt-get (see the second link in my sig for more details).

---

### Post by jmejedi on 2005-11-18
Thank you guys...... everything is working just fne..... Take care,

JME

---

### Post by BorgCymru on 2005-11-25
I tried using this method and I got

richard@MrLappy:~$ sudo apt-get install  mozilla-thunderbird
Reading package lists... Done
Building dependency tree... Done
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-thunderbird has no installation candidate


how do I get thunderbird

Total Ubuntu newbie by the way :) so please be kind and keep the words simple

Thnks

---

### Post by aysiu on 2005-11-25
Does it make any difference if you type these two commands ```
sudo apt-get update
sudo apt-get install mozilla-thunderbird
``` instead of just the one command ```
sudo apt-get install mozilla-thunderbird
```?

---

