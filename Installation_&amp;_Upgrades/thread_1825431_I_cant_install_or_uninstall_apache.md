---
title: "I cant install or uninstall apache"
date: 2011-08-15
forum: Installation &amp; Upgrades
---

### Post by coolx on 2011-08-15
Hello,
Firstly I am beginner at linux. I had some problems at apache server and then I tryed to uninstall with these command;
---------------------------------------
apt-get remove --purge apache2
---------------------------------------

Then I try lots of install and unintall commands. Now there is nothing in "/etc/apache2" directory. The command's output is below,
When I try to install command, server is not seems installed;
----------------------------------------
root@cacti:/etc/apache2# apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
apache2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 169 not upgraded.
-----------------------------------------

Then Im trying to uninstall it, the output is below;
-----------------------------------------
root@cacti:/etc/apache2# apt-get -purge apache2
E: Command line option 'p' [from -purge] is not known.
root@cactitest:/etc/apache2# apt-get purge apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 169 not upgraded.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146549 files and directories currently installed.)
Removing apache2 ...
---------------------------------------------

And I found these command from net, I think its getting Apache componenents;

---------------------------------------------
root@cactitest:/etc/apache2# dpkg --get-selections | grep apache
apache2-mpm-itk                                 install
apache2-utils                                   install
apache2.2-bin                                   install
apache2.2-common                                install
libapache2-mod-php5filter                       install
---------------------------------------------


Why is this so hard to uninstall or install a progra to Linux? Isnt this should be easy like executing a command or clicking a button like in Windows? Or am I doing somethings wrong? Now there is nothing I can do and I still dont know is apache installed or uninstalled? In both ways server is not running.

---------------------------------------------
root@cactitest:/etc/apache2# service apache2 restart 
.: 49: Can't open /etc/apache2/envvars
--------------------------------------------

---

### Post by wojox on 2011-08-15
It isn't to hard you just need to remove all of it:

```
sudo apt-get --purge remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
```

---

### Post by raja.genupula on 2011-08-15
i think after uninstalling some thing , i didnt remember actually you should have to clean it files either by apt-get autoremove or clean , i am in confusion of this . 
                        even though you have uninstalled it , still those files will be in the system . thats why your facing this problem .

---

### Post by coolx on 2011-08-16
> **wojox said:**
> It isn't to hard you just need to remove all of it:

```
sudo apt-get --purge remove apache2 apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
```

Thanks for your answer wojox, but how could I guess or know these command line? I mean mpm-prefork, libapache2.2 or somethings.. Isnt just ""apt-get purge apache2" enough for uninstalling programs?

---

### Post by ashickur.noor on 2011-08-16
Use synaptic package manager, if you are totally new in Ubuntu or linux.

---

