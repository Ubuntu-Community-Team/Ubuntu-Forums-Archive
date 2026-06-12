---
title: "Ubuntu 16.04 - &quot;dpkg --configure -a&quot; with no success"
date: 2019-12-12
forum: Installation &amp; Upgrades
---

### Post by isagarran2 on 2019-12-12
Ubuntu 16.04 : Linux  4.4.0-148-generic #174-Ubuntu SMP Tue May 7 12:20:14 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Hello,

Since three weeks, I've an issue with my Ubuntu. I can't use Synaptic or any dpkg command as there is always a process dpkg running.

```

#ps ef |grep dpkg
root      4428  4427  0 déc.11 pts/0  00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4
root      4434  4428  0 déc.11 pts/0  00:00:00 /bin/sh /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4
```

If I kill the process, of course, I've to run "dpkg --configure -a". 
```
$ sudo dpkg --configure -a 
Paramétrage de docker.io (18.09.7-0ubuntu1~16.04.5) ...
insserv: warning: script 'S15notes-enable-ptrace' missing LSB tags and overrides
insserv: warning: script 'K01vpnagentd_init' missing LSB tags and overrides
insserv: warning: script 'K01ibm-wclient' missing LSB tags and overrides
```

Then the that's still wait forever.


Looking at process, I see
```

#ps ef |grep dpkg
root      4419  3220  0 déc.11 pts/0  00:00:00 sudo dpkg --configure -a
root      4427  4419  0 déc.11 pts/0  00:00:00 dpkg --configure -a
root      4428  4427  0 déc.11 pts/0  00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4
root      4434  4428  0 déc.11 pts/0  00:00:00 /bin/sh /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4

```
in dpkg.log
```
2019-12-11 15:38:50 startup packages configure
2019-12-11 15:38:50 configure docker.io:amd64 18.09.7-0ubuntu1~16.04.5 <none>
2019-12-11 15:38:50 status half-configured docker.io:amd64 18.09.7-0ubuntu1~16.04.5
2019-12-11 15:40:04 configure util-linux:amd64 2.27.1-6ubuntu3.9 <none>
2019-12-11 15:40:04 status half-configured util-linux:amd64 2.27.1-6ubuntu3.9
2019-12-11 15:41:35 startup packages configure
2019-12-11 15:41:35 configure docker.io:amd64 18.09.7-0ubuntu1~16.04.5 <aucune>
2019-12-11 15:41:35 status half-configured docker.io:amd64 18.09.7-0ubuntu1~16.04.5

```

in syslog
```
Dec 11 15:40:04 HanaYoridango AptDaemon.Worker: CRITICAL: docker.io: subprocess installed post-installation script was killed by signal (Killed)
Dec 11 15:40:04 HanaYoridango org.debian.apt[1260]: 15:40:04 AptDaemon.Worker [CRITICAL]: docker.io: subprocess installed post-installation script was killed by signal (Killed)
Dec 11 15:40:04 HanaYoridango console-kit-daemon[2775]: console-kit-daemon[2775]: GLib-CRITICAL: Source ID 118 was not found when attempting to remove it
Dec 11 15:40:04 HanaYoridango console-kit-daemon[2775]: GLib-CRITICAL: Source ID 118 was not found when attempting to remove it
Dec 11 15:40:51 HanaYoridango gnome-session[3143]: /var/lib/dpkg/lock:
Dec 11 15:40:51 HanaYoridango /usr/lib/gdm3/gdm-x-session[3131]: Activating service name='com.ubuntu.OneConf'
Dec 11 15:40:51 HanaYoridango /usr/lib/gdm3/gdm-x-session[3131]: Successfully activated service 'com.ubuntu.OneConf'
Dec 11 15:40:51 HanaYoridango com.ubuntu.OneConf[3140]: WARNING:oneconf.hosts:Error in loading other_hosts file: [Errno 2] No such file or directory: '/home/jps/.cache/oneconf/0496667a33544fdf8008b764687a7a14/other_hosts'
Dec 11 15:40:59 HanaYoridango AptDaemon.Worker: INFO: Finished transaction /org/debian/apt/transaction/765693aec05c495ebb1ac16f0570d936
Dec 11 15:40:59 HanaYoridango org.debian.apt[1260]: /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning: Source ID 349 was not found when attempting to remove it
Dec 11 15:40:59 HanaYoridango org.debian.apt[1260]:   GLib.source_remove(id)
Dec 11 15:40:59 HanaYoridango org.debian.apt[1260]: /usr/lib/python3/dist-packages/aptdaemon/progress.py:491: Warning: Source ID 350 was not found when attempting to remove it
Dec 11 15:40:59 HanaYoridango org.debian.apt[1260]:   GLib.source_remove(id)
Dec 11 15:40:59 HanaYoridango org.debian.apt[1260]: 15:40:59 AptDaemon.Worker [INFO]: Finished transaction /org/debian/apt/transaction/765693aec05c495ebb1ac16f0570d936
Dec 11 15:40:59 HanaYoridango gnome-session[3143]: (gnome-software:3486): Gs-WARNING **: failed to call gs_plugin_refresh on apt: apt transaction returned result exit-failed
Dec 11 15:40:59 HanaYoridango gnome-session[3143]: (gnome-software:3486): Gs-WARNING **: failed to refresh the cache: no plugin could handle refresh
Dec 11 15:40:59 HanaYoridango console-kit-daemon[2775]: console-kit-daemon[2775]: GLib-CRITICAL: Source ID 127 was not found when attempting to remove it
Dec 11 15:40:59 HanaYoridango console-kit-daemon[2775]: GLib-CRITICAL: Source ID 127 was not found when attempting to remove it

```

