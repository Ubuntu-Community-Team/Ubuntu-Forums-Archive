---
title: "packages not found"
date: 2019-03-27
forum: Installation &amp; Upgrades
---

### Post by twayta on 2019-03-27
Hello,

i'm new on ubuntu , and i'm using ubuntu 17.04 , the problem that when i try to install any software or librarie , i get this erreur :
impossible to find the package "name of the package"

---

### Post by jeremy31 on 2019-03-27
That is because the servers for 17.04 were shut down when it went EOL last January.  Ubuntu 17.04 only had 9 months of support

---

### Post by twayta on 2019-03-27
but i installed it in this week and what can i do?

---

### Post by jeremy31 on 2019-03-27
Install 18.04 over it as Ubuntu 18.04 is supported until April 2023

---

### Post by twayta on 2019-03-27
i tested so many version but each version has a problem . and i will work with a software that maybe the version 18.04 dont support it

---

### Post by QIII on 2019-03-27
Hello!

What software is that?

---

### Post by twayta on 2019-03-27
NS3 ( Network Simulator) it support but with many problems

---

### Post by Impavidus on 2019-03-27
The options you currently have are 16.04, 18.04 or 18.10, and for most cases I recommend 18.04. I don't know about ns3 though, but I see it's in the repositories. If there are problems with the version in the repositories, maybe someone else can help.

BTW, if you already use a root shell, there's no need for sudo. And it's easier to copy-paste text from the terminal to the forum than to use a screenshot.

---

### Post by twayta on 2019-03-27
for ubuntu 16.04 and 18.04 the wifi don't work on my pc i dont know what is the problem so i installed the 17.04 version to solve the problem of wifi.

---

### Post by twayta on 2019-03-27
this is a part of my screen when i make apt-get update :

```

Ign:92 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) zesty-backports/main all DEP-11 Metadata
Ign:93 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) zesty-backports/main DEP-11 64x64 Icons
Ign:94 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) zesty-backports/restricted all Packages
Ign:95 [http://tn.archive.ubuntu.com/ubuntu](http://tn.archive.ubuntu.com/ubuntu) zesty-backports/restricted amd64 Packages
Lecture des listes de paquets... Fait
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://tn.archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://tn.archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://tn.archive.ubuntu.com/ubuntu zesty-backports Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

and when i try to install a package :

```

hp@hp-HP-Notebook:~$ sudo apt-get install mercurial
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet mercurial
hp@hp-HP-Notebook:~$
```

---

### Post by QIII on 2019-03-27
Let me repeat jeremy31's statement:

> That is because the servers for 17.04 were shut down when it went EOL last January. Ubuntu 17.04 only had 9 months of support 

You are getting those errors because the configuration Zesty is using is looking for URLs that are no longer used.  17.04 is no longer supported.  It no longer receives updates.  It no longer receives even security updates.  The software in the repos is no longer updated.  It is now insecure and unsafe to be used to connect to the web.

Although it is possible to set up your configuration to find the original files, it would be irresponsible for us to help you do that.  However, if you insist, you may look [here]("https://help.ubuntu.com/community/EOLUpgrades") for an answer.

It is irrational for you to attempt to solve two minor issues by inviting the disaster that could result from installing an EOL release.  It would be far more rational to install a supported version and then ask for help getting two things to work properly.

---

### Post by jeremy31 on 2019-03-27
> **twayta said:**
> for ubuntu 16.04 and 18.04 the wifi don't work on my pc i dont know what is the problem so i installed the 17.04 version to solve the problem of wifi.

Please start a thread in Networking and Wireless, see the wireless script link in my signature and post results on that thread and be sure to post that the wifi doesn't work on 16.04 or 18.04, somebody might know what the solution is

---

### Post by twayta on 2019-03-27
so i will retry 18.04 thank you for all

---

