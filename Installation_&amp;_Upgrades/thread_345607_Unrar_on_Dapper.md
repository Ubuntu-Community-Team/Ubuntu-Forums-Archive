---
title: "Unrar on Dapper"
date: 2007-01-24
forum: Installation &amp; Upgrades
---

### Post by HwH on 2007-01-24
Im trying to install unrar whatever i try whether i use the terminal or synaptic paclage manager i always come up with this problem:
> :~$ sudo apt-get install rar
Password:
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  unrar
The following NEW packages will be installed
  rar
0 upgraded, 1 newly installed, 0 to remove and 230 not upgraded.
Need to get 242kB of archives.
After unpacking 487kB of additional disk space will be used.
Errhttp://archive.ubuntu.com dapper/multiverse rar 3.30-2ubuntu2
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.30-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.30-2ubuntu2_i386.deb)  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)


any help would be good
thanks

---

### Post by fearevilleet on 2007-01-24
Why is the package manager trying to connect to local host? Dose your internet connection work? If your internet connection is not working I believe the package manage will not function.

---

### Post by youthforlinux on 2007-01-24
Does your internet work

try

```
sudo apt-get update
```

and see if it works and if it checks the repos

open firefox and see if you can get online

also 

try automatix at
[www.getautomatix.com]("www.getautomatix.com")

---

### Post by HwH on 2007-01-24
> **fearevilleet said:**
> Why is the package manager trying to connect to local host? Dose your internet connection work? If your internet connection is not working I believe the package manage will not function.
> **youthforlinux said:**
> Does your internet work
my internet is working or how else would i be here?


> **youthforlinux said:**
> ```
sudo apt-get update
```

and see if it works and if it checks the repos
tried here is the result
```
:~$ sudo apt-get update
Password:
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://gb.archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Errhttp://archive.ubuntu.com dapper-backports Release.gpg
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://gb.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.
henry@Henry:~$ sudo apt-get install rar
Reading package lists... Done
Building dependency tree... Done
Suggested packages:
  unrar
The following NEW packages will be installed
  rar
0 upgraded, 1 newly installed, 0 to remove and 230 not upgraded.
Need to get 242kB of archives.
After unpacking 487kB of additional disk space will be used.
Errhttp://archive.ubuntu.com dapper/multiverse rar 3.30-2ubuntu2
  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/multiverse/r/rar/rar_3.30-2ubuntu2_i386.deb  Could not connect to 127.0.0.1:8080 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

