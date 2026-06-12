---
title: "Updates problem and installation of tomcat problem"
date: 2014-02-10
forum: Installation &amp; Upgrades
---

### Post by Ub_4Machine on 2014-02-10
Hi All,
I get the following message whenever I try to update my Ubuntu 12-04:

Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-updates/universe Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) precise-backports/universe Translation-en
W: Failed to fetch [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubun-tor/ppa/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

I guess the last two lines implies the update have not been successful? Any help will be greatly appreciated!
Besides, I tried to install tomcat and got the following error:
The following packages will be upgraded:
  libservlet3.0-java libtomcat7-java tomcat7 tomcat7-common
4 upgraded, 0 newly installed, 0 to remove and 484 not upgraded.
1 not fully installed or removed.
Need to get 0 B/3,797 kB of archives.
After this operation, 4,096 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Setting up install-info (4.13a.dfsg.1-8ubuntu2) ...
/etc/environment: line 1: JAVA_HOME: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am surprised since Java Home was properly set as well and seem to have been mentioned as one of the errors.
Any help will be greatly appreciated!
Thanking

---

### Post by Bucky Ball on 2014-02-10
Welcome. This PPA:

```
W: Failed to fetch http://ppa.launchpad.net/**ubun-tor**/pp...source/Sources 404 Not Found

W: Failed to fetch http://ppa.launchpad.net/**ubun-tor**/pp...-i386/Packages 404 Not Found
```

... is third party and either down for the moment or not maintained any longer. If you have added them from an old tutorial link then it is probably they no longer exist (be careful about old how-tos). Open Software Sources and disable (the 'sources' one as well), then:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get install tomcat
```

This will NOT upgrade you to a newer release, only upgrade whatever is in your current system that needs it. And there is some stuff that does. ;)

---

### Post by Ub_4Machine on 2014-02-10
Thanks alot Bucky Ball. I will give a try immidiately!

---

### Post by Bucky Ball on 2014-02-10
Good-o. Make sure you do the commands in the order above. Update must come before the upgrade command (something to remember).

---

