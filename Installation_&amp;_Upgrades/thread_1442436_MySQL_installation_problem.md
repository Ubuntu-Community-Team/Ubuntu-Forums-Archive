---
title: "MySQL installation problem"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by ArtemNY on 2010-03-30
When I try to install MySQL I get some problem:

> 
mycomputer@name:~$ aptitude install mysql-server mysql-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
[B][COLOR=Red]E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?[/COLOR][/B]
What does this mean? I don't have some permission. What permission? I logged in as one and only user of this OS.

During the 1st installation I ignored that but when MySQL didn't work I uninstalled it and tried again and here we go the same problem.



**[COLOR=Blue]OR[/COLOR]**



When I try to run the installation like this: 
> sudo apt-get install mysql-serverI don't get any errors first, but during the installation it says:
>  
bla bla bla
* Stopping MySQL database server mysqld                                 [ OK ] 
* Starting MySQL database server mysqld                                 [fail]
bla bla bla
and finishing with:
> E: Sub-process /usr/bin/dpkg returned an error code (1)
And during the installation it all the time says about some "dependency problems"

---

### Post by ArtemNY on 2010-03-30
Anyone? ;)

---

### Post by ArtemNY on 2010-03-30
Oh cmon people!
No one knows what the problem could be?

I stuck on this problem and can't go on. 
I went through 100s of forums, tried 1000s options and no help...

---

### Post by wojox on 2010-03-30
Try running:

```
sudo apt-get -f install
```

```
sudo apt-get upgrade
```

To finish downloading any dependencies.

---

### Post by wojox on 2010-03-30
I don't know how you even got it to install with the first quote? You needed to ```
sudo aptitude
``` to get it to install correctly.

As far as *** Starting MySQL database server mysqld [fail]**

What exactly does the blah blah blah say?

---

### Post by ArtemNY on 2010-03-30
> **wojox said:**
> Try running:

```
sudo apt-get -f install
``````
sudo apt-get upgrade
```To finish downloading any dependencies.

Tried it already for several times - no help! ((

I think there's some kind of lack of administration privileges. I may be wrong but I think so couse the system can't create some folders because I don't have full access to the root folder.

---

### Post by ArtemNY on 2010-03-30
> **wojox said:**
> I don't know how you even got it to install with the first quote? You needed to ```
sudo aptitude
``` to get it to install correctly.

As far as *** Starting MySQL database server mysqld [fail]**

What exactly does the blah blah blah say?

I used this [http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) instruction.

Tried it ```
sudo aptitude
```The same story



That's what I get (full text) after repeating the installation (w/o uninstallation of broken setup).
The same text I get on a fresh installation but it says how much space is going to be used etc but error message is the same.
> 
mycomp@name:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                                                                                                                                                [ OK ] 
 * Starting MySQL database server mysqld                                                                                                                                                               [COLOR=Red] [fail][/COLOR] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.1; however:
  Package mysql-server-5.1 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.1
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)



---

### Post by wojox on 2010-03-30
Try uninstalling it again:

```
sudo dpkg --purge --force-all mysql-server
```

Then restart your computer and reinstall.

---

### Post by ArtemNY on 2010-03-30
> **wojox said:**
> Try uninstalling it again:

```
sudo dpkg --purge --force-all mysql-server
```Then restart your computer and reinstall.

Ok here we go attempts to uninstall:
```

my@name:~$ sudo apt-get remove mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.1 (5.1.37-1ubuntu5.1) ...
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.1
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```

my@name:~$ sudo dpkg --purge --force-all mysql-server
dpkg: warning: ignoring request to remove mysql-server which isn't installed.

```



Is there any choice to install/uninstall it with my own hands? I mean unpack, put all folders in appropriate places, code all configs myself?

---

### Post by iponeverything on 2010-03-30
sure, it's pretty easy to download the mysql source, build it and install it. I think just matter of untaring it doing a ./configure and make and make install. grab these first though.

sudo apt-get install build-essential
sudo apt-get build-dep mysql-server-5.1

---

### Post by ArtemNY on 2010-03-30
> **iponeverything said:**
> 
sudo apt-get install build-essential

Same error. Fail to start.

---

### Post by wojox on 2010-03-30
What does this return:

```
dpkg -s mysql
```

---

### Post by ArtemNY on 2010-03-30
> **wojox said:**
> What does this return:

```
dpkg -s mysql
```


> my@name:~$ dpkg -s mysql
Package `mysql' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

This is correct. I uninstall it one more time. For the 30th time.

I strongly believe there's some permission problem with writing to dpkg and/or mysqld folders.

---

