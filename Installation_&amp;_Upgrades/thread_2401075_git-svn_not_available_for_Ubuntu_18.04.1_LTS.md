---
title: "git-svn not available for Ubuntu 18.04.1 LTS"
date: 2018-09-13
forum: Installation &amp; Upgrades
---

### Post by raych on 2018-09-13
New to forum, and not sure this is the right place to ask this question.

I'm have problems installing the git-svn package on Ubuntu 18.04.1 LTS using:

sudo apt-get install git-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
 git-svn : Depends: git (> 1:2.19.0) but 1:2.17.1-1ubuntu0.1 is to be installed
           Depends: libsvn-perl but it is not installable
           Depends: libterm-readkey-perl but it is not installable
E: Unable to correct problems, you have held broken packages.

Any help would be appreciated (I've also posted a fuller description on StackOverflow: [https://stackoverflow.com/questions/52310564/git-svn-not-available-for-ubuntu-18-04-1-lts](https://stackoverflow.com/questions/52310564/git-svn-not-available-for-ubuntu-18-04-1-lts)).

---

### Post by deadflowr on 2018-09-14
what does
```
sudo apt-get install -f
```
show?

---

