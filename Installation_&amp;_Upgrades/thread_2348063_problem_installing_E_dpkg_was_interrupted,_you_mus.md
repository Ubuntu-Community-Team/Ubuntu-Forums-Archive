---
title: "problem installing E: dpkg was interrupted, you must manually run 'sudo dpkg --config"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by nick2learn on 2016-12-31
Hi,

Been browsing the forum (search facility says I'm forbidden?) wondered if anyone can help please?

Just trying to install pinto as per these directions:
[https://duckduckgo.com/?q=how+to+install+pinta+ubuntu&t=canonical&ia=qa&iax=1](https://duckduckgo.com/?q=how+to+install+pinta+ubuntu&t=canonical&ia=qa&iax=1)
but having this error message:
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

FYI - I have a SSD and a separate drive for data

------------------- Full Terminal text here -----------

```
nick@MSI:~$ sudo add-apt-repository ppa:pinta-maintainers/pinta-stable
[sudo] password for nick: 
 
 More info: [https://launchpad.net/~pinta-maintainers/+archive/ubuntu/pinta-stable](https://launchpad.net/~pinta-maintainers/+archive/ubuntu/pinta-stable)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmpnlw0do9x/secring.gpg' created
gpg: keyring `/tmp/tmpnlw0do9x/pubring.gpg' created
gpg: requesting key A5A1D6B2 from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpnlw0do9x/trustdb.gpg: trustdb created
gpg: key A5A1D6B2: public key "Launchpad PPA for Pinta Maintainers" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
nick@MSI:~$ sudo apt-get update
Hit:1 [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial InRelease
Hit:2 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial InRelease           
Hit:3 [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial InRelease 
Ign:5 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial InRelease
Ign:6 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial Release
Ign:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]    
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Get:4 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb InRelease [8,139 B]          
Ign:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Get:15 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb/apps amd64 Packages [65.6 kB]
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Get:17 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [68.1 kB]
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Hit:18 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                    
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Get:19 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]   
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:16 [http://screenshots.getdeb.net](http://screenshots.getdeb.net) xenial-getdeb/apps i386 Packages [66.3 kB]
Ign:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [25.6 kB]
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Get:24 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Get:25 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [443 kB]
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Get:26 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [436 kB]
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Err:7 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 Packages
  404  Not Found
Ign:8 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main i386 Packages
Get:27 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [302 kB]
Ign:9 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main all Packages
Ign:11 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en_GB
Get:28 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [188 kB]
Get:29 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Ign:12 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main Translation-en
Get:30 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Ign:13 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main amd64 DEP-11 Metadata
Get:31 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [2,520 B]
Get:32 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 Packages [4,404 B]
Get:33 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main i386 Packages [4,404 B]
Get:34 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main Translation-en [3,124 B]
Get:35 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:36 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:37 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/multiverse amd64 DEP-11 Metadata [212 B]
Ign:14 [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial/main DEP-11 64x64 Icons
Fetched 2,254 kB in 6s (325 kB/s)                                              
AppStream cache update completed, but some metadata was ignored due to errors.
W: The repository 'http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-amd64/Packages](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu/dists/xenial/main/binary-amd64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
nick@MSI:~$ ^C
nick@MSI:~$ sudo apt-get install pinta
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```

---

### Post by howefield on 2016-12-31
So, have you run the command as suggested ?

By the way, there is no xenial repository for the pinta-maintainers ppa that you have added. You'll have to remove it.

---

### Post by nick2learn on 2016-12-31
Hi,
yes I ran them in order as far as I know.
Thanks - How do I remove it?

---

### Post by howefield on 2016-12-31
> **nick2learn said:**
> yes I ran them in order as far as I know.

You haven't posted the output to... 

```
sudo dpkg --configure -a
```
 
> Thanks - How do I remove it?

You could remove the files from /etc/apt/sources.list.d/ that relate to the PPA in question or install ppa-manager and use that. If you need help in identifying the relevant files, post the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by nick2learn on 2016-12-31
I think I need to go to basic terminal school for noobies, can you recommend a resource please? :)

> **howefield said:**
> You haven't posted the output to... 

```
sudo dpkg --configure -a
```

I thought I post all the text from terminal, is this not what you mean?


> **howefield said:**
> You could remove the files from /etc/apt/sources.list.d/ that relate to the PPA in question or install ppa-manager and use that. If you need help in identifying the relevant files, post the output of..

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

```
nick@MSI:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list.d/getdeb.list:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
/etc/apt/sources.list.d/getdeb.list.save:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
/etc/apt/sources.list.d/jtaylor-ubuntu-keepass-xenial.list:deb [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial main
/etc/apt/sources.list.d/jtaylor-ubuntu-keepass-xenial.list.save:deb [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:deb [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list.save:deb [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/pinta-maintainers-ubuntu-pinta-stable-xenial.list:deb [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial main
nick@MSI:~$
```

---

### Post by howefield on 2017-01-01
> **nick2learn said:**
> I think I need to go to basic terminal school for noobies, can you recommend a resource please? :)

There is a [thread here]("https://ubuntuforums.org/showthread.php?t=2015424&highlight=linux+command+line+resources") which has a ton of resources that you could browse for one that suits your preferred learning style.

> I thought I post all the text from terminal, is this not what you mean?

```
nick@MSI:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates universe
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
/etc/apt/sources.list:deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
/etc/apt/sources.list.d/getdeb.list:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
/etc/apt/sources.list.d/getdeb.list.save:deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) xenial-getdeb apps
/etc/apt/sources.list.d/jtaylor-ubuntu-keepass-xenial.list:deb [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial main
/etc/apt/sources.list.d/jtaylor-ubuntu-keepass-xenial.list.save:deb [http://ppa.launchpad.net/jtaylor/keepass/ubuntu](http://ppa.launchpad.net/jtaylor/keepass/ubuntu) xenial main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list:deb [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial main
/etc/apt/sources.list.d/noobslab-ubuntu-apps-xenial.list.save:deb [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/openshot_developers-ubuntu-ppa-xenial.list.save:deb [http://ppa.launchpad.net/openshot.developers/ppa/ubuntu](http://ppa.launchpad.net/openshot.developers/ppa/ubuntu) xenial main
/etc/apt/sources.list.d/pinta-maintainers-ubuntu-pinta-stable-xenial.list:deb [http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu](http://ppa.launchpad.net/pinta-maintainers/pinta-stable/ubuntu) xenial main
nick@MSI:~$
```

Use the following to move the problem pinta repository files to your Documents folder, in case you want to use it later on.

```
sudo mv /etc/apt/sources.list.d/pinta-maintainers-ubuntu-pinta-stable-xenial* ~/Documents
```

Then update your sources and run the suggested command from your original error..
```
sudo apt update
```
```
sudo dpkg --configure -a
```

---

