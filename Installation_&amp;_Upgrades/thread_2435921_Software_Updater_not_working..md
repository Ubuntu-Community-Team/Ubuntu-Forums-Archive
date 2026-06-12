---
title: "Software Updater not working."
date: 2020-01-28
forum: Installation &amp; Upgrades
---

### Post by mawil10132 on 2020-01-28
Software Updater > Software updates are no longer provided for Ubuntu 19.04, To stay secure you should upgrade to Ubuntu 19.10

Then I click on 'Upgrade' button, but the message window disappears and nothing happens.

---

### Post by Frogs Hair on 2020-01-28
Try the following from the terminal.

```
sudo apt update && sudo apt dist-upgrade
```

---

### Post by mawil10132 on 2020-01-30
> **Frogs Hair said:**
> Try the following from the terminal.

```
sudo apt update && sudo apt dist-upgrade
```

Didn't work  :(     no biggy

---

### Post by CatKiller on 2020-01-30
```
sudo do-release-upgrade
``` is the way to upgrade from one release to the next from the command line. That might show any issues with the process that the GUI tool might not. As the initial message said, there won't be any more normal updates for 19.04.

---

### Post by Frogs Hair on 2020-01-30
> **mawil10132 said:**
> Didn't work  :(     no biggy

That command maybe a bit dated try as posted above.

---

### Post by Impavidus on 2020-01-31
19.04 reached end of life only a week ago, so the repositories may still be available. But maybe not. First try to install all available upgrades for 19.04. No new upgrades have been made available in the past week, but maybe you were behind. It should work with the slightly outdated command above, but we like to see the full output. In particular if there are errors. We always like to see error messages; they are helpful. Then try to upgrade to 19.10 with the command CatKiller showed. Make sure you've got backups of all important files, because, if the release upgrade fails, you want a fresh install. And if this is your only computer, prepare a 19.10 live disk. Just in case.

I'm pleasantly surprised that these days there's actually a warning when your release reaches end of life.

---

### Post by mawil10132 on 2020-02-23
> **Impavidus said:**
> 19.04 reached end of life only a week ago, so the repositories may still be available. But maybe not. First try to install all available upgrades for 19.04. No new upgrades have been made available in the past week, but maybe you were behind. It should work with the slightly outdated command above, but we like to see the full output. In particular if there are errors. We always like to see error messages; they are helpful. Then try to upgrade to 19.10 with the command CatKiller showed. Make sure you've got backups of all important files, because, if the release upgrade fails, you want a fresh install. And if this is your only computer, prepare a 19.10 live disk. Just in case.

I'm pleasantly surprised that these days there's actually a warning when your release reaches end of life.

Here is results of second attempt, did it before and tried update and results were the same.
```
michael@michael-Inspiron-5575:~$ sudo apt update && sudo apt dist-upgrade
[sudo] password for michael: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-updates InRelease              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) disco-security InRelease               
Hit:5 [https://updates.signal.org/desktop/apt](https://updates.signal.org/desktop/apt) xenial InRelease                  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  libmysqlclient20 mysql-common
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  libsnmp30
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
michael@michael-Inspiron-5575:~$
```

---

### Post by Impavidus on 2020-02-23
19.04 has now been unsupported for a month, so the idea of a release upgrade as opposed to a fresh install is getting less appealing, but you can still try.  You've got one official bionic (18.04) repository mixed up with your disco (19.04) repositories. Fix that. You've also got an unofficial source in /etc/apt/sources.list.d/signal-xenial.list. That appears to be made for xenial (Ubuntu 16.04) and produces a lot of warning, although no errors, so it appears that that file is somehow messed up. Best to remove all non-official sources before attempting to release upgrade, along with all software that came from those unofficial sources. Finally, the package libsnmp30, which is in the official repositories of Ubuntu 19.04 (at version 5.7.3+dfsg-5ubuntu1.2), is for some reason not upgraded. Find out why:```
apt-cache policy libsnmp30
sudo apt upgrade libsnmp30
```

---

### Post by mawil10132 on 2020-02-23
> **Impavidus said:**
> 19.04 has now been unsupported for a month, so the idea of a release upgrade as opposed to a fresh install is getting less appealing, but you can still try.  You've got one official bionic (18.04) repository mixed up with your disco (19.04) repositories. Fix that. You've also got an unofficial source in /etc/apt/sources.list.d/signal-xenial.list. That appears to be made for xenial (Ubuntu 16.04) and produces a lot of warning, although no errors, so it appears that that file is somehow messed up. Best to remove all non-official sources before attempting to release upgrade, along with all software that came from those unofficial sources. Finally, the package libsnmp30, which is in the official repositories of Ubuntu 19.04 (at version 5.7.3+dfsg-5ubuntu1.2), is for some reason not upgraded. Find out why:```
apt-cache policy libsnmp30
sudo apt upgrade libsnmp30
```


Entered the two commands ;
```
apt-cache policy libsnmp30
sudo apt upgrade libsnmp30and got this, 
michael@michael-Inspiron-5575:~$ apt-cache policy libsnmp30
libsnmp30:
  Installed: 5.7.3+dfsg-1.8ubuntu3.3
  Candidate: 5.7.3+dfsg-5ubuntu1.2
  Version table:
     5.7.3+dfsg-5ubuntu1.2 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco-updates/main amd64 Packages
     5.7.3+dfsg-5ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco/main amd64 Packages
 *** 5.7.3+dfsg-1.8ubuntu3.3 100
        100 /var/lib/dpkg/status
michael@michael-Inspiron-5575:~$ sudo apt upgrade libsnmp30
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libsnmp30 : Depends: libsensors5 (>= 1:3.5.0) but it is not going to be installed
E: Broken packages
michael@michael-Inspiron-5575:~$
```

---

### Post by Impavidus on 2020-02-24
You've got a weird version of libsnmp30 and it refuses to upgrade to the normal version because you don't have the right version of libsensors5. The right version is in the 19.04 repositories (which, fortunately, still appear to be available, but that could change at any time), but for some reason your system won't install it. Maybe this will shed some light on it:```
apt-cache policy libsensors5
```

Can you manage to fix your software sources? If you need help, post the contents of your /etc/apt/sources.list. And disable that source in /etc/apt/sources.list.d/signal-xenial.list.

---

### Post by mörgæs on 2020-02-24
Fixing the problem is a learning experience but it's not necessarily the fastest way to a working system. If the latter is more important then a clean install of 19.10 is worth considering - and clean installs every time in the future you want a new release.

---

### Post by mawil10132 on 2020-02-24
```
apt-cache policy libsensors5michael@michael-Inspiron-5575:~$ apt-cache policy libsensors5
libsensors5:
  Installed: (none)
  Candidate: 1:3.5.0-3ubuntu1
  Version table:
     1:3.5.0-3ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) disco/main amd64 Packages
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:2
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list.d/signal-xenial.list:1 and /etc/apt/sources.list.d/signal-xenial.list:3
michael@michael-Inspiron-5575:~$
```

It's beginning to feel like I'll have to do a clean/fresh install of 19.10, but I did that when I installed Ubuntu on this laptop, where all the other versions are there beats me.

---

### Post by Impavidus on 2020-02-24
apt knows that libsensors5 is available and not installed, yet doesn't want to install it. I don't know why, but it may be possible to figure that out. I do know that without clean software sources a release upgrade will end in failure. So, the contents of /etc/apt/sources.list. Unless you decide to wipe your system and fresh install, which is probably faster.

---

