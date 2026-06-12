---
title: "The update information is outdated. This may be caused by a network problem"
date: 2014-01-21
forum: Installation &amp; Upgrades
---

### Post by madhumithabiw on 2014-01-21
On execution of [B]sudo apt-get update, 
[/B]the output is as follows

```

Err [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg                               
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise Release.gpg                           
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-updates Release.gpg                   
  Unable to connect to 199.201.121.113:442:
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) precise-backports Release.gpg                 
  Unable to connect to 199.201.121.113:442:
Err [http://tinyos.stanford.edu](http://tinyos.stanford.edu) lucid Release.gpg                               
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) precise Release.gpg                           
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://tinyprod.net](http://tinyprod.net) squeeze Release.gpg                                    
  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)
Err [http://tinyprod.net](http://tinyprod.net) msp430-46 Release.gpg       
  Unable to connect to 199.201.121.113:442:
Ign mirror://mirrors.ubuntu.com precise-security Release.gpg
Ign mirror://mirrors.ubuntu.com precise-security Release
Ign mirror://mirrors.ubuntu.com precise-security/main TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/multiverse TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/restricted TranslationIndex
Ign mirror://mirrors.ubuntu.com precise-security/universe TranslationIndex
Err mirror://mirrors.ubuntu.com precise-security/main i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/restricted i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/universe i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Err mirror://mirrors.ubuntu.com precise-security/multiverse i386 Packages
  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en_IN
Ign mirror://mirrors.ubuntu.com precise-security/main Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en_IN
Ign mirror://mirrors.ubuntu.com precise-security/multiverse Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en_IN
Ign mirror://mirrors.ubuntu.com precise-security/restricted Translation-en
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en_IN
Ign mirror://mirrors.ubuntu.com precise-security/universe Translation-en
Reading package lists... Done
W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise-updates/Release.gpg)  Unable to connect to 199.201.121.113:442:


W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/precise-backports/Release.gpg)  Unable to connect to 199.201.121.113:442:


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/precise-security/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/precise/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/lucid/Release.gpg](http://tinyos.stanford.edu/tinyos/dists/ubuntu/dists/lucid/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://tinyprod.net/repos/debian/dists/squeeze/Release.gpg](http://tinyprod.net/repos/debian/dists/squeeze/Release.gpg)  Could not connect to 199.201.121.113:442 (199.201.121.113). - connect (111: Connection refused)


W: Failed to fetch [http://tinyprod.net/repos/debian/dists/msp430-46/Release.gpg](http://tinyprod.net/repos/debian/dists/msp430-46/Release.gpg)  Unable to connect to 199.201.121.113:442:


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/main/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/restricted/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/universe/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/precise-security/multiverse/binary-i386/Packages  No mirror file '/var/lib/apt/mirrors/mirrors.ubuntu.com_mirrors.txt' found  [Mirror: ]


W: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by ibjsb4 on 2014-01-21
Try changing your download source.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

Are you hooked direct to the internet (no proxy)?

---

### Post by madhumithabiw on 2014-01-22
I'm pinged to the internet whose ip is 192.168.77.127. But on executing the sudo apt-get update, its showing Could not connect to 199.201.121.113:442 (199.201.121.113) (This is proxy I tried to use), connection timed out. This is not supposed to be ip. Also, the problem has started arising, when actually I tried to use the proxy.

Please reply. Its urgent

---

### Post by fantab on 2014-01-22
How did you setup a proxy?

---

### Post by madhumithabiw on 2014-01-22
In Dashboard, System Setting->Network ->Network Proxy

In Proxy, the method is selected as manual. HTTP Proxy is set using corresponding IP along with a port id.

But it didn't work so I removed corresponding Ip and set it back to wired connection. Still after that there is updation problem.

---

### Post by fantab on 2014-01-22
Post the output of:

```
cat /etc/apt/sources.list
```

It is possible that your sources got changed when you enabled the proxy...

---

### Post by madhumithabiw on 2014-01-22
The output of cat /etc/apt/sources.list

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
# TinyOS Repository
deb [http://tinyos.stanford.edu/tinyos/dists/ubuntu](http://tinyos.stanford.edu/tinyos/dists/ubuntu) lucid main


# TinyOS MSP430 GCC Compiler Repository
deb [http://tinyprod.net/repos/debian](http://tinyprod.net/repos/debian) squeeze main
deb [http://tinyprod.net/repos/debian](http://tinyprod.net/repos/debian) msp430-46 main

---

### Post by raja.genupula on 2014-01-22
I think if you have a proxy , you must set  them for apt-get ,software centre too.

---

### Post by madhumithabiw on 2014-01-22
Now, I'm using either wired connection or wifi connection.

---

### Post by madhumithabiw on 2014-01-23
My problem is solved, as [COLOR=#000000]In Dashboard, System Setting->Network ->Network Proxy

After removing the proxy, I had'n't clicked in the Apply system wide.

Thanx for patience and reply.[/COLOR]

---

