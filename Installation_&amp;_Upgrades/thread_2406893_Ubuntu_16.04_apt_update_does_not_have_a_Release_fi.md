---
title: "Ubuntu 16.04 apt update does not have a Release file"
date: 2018-11-27
forum: Installation &amp; Upgrades
---

### Post by tunctuncbilek on 2018-11-27
I can't install anything to ubuntu server and can't update it. My sources.list and other commands output is below. How can i fix it ?

$ sudo nano /etc/apt/sources.list

```
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```

$ sudo apt update

```
Ign:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Ign:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Err:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security Release
  Connection failed [IP: 91.189.88.161 80]
Ign:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Err:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial Release
  Connection failed [IP: 91.189.88.162 80]
Err:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates Release 
  Connection failed [IP: 91.189.88.152 80]
Err:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports Release
  Connection failed [IP: 91.189.88.162 80]
Reading package lists... Done                           
E: The repository 'http://security.ubuntu.com/ubuntu xenial-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://gb.archive.ubuntu.com/ubuntu xenial-backports Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
```

$ wget [http://security.ubuntu.com/ubuntu/dists/xenial-security/Release](http://security.ubuntu.com/ubuntu/dists/xenial-security/Release)
```

--2018-11-27 19:00:09--  [http://security.ubuntu.com/ubuntu/dists/xenial-security/Release](http://security.ubuntu.com/ubuntu/dists/xenial-security/Release)
Resolving security.ubuntu.com (security.ubuntu.com)... 91.189.88.162, 91.189.88.152, 91.189.88.161, ...
Connecting to security.ubuntu.com (security.ubuntu.com)|91.189.88.162|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 105813 (103K)
Saving to: ‘Release.2’

Release.2                                  100%[=====================================================================================>] 103,33K   336KB/s    in 0,3s    

2018-11-27 19:00:11 (336 KB/s) - ‘Release.2’ saved [105813/105813]
```

$ wget 91.189.88.162

```
--2018-11-27 19:01:21--  [http://91.189.88.162/](http://91.189.88.162/)
Connecting to 91.189.88.162:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11321 (11K) [text/html]
Saving to: ‘index.html.1’

index.html.1                               100%[=====================================================================================>]  11,06K  --.-KB/s    in 0,02s   

2018-11-27 19:01:22 (528 KB/s) - ‘index.html.1’ saved [11321/11321]
```

$ lsb_release -a

```
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.4 LTS
Release:    16.04
Codename:   xenial
```

---

### Post by tunctuncbilek on 2018-11-28
Network admin added a new rule. They reverted it and problem solved

---