Do you know hoit can be solved ? I can totally remove the package docker if needed.
I'll appreciate greatly any help

isagarran

---

### Post by Frogs Hair on 2019-12-12
Is there any 3rd party software or repositories in use ?

---

### Post by isagarran2 on 2019-12-12
Hello,
Thanks for your reply
Not sure to understand the answer. I saw that It tries to post install docker. so there is a dpkg process active. But I can't remove it. If I kill it then dpkg --configure -a launch it and then it waits forever. It seems docker post install never finishes.

```
#ps ef |grep dpkg
root      4419  3220  0 déc.11 pts/0  00:00:00 sudo dpkg --configure -a
root      4427  4419  0 déc.11 pts/0  00:00:00 dpkg --configure -a
root      4428  4427  0 déc.11 pts/0  00:00:00 /usr/bin/perl -w /usr/share/debconf/frontend /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4
root      4434  4428  0 déc.11 pts/0  00:00:00 /bin/sh /var/lib/dpkg/info/docker.io.postinst configure 18.09.7-0ubuntu1~16.04.4
```

---

### Post by Frogs Hair on 2019-12-12
I was referring to any software not from the official repository. Post the output of the following.
```
cat /etc/apt/sources.list
```


Also :```
 sudo apt update
```

---

### Post by isagarran2 on 2019-12-12
Hello,

Please find elements you requested :

```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-GNOME 16.04.3 LTS _Xenial Xerus_ - Release amd64 (20170801)]/ xenial main multiverse restricted universe


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ xenial main restricted
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ xenial universe
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial universe
deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates universe
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://fr.archive.ubuntu.com/ubuntu/ xenial multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial multiverse
deb http://fr.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://fr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
# deb-src http://fr.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu xenial partner
# deb-src http://archive.canonical.com/ubuntu xenial partner


deb http://security.ubuntu.com/ubuntu xenial-security main restricted
# deb-src http://security.ubuntu.com/ubuntu xenial-security main restricted
deb http://security.ubuntu.com/ubuntu xenial-security universe
# deb-src http://security.ubuntu.com/ubuntu xenial-security universe
deb http://security.ubuntu.com/ubuntu xenial-security multiverse
# deb-src http://security.ubuntu.com/ubuntu xenial-security multiverse

```
and 

```
$ sudo apt update
Atteint :1 http://fr.archive.ubuntu.com/ubuntu xenial InRelease
Atteint :2 http://fr.archive.ubuntu.com/ubuntu xenial-updates InRelease                                                                           
Atteint :3 http://ppa.launchpad.net/git-core/ppa/ubuntu xenial InRelease                                                                          
Atteint :4 http://fr.archive.ubuntu.com/ubuntu xenial-backports InRelease                                                                         
Atteint :5 http://security.ubuntu.com/ubuntu xenial-security InRelease                             
Atteint :6 http://security.ubuntu.com/ubuntu precise-security InRelease                             
Atteint :7 http://ocdc.dub.usoh.ibm.com/ocdc xenial-safe InRelease                    
Atteint :8 http://ocdc.dub.usoh.ibm.com/ocdc xenial-beta InRelease             
Atteint :9 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
292 paquets peuvent être mis à jour. Exécutez « apt list --upgradable » pour les voir.
W: http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease: la signature par la clé 630239CC130E1A7FD81A27B140976EAF437D05B5 utilise des algorithmes « digest » faibles (SHA1)

```
ocdc reposittory are my company repositories.

regards,
Isagarran

