---
title: "Trying and failing to install Sun Java 6, need help please :)"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by ClutchHunter on 2012-02-22
This is the error I get when I try installing Sun Java 6 bin + jre via Synaptic Package Manager:

```
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Selecting previously deselected package sun-java6-jre.
(Reading database ... 170379 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-bin (from .../sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb
 /var/cache/apt/archives/sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up man-db (2.6.0.2-2) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db

```

Help please :)

---

### Post by cortman on 2012-02-22
This is a very simple problem.
Ubuntu uses the programs **apt** and **dpkg** for all package handling (installing, removing, updating, upgrading, etc.). To prevent multiple package management processes from running at once, apt or dpkg opens or "locks" an empty file named (appropriately) "lock", in either /var/lib/apt/lists/ (for apt processes) or /var/lib/dpkg/ (for dpkg processes). If this file is already locked by an apt or dpkg process, no other process of that nature can run.
That's the in-depth explanation. Put shortly, you apparently have another apt or dpkg process running. This could be in the form of Synaptic Package Manager, or the USC, as they both utilize apt. You can either log out and back in, or run

```
sudo killall *apt* *dpkg*
```

in a terminal (Ctrl+Alt+t) which will kill these processes. You should then be able to successfully run your package management program.

---

### Post by zeljkojagust on 2012-02-23
If all fails, try to do it manual way, here's how to: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by ClutchHunter on 2012-02-23
> **cortman said:**
> This is a very simple problem.
Ubuntu uses the programs **apt** and **dpkg** for all package handling (installing, removing, updating, upgrading, etc.). To prevent multiple package management processes from running at once, apt or dpkg opens or "locks" an empty file named (appropriately) "lock", in either /var/lib/apt/lists/ (for apt processes) or /var/lib/dpkg/ (for dpkg processes). If this file is already locked by an apt or dpkg process, no other process of that nature can run.
That's the in-depth explanation. Put shortly, you apparently have another apt or dpkg process running. This could be in the form of Synaptic Package Manager, or the USC, as they both utilize apt. You can either log out and back in, or run

```
sudo killall *apt* *dpkg*
```

in a terminal (Ctrl+Alt+t) which will kill these processes. You should then be able to successfully run your package management program.


I ran the command you gave me and I got:

```
*apt*: no process found
*dpkg*: no process found
```


I then tried again this command, hoping me restarting the computer after a nights sleep would have helped:

```
sudo apt-get install sun-java6-bin sun-java6-jre
```


I then got the following error(s):

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by cortman on 2012-02-23
Do you have the update manager running?
Another, slightly more involved way to kill processes is to run

```
ps -ef | grep apt
ps -ef | grep dpkg
```

and then run

```
sudo kill -9 process_id
```

Substituting the actual four digit process ID (the second column of numbers from the left) for "process_id".

---

### Post by ClutchHunter on 2012-02-23
> **cortman said:**
> Do you have the update manager running?
Another, slightly more involved way to kill processes is to run

```
ps -ef | grep apt
ps -ef | grep dpkg
```

and then run

```
sudo kill -9 process_id
```

Substituting the actual four digit process ID (the second column of numbers from the left) for "process_id".

The responses I got from the two commands at the top, please let me know what to do now :)

```
root      8876     1  0 01:19 ?        00:00:00 /usr/bin/python /usr/share/apt-xapian-index/update-apt-xapian-index-dbus
sam      12109     1  0 02:16 ?        00:00:00 /bin/sh /usr/bin/synaptic-pkexec
root     12110 12109  0 02:16 ?        00:00:13 /usr/sbin/synaptic
root     12157 12110  0 02:19 ?        00:00:00 [synaptic] <defunct>
sam      18729 18673  0 16:22 pts/2    00:00:00 grep --color=auto apt

```
```
root      8409     1  0 01:05 ?        00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/tmp.ci/preinst install
root      8416  8409  0 01:05 ?        00:00:00 /bin/sh -e /var/lib/dpkg/tmp.ci/preinst install
sam      18731 18673  0 16:22 pts/2    00:00:00 grep --color=auto dpkg

```

---

### Post by cortman on 2012-02-23
Run the second command I gave above

```
sudo kill -9 process_id
```

The id's may have shifted by now, but for apt it'd be

```
sudo kill -9 8876 12109 12110 12157
```

---

### Post by ClutchHunter on 2012-02-23
> **cortman said:**
> Run the second command I gave above

```
sudo kill -9 process_id
```

The id's may have shifted by now, but for apt it'd be

```
sudo kill -9 8876 12109 12110 12157
```

Okay, now I'm getting:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sun-java6-plugin ia32-sun-java6-plugin sun-java6-fonts ttf-kochi-gothic ttf-sazanami-gothic
  ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed
  sun-java6-bin sun-java6-jre
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/35.1 MB of archives.
After this operation, 101 MB of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 170379 files and directories currently installed.)
Unpacking sun-java6-jre (from .../sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Unpacking sun-java6-bin (from .../sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing /var/cache/apt/archives/sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 1
Processing triggers for menu ...
Errors were encountered while processing:
 /var/cache/apt/archives/sun-java6-jre_6.26-1~lffl~oneiric~ppa_all.deb
 /var/cache/apt/archives/sun-java6-bin_6.26-1~lffl~oneiric~ppa_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by cortman on 2012-02-23
Ok, do the apt and dpkg process kill procedure again, this time also run

```
ps -ef | grep debconf
```

and kill any processes that match it. Now run

```
sudo apt-get purge sun-java6-bin 
sudo apt-get purge sun-java6-jre
```

The official Sun java products have been removed from the repositories, so run

```
sudo apt-get update
```

to update the repository list. The openJDK product is virtually identical and should work for you unless you know for certain you need Sun java. You can install it with

```
sudo apt-get install openjdk-6-jdk
sudo apt-get install openjdk-6-jre
```

---

### Post by ClutchHunter on 2012-02-23
> **cortman said:**
> Ok, do the apt and dpkg process kill procedure again, this time also run

```
ps -ef | grep debconf
```

and kill any processes that match it. Now run

```
sudo apt-get purge sun-java6-bin 
sudo apt-get purge sun-java6-jre
```

The official Sun java products have been removed from the repositories, so run

```
sudo apt-get update
```

to update the repository list. The openJDK product is virtually identical and should work for you unless you know for certain you need Sun java. You can install it with

```
sudo apt-get install openjdk-6-jdk
sudo apt-get install openjdk-6-jre
```

Okay thanks for all the help so far, I've got it to the point that it will try to install sun java(for Minecraft, says it's required, and it didn't work with Open so...).

I'm on a package configuration screen with an agreement and an <Ok> bit of text at the bottom. Problem is I don't know how to proceed and accept... tried hitting enter, down etc. I can scroll but nothing more :/

---

### Post by ClutchHunter on 2012-02-23
Here:

[IMG]http://oi44.tinypic.com/xf0sap.jpg[/IMG]

---

### Post by ClutchHunter on 2012-02-23
Problem sorted!

Thanks for the help :popcorn:

---

### Post by cortman on 2012-02-23
Well, good- you installed the Sun java then? Did you follow the link given in post #3?
Mark this thread as [SOLVED] using the thread tools in the upper right, if you would. Good luck!

---

