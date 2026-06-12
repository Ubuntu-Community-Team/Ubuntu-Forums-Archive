---
title: "jdk and path problem"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by frank05 on 2005-08-11
I've tried setting up the java sdk1.5 with the self extracting binary (following the advice found here: [https://wiki.ubuntu.com/Java](https://wiki.ubuntu.com/Java)) but I am having trouble setting up the path variable in bash. The jdk is installed to /usr/jdk1.5.0_04. I changed the path in /etc/profile however i found this only works for login shells. When I run a terminal on gnome the path variable does not include the jdk's bin directory. 
Basically, if somone could tell me where non-login shells have their path variable set I'd be much closer to a solution.

Thanks for any help!


PS I've noticed there's a /etc/environment file. Should be putting environment variables here? If so how?

---

### Post by scoon on 2005-08-11
Hey there, 

The problem is becuase gdm does not seem to use /etc/profile for anything.  Take a look at gdm.conf and add your ENV stuff there.

regards, 

scoon

---

### Post by parapete on 2005-08-11
or, put all of the extra path stuff in your ~/.bashrc...mine has the following two
lines at the end:

JAVA_HOME=/opt/jdk1.5.4_04

PATH=$PATH:$JAVA_HOME/bin

(you'd obviously have JAVA_HOME=/usr/jdk1.5.4_04)

bye bye

pete

---

### Post by frank05 on 2005-08-11
Thanks guys that really did the trick. I ended up editing the /etc/bash.bashrc file because I wanted all users to have the java path. 
And I don't think I would have been able to find where gnome was getting its path values from without scoons help.

Thanks again!  :smile:

---

