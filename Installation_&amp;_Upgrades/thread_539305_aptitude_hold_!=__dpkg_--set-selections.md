---
title: "aptitude hold !=  dpkg --set-selections"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by kaipower on 2007-08-31
hi,

I have made a few assumptions when I was using apt-get, aptitude, apt-cache and synaptic.

Number one, they are just front-ends to dpkg and its database.
Hence, whatever I do in apt-get/aptitude/synaptic, should coexist with each other.

An analogy will be database front-end tools like phpmyadmin and mysql-client statements.
They are just front-ends to the database. Whatever modification statements made to the data should be made stateful and propagated to the database.

However, this does not seem to be the case. At least not with the following case:

aptitude hold <package name> != echo <package name> hold | dpkg --set-selections 

Do try the following and let me know about your results:
1) aptitude hold <package name> 
2) dpkg --get-selections | grep <package name>

You will then find that the status of the package is not set to hold.

Could someone explain the above behavior?

Thanks and best regards.

---

### Post by Fisslefink on 2008-04-04
I observe the same exact behavior with Ubuntu Feisty Fawn 7.04...

Running aptitude first, I get...
```
mythtv@mythtvbox:/usr/src$ sudo aptitude hold netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  netatalk 
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

```

Checking with dpkg --get-selections, I get...
```
mythtv@mythtvbox:/usr/src$ dpkg --get-selections|grep netatalk
netatalk                                        install
```

I decided to test an apt-get upgrade and make sure this is really a problem:
```
 mythtv@mythtvbox:/usr/src$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  netatalk
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/710kB of archives.
After unpacking 164kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
 
```

It appears you're right... I had to run the dpkg --set-selections command for apt-get to know what to do:
```
 mythtv@mythtvbox:/usr/src$ su
Password: 
root@mythtvbox:/usr/src# echo 'netatalk hold' | dpkg --set-selections
root@mythtvbox:/usr/src# exit
exit
mythtv@mythtvbox:/usr/src$ dpkg --get-selections|grep netatalk
netatalk                                        hold
 
```


This time, apt-get upgrade knows to hold the package:
```
 mythtv@mythtvbox:/usr/src$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  netatalk
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
 
```

---

