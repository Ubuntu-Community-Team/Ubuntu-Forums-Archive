---
title: "sudo apt-get update errors"
date: 2018-01-21
forum: Installation &amp; Upgrades
---

### Post by pkoukoulis-r on 2018-01-21
I'm attempting an sudo update on a laptop I haven't worked on for almost 8 months, but I get the following command line errors:

```
$ sudo apt-get update 
Hit:1 http://download.virtualbox.org/virtualbox/debian zesty InRelease
Ign:2 http://gb.archive.ubuntu.com/ubuntu zesty InRelease
Ign:3 http://security.ubuntu.com/ubuntu zesty-security InRelease
Ign:4 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease        
Err:5 http://security.ubuntu.com/ubuntu zesty-security Release           
  404  Not Found [IP: 91.189.88.161 80]
Ign:6 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease
Err:7 http://gb.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 91.189.88.152 80]
Err:8 http://gb.archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 91.189.88.152 80]
Err:9 http://gb.archive.ubuntu.com/ubuntu zesty-backports Release
  404  Not Found [IP: 91.189.88.152 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty



```

I selected software sources and deselected an "other" option. The cache was then updated, but then the following error message appeared:

> *E:The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://gb.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file., W:Updating from such a repository can't be done securely, and is therefore disabled by default., W:See apt-secure(8) manpage for repository creation and user configuration details., E:The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.*

Can somebody suggest how to get around the errors?
I'd like to do an upgrade, but only after I've applied all the updates.

Thanks

---

### Post by howefield on 2018-01-21
Zesty has reached end of life and the repositories have moved. I'd suggest a clean install of 17.10 in light of how much has changed since 17.04 with regards the desktop environment.

---

### Post by lionel4anlominus on 2018-01-21
> **pkoukoulis-r said:**
> I'm attempting an sudo update on a laptop I haven't worked on for almost 8 months, but I get the following command line errors:

```
$ sudo apt-get update 
Hit:1 http://download.virtualbox.org/virtualbox/debian zesty InRelease
Ign:2 http://gb.archive.ubuntu.com/ubuntu zesty InRelease
Ign:3 http://security.ubuntu.com/ubuntu zesty-security InRelease
Ign:4 http://gb.archive.ubuntu.com/ubuntu zesty-updates InRelease        
Err:5 http://security.ubuntu.com/ubuntu zesty-security Release           
  404  Not Found [IP: 91.189.88.161 80]
Ign:6 http://gb.archive.ubuntu.com/ubuntu zesty-backports InRelease
Err:7 http://gb.archive.ubuntu.com/ubuntu zesty Release
  404  Not Found [IP: 91.189.88.152 80]
Err:8 http://gb.archive.ubuntu.com/ubuntu zesty-updates Release
  404  Not Found [IP: 91.189.88.152 80]
Err:9 http://gb.archive.ubuntu.com/ubuntu zesty-backports Release
  404  Not Found [IP: 91.189.88.152 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-updates Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu zesty-backports Release' does no longer have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 17.04
Release:    17.04
Codename:    zesty



```

I selected software sources and deselected an "other" option. The cache was then updated, but then the following error message appeared:



Can somebody suggest how to get around the errors?
I'd like to do an upgrade, but only after I've applied all the updates.

Thanks

i see in the end this problem 
```
$ lsb_release -a
``````
No LSB modules are available.
```
so TRY THIS

Since there are no lsb modules installed in your machine, you get that message.
You can install the lsb modules using the command
sudo apt-get install lsb-core
After installation, when you run the same command you wont see the message saying 'No LSB modules are available'
lsb_release -a will display some basic info about to which LSB specifications your system/OS complies with.
Hope this helps.

Was taken from [Link]("https://askubuntu.com/questions/230766/how-lsb-module-affects-system-and-can-be-made-available-to-the-system")

---

### Post by deadflowr on 2018-01-21
> **lionel4anlominus said:**
> i see in the end this problem 
```
$ lsb_release -a
``````
No LSB modules are available.
```
so TRY THIS

Since there are no lsb modules installed in your machine, you get that message.
You can install the lsb modules using the command
sudo apt-get install lsb-core
After installation, when you run the same command you wont see the message saying 'No LSB modules are available'
lsb_release -a will display some basic info about to which LSB specifications your system/OS complies with.
Hope this helps.

Was taken from [Link]("https://askubuntu.com/questions/230766/how-lsb-module-affects-system-and-can-be-made-available-to-the-system")

That's not the problem.
And to top it off, the OP cannot install lsb-core since the system is out of date.
Hence the suggestion to do a reinstall of a supported system such as 17.10 (or even going backwards to 16.04 or really backwards to 14.04)

Same issues and suggestions posted here apply: [https://ubuntuforums.org/showthread.php?t=2383048]("https://ubuntuforums.org/showthread.php?t=2383048")

---

### Post by pkoukoulis-r on 2018-01-23
Thanks.

I've added the following:
[FONT=courier new]deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse[/FONT]

to the /etc/apt/sources.list as per the advice from [end of line upgrades]("https://help.ubuntu.com/community/EOLUpgrades")

and the upgrade worked.

---

### Post by deadflowr on 2018-01-23
> **pkoukoulis-r said:**
> Thanks.

I've added the following:
[FONT=courier new]deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse[/FONT]

to the /etc/apt/sources.list as per the advice from [end of line upgrades]("https://help.ubuntu.com/community/EOLUpgrades")

and the upgrade worked.

Congratulations (or condolences) 
If you feel the issue has been solved please go ahead and mark this thread as solved:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

