---
title: "PlayOnLinux &amp; tth-mscorefonts errors"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by scoobyd on 2011-01-31
Hi,

I think I interrupted one of the setup processes and since then, there has been an error every time I try to install something.

Taking PlayaOnLinux: If if try to install it using the Software Centre, it gives me this error:

installArchives() failed: debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package playonlinux.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 217722 files and directories currently installed.)
Unpacking playonlinux (from .../playonlinux_3.7.6-1_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_NZ.UTF8.cache...
Processing triggers for python-support ...
Setting up wine1.2 (1.2.2-0ubuntu2~maverick2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.5.7-4) ...
No apport report written because MaxReports is reached already
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.2; however:
  Package wine1.2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of playonlinux:
 playonlinux depends on wine | wine-unstable; however:
  Package wine is not configured yet.
  Package wine1.2 which provides wine is not configured yet.
  Package wine-unstable is not installed.
dpkg: error processing playonlinux (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 wine1.2
 man-db
 wine
 playonlinux
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up wine1.2 (1.2.2-0ubuntu2~maverick2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of wine:
 wine depends on wine1.2; however:
  Package wine1.2 is not configured yet.
dpkg: error processing wine (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of playonlinux:
 playonlinux depends on wine | wine-unstable; however:
  Package wine is not configured yet.
  Package wine1.2 which provides wine is not configured yet.
  Package wine-unstable is not installed.
dpkg: error processing playonlinux (--configure):
 dependency problems - leaving unconfigured



When trying to install ttf-mscorefonts (which is where I think the original problem started) I get this error message:

E: wine1.2: subprocess installed post-installation script returned error exit status 1
E: man-db: subprocess installed post-installation script returned error exit status 1
E: wine: dependency problems - leaving unconfigured
E: playonlinux: dependency problems - leaving unconfigured
E: ttf-mscorefonts-installer: subprocess installed post-installation script returned error exit status 1


Any ideas how to resolve this?

Thanks

---

### Post by sikander3786 on 2011-01-31
Welcome to the forums :-)

First of all resource temporary unaavailale message appears when some other package manager like Software Center, apt-get, Synaptic or Update Manager is running and you can't run any of them simultaneously with another. So close all the package managers, log out and log back in. Then from Applications > Accessories > Terminal, paste the _complete_ output of following commands.

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

If it gives you an option for configuration of fonts package, press <Tab> and then <Enter> to make sure choice.

---

### Post by scoobyd on 2011-01-31
Thanks! It works :)

---

### Post by darknuts on 2011-02-20
I tried it and this is what I got. All of my update and package programs are closed. Unless there is something running that I can't see.

```

bearcat@bearcat8f:~$ sudo dpkg --configure -a
Setting up man-db (2.5.7-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
 wine1.2
bearcat@bearcat8f:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.5.7-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.2
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by sikander3786 on 2011-02-20
Try,
```
sudo apt-get install --reinstall wine1.2 man-db
```

If that doesn't work, try these one-by-one.

```
sudo apt-get remove --purge wine1.2 man-db
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get install -f
```

Please post the outputs.

---

### Post by darknuts on 2011-02-20
The results:

```

bearcat@bearcat8f:~$ sudo apt-get install --reinstall wine1.2 man-db
[sudo] password for bearcat: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up wine1.2 (1.2.2-0ubuntu2~lucid1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up man-db (2.5.7-2ubuntu1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 wine1.2
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ sudo apt-get remove --purge wine1.2 man-db
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-user-guide* gnome-user-guide-en* man-db* startupmanager*
  ubuntu-desktop* ubuntu-docs* ubuntu-standard* wine1.2* yelp*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 376MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 188239 files and directories currently installed.)
Removing startupmanager ...
Purging configuration files for startupmanager ...
Removing ubuntu-docs ...
Removing ubuntu-desktop ...
Removing gnome-user-guide-en ...
Removing gnome-user-guide ...
Removing yelp ...
Purging configuration files for yelp ...
Removing ubuntu-standard ...
Removing man-db ...
Purging configuration files for man-db ...
  Removing catpages as well as /var/cache/man hierarchy.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--purge):
 subprocess installed post-removal script returned error exit status 1
Removing wine1.2 ...
update-binfmts: warning: /var/lib/binfmts/wine does not exist; nothing to do! 
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--purge):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for python-support ...
Processing triggers for menu ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for doc-base ...
Processing 1 removed doc-base file(s)...
Registering documents with scrollkeeper...
Processing triggers for python-support ...
Errors were encountered while processing:
 man-db
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ sudo apt-get clean
bearcat@bearcat8f:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bearcat@bearcat8f:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine1.2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 88.0MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 178803 files and directories currently installed.)
Removing wine1.2 ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ 


```

It looks like the file /var/cache/debconf/config.dat is the culprit but how do I find out what program has it locked down? I dread ever installing that POS program wine...

---

### Post by sikander3786 on 2011-02-20
```
sudo rm /var/cache/debconf/config.dat
```

```
sudo apt-get remove --purge wine1.2
```

```
sudo apt-get install -f
```

---

### Post by darknuts on 2011-02-20
```

bearcat@bearcat8f:~$ sudo rm /var/cache/debconf/config.dat
[sudo] password for bearcat: 
bearcat@bearcat8f:~$ sudo apt-get remove --purge wine1.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine1.2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 88.0MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 178803 files and directories currently installed.)
Removing wine1.2 ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  wine1.2
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 88.0MB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 178803 files and directories currently installed.)
Removing wine1.2 ...
debconf: DbDriver "passwords" warning: /var/cache/debconf/passwords.dat is locked by another process: Resource temporarily unavailable
debconf: DbDriver "templatedb": /var/cache/debconf/templates.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing wine1.2 (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 wine1.2
E: Sub-process /usr/bin/dpkg returned an error code (1)
bearcat@bearcat8f:~$ 


```

Now it's '/var/cache/debconf/passwords.dat' and ' /var/cache/debconf/templates.dat'. Should I repeat the process for them as well? Thanks for your help by the way.

---

### Post by sikander3786 on 2011-02-20
I am not sure removing all files one by one will help. Instead of removing them, try renaming them and try removing wine1.2 again.

```
sudo mv /var/cache/debconf/passwords.dat /var/cache/debconf/passwords.dat.bad
sudo mv /var/cache/debconf/templates.dat /var/cache/debconf/templates.dat.bad
```

You can later restore those files if needed.

---

### Post by darknuts on 2011-02-22
Well, it looks like that did it. Now I have a different error msg when I try to update virtual box but I dont think its related to wine. Thanks for your help!

---

### Post by sikander3786 on 2011-02-22
> **darknuts said:**
> Well, it looks like that did it. Now I have a different error msg when I try to update virtual box but I dont think its related to wine. Thanks for your help!
You are Welcome :-)

You can post the other error here as well and we'll try to help you on that also.

---

### Post by darknuts on 2011-02-25
Actually that other error was just because the program i was trying to update was still running. Everything's good now. Thanks.

---

