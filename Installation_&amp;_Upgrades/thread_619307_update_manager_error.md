---
title: "update manager error"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by ehcualp on 2007-11-21
there are a few updates i need to do with update manager, but when i click install updates i get an error.
```
E: tzdata: subprocess post-installation script returned error exit status 10
```
the updates that it says are needed t be updated are 
ubufox, as a proposed update, and
awn-core-applets-bzr, as an other update.
help?
forgot:
my terminal says this:
```

Setting up tzdata (2007i-0ubuntu0.710) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install. Trying to recover:
Setting up tzdata (2007i-0ubuntu0.710) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10

```
edit:
this problem affects all install programs on ubuntu, such as automatix2 and add/remove

---

### Post by ehcualp on 2007-11-21
bump!
i know theres somebody who can help me! :mad:

---

### Post by Pumalite on 2007-11-21
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)
Remove your automatix.

---

### Post by ehcualp on 2007-11-21
i have uninstalled automatix2 and it came up with this:
```

aaron@aaron-desktop:~$ sudo apt-get remove automatix2
[sudo] password for aaron:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package automatix2 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libwxgtk2.8-0 libgtk-jni
  tango-icon-theme-common tango-icon-theme libcairo-java libglib-jni
  libbcprov-java libwxbase2.8-0 libglib-java python-wxversion libgtk-java
  python-wxgtk2.8
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tzdata (2007i-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
(that last part looks similar, hmm, i wonder where its from...)
 
i then ran "apt-get autoremove" and it removed the miscellaneous files.
update manager still comes up with earlier said error(s).

(and what was the link about Malicious Commands about?)

---

### Post by Pumalite on 2007-11-21
Run:
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade

---

### Post by ehcualp on 2007-11-21
1)sudo dpkg --configure -a came up with this
```

aaron@aaron-desktop:~$ sudo dpkg --configure -a
Setting up tzdata (2007i-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata

```
2)sudo apt-get update came up with what it would normally
3)sudo apt-get upgrade came up with this:
```

aaron@aaron-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  awn-core-applets-bzr ubufox
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/2466kB of archives.
After unpacking 41.0kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up tzdata (2007i-0ubuntu0.7.10) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
Errors were encountered while processing:
 tzdata
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by santiagoward2000 on 2007-11-21
Hey! I had the same problem and found this thread:
[http://ubuntuforums.org/showthread.php?t=583024]("http://ubuntuforums.org/showthread.php?t=583024")
The solution I've used was to change my timezone to London, then use Update Manager. I don't really know why, but it worked! You can change it back after the updates are installed.
I hope this helps!

---

### Post by ehcualp on 2007-11-21
that did it. thank you :)

---

### Post by santiagoward2000 on 2007-11-21
> **ehcualp said:**
> that did it. thank you :)

You're welcome! :KS

---

### Post by professorYaffle on 2007-12-10
I've been having this update problem for a while as well, and the above suggestions did me no good. In particular the link suggesting changing the timezone temporarily to Europe/London wasn't helping since I'm already in that timezone :).

After a bit of experimentation I found a solution that worked for me which I thought I'd add here in case anyone else is in the same boat: temporarily delete the timezone completely!```
sudo rm /etc/timezone
sudo dpkg --configure tzdata
```(fortunately the default configuration was Europe/London) then I reran the update manager and the backlog of updates went through fine.

---

### Post by sandkiller on 2007-12-10
> **santiagoward2000 said:**
> Hey! I had the same problem and found this thread:
[http://ubuntuforums.org/showthread.php?t=583024]("http://ubuntuforums.org/showthread.php?t=583024")
The solution I've used was to change my timezone to London, then use Update Manager. I don't really know why, but it worked! You can change it back after the updates are installed.
I hope this helps!

Thx!

It also worked for me >D

---

