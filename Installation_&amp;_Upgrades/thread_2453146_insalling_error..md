---
title: "insalling error."
date: 2020-11-04
forum: Installation &amp; Upgrades
---

### Post by josephchrzempiec on 2020-11-04
Hello I'm trying to install node also do updates and upgrades and other things. When i do these things i get this error i have never saw before.


E: Malformed entry 60 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.
E: Malformed entry 60 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.


I'm not a programmer or a linux guy But I'm starting to fall in love with linux and yes the ubuntu version lol. I really need help everything i found online pretty much didn't work. I'm not usre if this is a common thing or not. But i do see a lot of people with this proble. However i can not reinstall the OS because I'm 700 miles away. Can someone please help me?


Joseph

---

### Post by CelticWarrior on 2020-11-04
It's a human error and it happens, sometimes.

It means there's an error on line 60 that likely occurred due to a typo in adding a software source.

```
sudoedit [COLOR=#000000]/etc/apt/sources.list[/COLOR]
```
will show the entire file. Scroll down and pay attention to the white lines (starting with "deb"). If you don't see what's wrong then copy it in its entirety and paste here inside code tags so we can have a look.

---

### Post by josephchrzempiec on 2020-11-04
Hello i think i see the problem on line 60 it has deb-src [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) focal main But it looks like the space after the ubuntu is the problem. Thank you i been banging my head on my desk litterly for a few days trying to figure this out. Well i added line 60 to there. Because it looks like it was missing so i searched online and found that was missing. I added that But didn't think when i was typing all that i added a space in there. Thank you


Joseph

---

### Post by josephchrzempiec on 2020-11-04
Okay new error now. E: Unable to locate package node when i try to install node also when i try to apt update and upgrade i get some different errors now.

---

### Post by CelticWarrior on 2020-11-04
Please post those errors

---

### Post by josephchrzempiec on 2020-11-04
When i try to do a apt update i get this error.

> Reading package lists... DoneW: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
E: The repository 'http://download.rethinkdb.com/apt focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:58 and /etc/apt/sources.list:60
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:66 and /etc/apt/sources.list.d/rethinkdb.list:1





Edit: Some how i think my list got screwed up and i think i screwed it up even more. is there a list i can find online for all the default stuff?

---

### Post by ActionParsnip on 2020-11-04
What is the output of:
```

cat -n /etc/apt/sources.list

```
Thanks

---

