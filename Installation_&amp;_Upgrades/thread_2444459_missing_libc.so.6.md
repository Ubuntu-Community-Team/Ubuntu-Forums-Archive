---
title: "missing libc.so.6"
date: 2020-05-30
forum: Installation &amp; Upgrades
---

### Post by kellys4279 on 2020-05-30
I've downloaded Steam already but it gives me an error when I try to run  it: "You are missing the following 32-bit libraries, and Steam may not  run: libc.so.6". So I tried to download it and typed ```
sudo apt-get install libc-i386
``` but it just gave me  ```
Reading package lists... Done 
Building dependency tree 
Reading state information... Done
E: Unable to locate package libc-i386
``` I have tried ```
sudo apt-get update
``` then running ```
sudo apt-get install libc-i386
```  but it just gave me the same error code again. Any help? Also, I've  only had Linux running for a few hours so I don't know much about it :/ 

Edit: Then I ran ```
sudo dpkg --add-architecture i386
``` but it gave me ```
Hit:1 http://repo.steampowered.com/steam precise InRelease
Hit:2 http://ports.ubuntu.com/ubuntu-ports xenial InRelease                   
Get:3 http://ports.ubuntu.com/ubuntu-ports xenial-updates InRelease [109 kB]
Get:4 http://ports.ubuntu.com/ubuntu-ports xenial-security InRelease [109 kB]
Ign:5 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Ign:6 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:8 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Ign:5 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Ign:6 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:8 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Ign:5 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
Ign:6 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:11 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Ign:8 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Err:5 http://ports.ubuntu.com/ubuntu-ports xenial/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:6 http://ports.ubuntu.com/ubuntu-ports xenial/restricted i386 Packages
Ign:7 http://ports.ubuntu.com/ubuntu-ports xenial/universe i386 Packages
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:11 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Ign:8 http://ports.ubuntu.com/ubuntu-ports xenial/multiverse i386 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:15 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:16 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Ign:9 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:11 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:15 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:16 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Err:9 http://ports.ubuntu.com/ubuntu-ports xenial-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:10 http://ports.ubuntu.com/ubuntu-ports xenial-updates/restricted i386 Packages
Ign:11 http://ports.ubuntu.com/ubuntu-ports xenial-updates/universe i386 Packages
Ign:12 http://ports.ubuntu.com/ubuntu-ports xenial-updates/multiverse i386 Packages
Ign:13 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:15 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:16 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Err:13 http://ports.ubuntu.com/ubuntu-ports xenial-security/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:14 http://ports.ubuntu.com/ubuntu-ports xenial-security/restricted i386 Packages
Ign:15 http://ports.ubuntu.com/ubuntu-ports xenial-security/universe i386 Packages
Ign:16 http://ports.ubuntu.com/ubuntu-ports xenial-security/multiverse i386 Packages
Fetched 218 kB in 3s (70.7 kB/s)
Reading package lists... Done
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch http://ports.ubuntu.com/ubuntu-ports/dists/xenial-security/main/binary-i386/Packages  404  Not Found [IP: 91.189.88.150 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by Dennis N on 2020-05-30
Try installing **libc6:i386**
You don't need to add the 32-bit architecture anymore. It's supported by default. 
Verify on 64-bit machine with:
```
dmn@Tyana-vm:~$ dpkg --print-foreign-architectures
i386

```

---

### Post by lazyteddy on 2020-05-31
Did you download the deb file from the steam website? You can install it from the software center, too. You need to enable the "multiverse" repository from "Software and Updates", then you can install a package called "steam-installer". This will take care of all the dependencies, plus you will be able to update it with the rest of the system.

---

### Post by deadflowr on 2020-05-31
You need to fix your archives.

See this as an example of how it should be:
[https://gist.github.com/josephlr/5034c933bbcfddc25a9275037821b048]("https://gist.github.com/josephlr/5034c933bbcfddc25a9275037821b048")

Edit: For prosperity (since github threads can be edited and the output may change) I'm posting it here with release codename changed for you:
```
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ xenial main restricted universe multiverse
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted universe multiverse
deb [arch=amd64,i386] http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
deb [arch=amd64,i386] http://security.ubuntu.com/ubuntu xenial-security main restricted universe multiverse

deb [arch=arm64,armhf,ppc64el,s390x] http://ports.ubuntu.com/ubuntu-ports/ xenial main restricted universe multiverse
deb [arch=arm64,armhf,ppc64el,s390x] http://ports.ubuntu.com/ubuntu-ports/ xenial-updates main restricted universe multiverse
deb [arch=arm64,armhf,ppc64el,s390x] http://ports.ubuntu.com/ubuntu-ports/ xenial-backports main restricted universe multiverse
deb [arch=arm64,armhf,ppc64el,s390x] http://ports.ubuntu.com/ubuntu-ports/ xenial-security main restricted universe multiverse
```
To also add, to give an understanding of what it does is basically the arch= flag tells apt to only look for the listed architecture types,
and to ignore any others in that particular archive or whatever the archtiecture types your system has been configured for.
So it won't fail because it wants some architecture that is non-existent in some archive or another.
If that makes sense.

As far as I know the ports repository main archives do not contain any amd64 or i386 packages.

---