---

### Post by Frogs Hair on 2019-12-12
You have 3rd party repositories and 292 packages that need updating . I would start by removing docker and then run the following. ```
sudo apt upgrade
``` After the system is updated try installing the package again.

---

### Post by westie457 on 2019-12-12
This line in your 'apt update' is probably not helping. 

Atteint :6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security InRelease  

I have no idea how to remove this as it is not visible in your sources list.

---

### Post by ubfan1 on 2019-12-12
Check the /etc/apt/sources.list.d directory also.  Looks like it may contain some old repos.

---

### Post by isagarran2 on 2019-12-13
Hello,

Checking the directory

```
$ ls -alrt  /etc/apt/sources.list.d 
total 40
lrwxrwxrwx 1 root root   33 nov.   6  2017 ocdc.auto.list -> /var/opt/openclient/ocdc.apt.list
drwxr-xr-x 7 root root 4096 août  13 11:06 ..
-rw-r--r-- 1 root root   60 août  13 11:06 precise.list.save
-rw-r--r-- 1 root root  102 août  13 11:06 layer.list.save
-rw-r--r-- 1 root root  481 août  13 11:06 ocdc.auto.list.save
-rw-r--r-- 1 root root  193 août  13 11:06 slack.list.save
drwxr-xr-x 2 root root 4096 août  13 11:06 .
-rw-r--r-- 1 root root  128 août  13 11:06 git-core-ubuntu-ppa-xenial.list
-rw-r--r-- 1 root root  193 août  13 11:06 slack.list
-rw-r--r-- 1 root root  103 août  13 11:06 layer.list
-rw-r--r-- 1 root root   60 août  13 11:06 precise.list
```


```
$ cat /etc/apt/sources.list.d/ocdc.auto.list
# OCDC Apt sources file
# This file is managed by ocdc-repository, run 'sudo dpkg-reconfigure ocdc-repository' to change it
# Any edits you make to this file wil be overwritten
```


```
# Safe release
deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-safe IBM IBM-layer
deb-src [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-safe IBM IBM-layer
```


```
# Beta release
deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-beta IBM IBM-layer
deb-src [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-beta IBM IBM-layer
```


```
$ cat /etc/apt/sources.list.d/precise.list.save 
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
```


```
$ cat /etc/apt/sources.list.d/layer.list.save 
#deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-safe IBM IBM-layer #commented by ocdc-repsitory package
```


```
$ cat /etc/apt/sources.list.d/ocdc.auto.list.save 
# OCDC Apt sources file
# This file is managed by ocdc-repository, run 'sudo dpkg-reconfigure ocdc-repository' to change it
# Any edits you make to this file wil be overwritten
```


```
# Safe release
deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc)     xenial-safe IBM IBM-layer
deb-src [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-safe IBM IBM-layer
```


```
# Beta release
deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc)     xenial-beta IBM IBM-layer
deb-src [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-beta IBM IBM-layer
```


```
$ cat /etc/apt/sources.list.d/slack.list.save 
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [https://packagecloud.io/slacktechnologies/slack/debian/](https://packagecloud.io/slacktechnologies/slack/debian/) jessie main
```


```
$ cat /etc/apt/sources.list.d/git-core-ubuntu-ppa-xenial.list 
deb [http://ppa.launchpad.net/git-core/ppa/ubuntu](http://ppa.launchpad.net/git-core/ppa/ubuntu) xenial main
# deb-src [http://ppa.launchpad.net/git-core/ppa/ubuntu](http://ppa.launchpad.net/git-core/ppa/ubuntu) xenial main
```


```
$ cat /etc/apt/sources.list.d/slack.list
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [https://packagecloud.io/slacktechnologies/slack/debian/](https://packagecloud.io/slacktechnologies/slack/debian/) jessie main
```


```
$ cat /etc/apt/sources.list.d/layer.list
# deb [http://ocdc.dub.usoh.ibm.com/ocdc](http://ocdc.dub.usoh.ibm.com/ocdc) xenial-safe IBM IBM-layer #commented by ocdc-repsitory package
```


```
$ cat /etc/apt/sources.list.d/precise.list
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main
```

What could be the next step ? Do you see any issues in my configuration ?
Thanks for your help.

Isagarran

---

### Post by Frogs Hair on 2019-12-13
Look in software sources /software & updates both in the Ubuntu software and Other software tab for unneeded software sources that can be removed. You can also carefully and directly edit the unneeded sources on the  list from gedit opened from the terminal. I can't  give any advice on your work related repositories.   ```
 sudo -H gedit /etc/apt/sources.list
```

---

