---
title: "[SOLVED] Openoffice.org update problem"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by indikid on 2008-06-23
[COLOR=Blue][B][COLOR=DarkRed]
Finally managed to get things back online.... :) I've posted the my solution at[/COLOR] [http://ubuntuforums.org/showthread.php?t=832995&page=3](http://ubuntuforums.org/showthread.php?t=832995&page=3)...[/B][/COLOR]



People need help with this... My openoffice installation is screwed up! Did an udate recently and there was an error in the package. Since then onwards openoffice is giving me errors. I tried to reinstall but got the same output. Removed part if openoffice through synaptic and now I'm stuck with an error that says that openoffice has unmet dependencies. This is what I got when i tried to reinstall the program through terminal:

paul@paul-desktop:~$ sudo apt-get install --reinstall openoffice.org
[sudo] password for paul:
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:

openoffice.org: Depends: openoffice.org-base but it is not going to be installed
Depends: openoffice.org-core (= 1:2.4.1-1ubuntu1) but it is not going to be installed
Depends: openoffice.org-draw but it is not going to be installed
Depends: openoffice.org-filter-binfilter but it is not going to be installed
Depends: openoffice.org-filter-mobiledev but it is not going to be installed
Depends: openoffice.org-impress but it is not going to be installed
Depends: openoffice.org-java-common (> 2.2.0-4) but it is not going to be installed
Depends: openoffice.org-math but it is not going to be installed
Depends: openoffice.org-officebean but it is not going to be installed
Depends: openoffice.org-writer2latex but it is not going to be installed
openoffice.org-calc: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
openoffice.org-style-human: Depends: openoffice.org-common (= 1:2.4.1-1ubuntu1) but it is not going to be installed
openoffice.org-writer: Depends: openoffice.org-base-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
Depends: openoffice.org-core (= 1:2.4.0-3ubuntu6) but it is not going to be installed
Depends: python-uno (>= 1:2.4.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
paul@paul-desktop:~$ 

N when i tried sudo apt-get -f install:

paul@paul-desktop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
openoffice.org-base-core openoffice.org-calc openoffice.org-common
openoffice.org-core openoffice.org-writer python-uno
Suggested packages:
openoffice.org-base openoffice.org-style-hicontrast
openoffice.org-style-industrial openoffice.org-gcj
Recommended packages:
gij java-gcj-compat openjdk-6-jre sun-java5-jre sun-java6-jre java2-runtime
openoffice.org-filter-binfilter openoffice.org-java-common
openoffice.org-writer2latex
The following NEW packages will be installed:
openoffice.org-base-core openoffice.org-common openoffice.org-core
python-uno
The following packages will be upgraded:
openoffice.org-calc openoffice.org-writer
2 upgraded, 4 newly installed, 0 to remove and 42 not upgraded.
3 not fully installed or removed.
Need to get 0B/48.8MB of archives.
After this operation, 167MB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing openoffice.org-calc (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
dpkg: error processing openoffice.org-writer (--remove):
Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.
Errors were encountered while processing:
openoffice.org-calc
openoffice.org-writer
E: Sub-process /usr/bin/dpkg returned an error code (1)
paul@paul-desktop:~$

Does anyone have a solution to this. Its almost been a week now n I still haven't been able to get things right... People pl help!!! :( I've got a AMD 64 bit system and am running Ubuntu for AMD (V - 8.04)....

---

### Post by ajgreeny on 2008-06-23
Sounds like you need to purge everything in open office and start again.  Use apt-get or synaptic to purge all the OO packages, restart to ensure they have all gone and then reinstall.

---

### Post by Archmage on 2008-06-23
Did you look if there are new packages for Openoffice?

```
sudo aptitude update ; sudo aptitude safe-upgrade
```

---

### Post by indikid on 2008-06-23
I tried to reinstall but didn't work. Tried to purge the entire pack but that didn't work either. I keep coming up with an error that says oo has unmet dependencies!! Any ideas as to what can be done to my sorry state of affairs???  

Thanks for the help guys... but by the look of things i think its gonna take me a lot more to get to the solution!

---

