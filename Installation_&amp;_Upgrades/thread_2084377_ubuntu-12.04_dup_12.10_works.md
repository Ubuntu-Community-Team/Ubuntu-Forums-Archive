---
title: "ubuntu-12.04 dup 12.10 works?"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by ramaswamyps on 2012-11-15
i have nstalled 12.04 and uptdate.
i tried to apt-get dist-upgrade
it installed kernel version 3.2.0-33

```
ramaswamy@ramaswamy-Satellite-C855D:~$ uname -a
Linux ramaswamy-Satellite-C855D 3.2.0-33-generic #52-Ubuntu SMP Thu Oct 18 16:29:15 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
ramaswamy@ramaswamy-Satellite-C855D:~$ 
```

```
ramaswamy@ramaswamy-Satellite-C855D:~$ cat /etc/os-release
NAME="Ubuntu"
VERSION="12.04.1 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"
VERSION_ID="12.04"
```

do i have to download new version iso and reinstall or that is ll the difference in 12.10 ?
kindly advice
i have been upgrading the system
in 2 3 days regularly

---

### Post by oldfred on 2012-11-15
The command sudo apt-get dist-upgrade just installs the newest kernel and some other house cleaning updates.
See
man apt-get

If you want to upgrade, but be sure to have good backups and best to have the next version liveCD and test that everything works first.

new install upgrade to next version
sudo do-release-upgrade

I now prefer to do clean installs to another / partition. Then I still have my old install to boot into if there are any major issues with new install. I use 25GB for / and have data in other partitions so I do not need large root partitions.

---

### Post by ramaswamyps on 2012-11-16
```
ramaswamy@ramaswamy-Satellite-C855D:~$ sudo do-release-upgrade
[sudo] password for ramaswamy: 
Checking for a new Ubuntu release
No new release found
ramaswamy@ramaswamy-Satellite-C855D:~$ 
```

now i get this message

---

### Post by oldfred on 2012-11-16
Since 12.04 is a long term release there are two upgrade paths. One to the next long term release and the other to the next 6 month release.

There is a setting somewhere but I only know how to change in Update Manager, not from command line. Look in Update Manager and Settings. Then look in updates and change the setting to for any version.

---

