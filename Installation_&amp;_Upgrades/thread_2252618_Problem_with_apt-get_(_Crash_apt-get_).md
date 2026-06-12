---
title: "Problem with apt-get ( Crash apt-get )"
date: 2014-11-13
forum: Installation &amp; Upgrades
---

### Post by alireza378 on 2014-11-13
hi all
I have a problem.

I tried to install Code::Blocks IDE from its site : [http://www.codeblocks.org/](http://www.codeblocks.org/)
I downloaded it. and tried to install it. It installed but it causes a problem for apt-get

The problem is this :
Everytime that i want install or remove a package from apt-get or software center, I get this error :

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 codeblocks-contrib : Depends: libwxsmithlib0 (= 13.12-1) but 13.12-3 is to be installed
                      Depends: codeblocks (= 13.12-1) but 13.12-3 is to be installed
                      Recommends: valgrind but it is not going to be installed
                      Recommends: cppcheck but it is not going to be installed
                      Recommends: cscope but it is not going to be installed
                      Recommends: cccc but it is not going to be installed
 codeblocks-dbg : Depends: codeblocks-contrib (= 13.12-3) but 13.12-1 is to be installed
 hhvm : Depends: libboost-filesystem1.54.0 but it is not going to be installed
        Depends: libboost-program-options1.54.0 but it is not going to be installed
        Depends: libboost-system1.54.0 but it is not going to be installed
        Depends: libboost-system1.54.0 but it is not going to be installed
        Depends: libc-client2007e but it is not going to be installed
        Depends: libmcrypt4 but it is not going to be installed
        Depends: libmemcached10 but it is not going to be installed
        Depends: libonig2 but it is not going to be installed
        Depends: libjemalloc1 (>= 3.0.0) but it is not going to be installed
        Depends: libgoogle-glog0 (>= 0.3.1) but it is not going to be installed
        Depends: libboost-thread1.54.0 but it is not going to be installed
        Depends: libmagickwand5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

And when i type "apt-get -f install" i get this error :

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  codeblocks-contrib
Recommended packages:
  valgrind
The following packages will be upgraded:
  codeblocks-contrib
1 upgraded, 0 newly installed, 0 to remove and 172 not upgraded.
3 not fully installed or removed.
Need to get 0 B/3,018 kB of archives.
After this operation, 1,162 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 165755 files and directories currently installed.)
Preparing to unpack .../codeblocks-contrib_13.12-3_amd64.deb ...
Unpacking codeblocks-contrib (13.12-3) over (13.12-1) ...
dpkg: error processing archive /var/cache/apt/archives/codeblocks-contrib_13.12-3_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/pkgconfig/cb_wximagepanel.pc', which is also in package codeblocks-wxcontrib-dev 13.12-1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/codeblocks-contrib_13.12-3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How do i can solve this problem ?

Best Regards

---

### Post by alireza378 on 2014-11-13
Update Topic

---

### Post by Impavidus on 2014-11-13
Why install codeblocks 13.12 directly from the dev's site instead of installing the same release from the Ubuntu repositories? Codeblocks 13.12 is available from the Trusty repositories.

You somehow got a package named **codeblocks-wxcontrib-dev** installed on your system and it conflicts with the upgraded version of **codeblocks-contrib** from the repositories. Try to remove **codeblocks-wxcontrib-dev**.

---

### Post by alireza378 on 2014-11-13
> **Impavidus said:**
> Why install codeblocks 13.12 directly from the dev's site instead of installing the same release from the Ubuntu repositories? Codeblocks 13.12 is available from the Trusty repositories.

You somehow got a package named **codeblocks-wxcontrib-dev** installed on your system and it conflicts with the upgraded version of **codeblocks-contrib** from the repositories. Try to remove **codeblocks-wxcontrib-dev**.

Indeed i use Xubuntu.

Can you say me how to remove **codeblocks-wxcontrib-dev **and how to install codeblocks from Trusty repositories** in Xubuntu **?

Ta very much ;)

---

### Post by slickymaster on 2014-11-13
> **Impavidus said:**
> Why install codeblocks 13.12 directly from the dev's site instead of installing the same release from the Ubuntu repositories? Codeblocks 13.12 is available from the Trusty repositories.

You somehow got a package named **codeblocks-wxcontrib-dev** installed on your system and it conflicts with the upgraded version of **codeblocks-contrib** from the repositories. Try to remove **codeblocks-wxcontrib-dev**.

This ^^^

**codeblocks-wxcontrib-dev** is an unofficial, third party package (provided by upstream). Third party packages is not supported, so you'll have to uninstall it and use packages in the official repositories only.

---

### Post by kc1di on 2014-11-13
> **alireza378 said:**
> Indeed i use Xubuntu.

Can you say me how to remove **codeblocks-wxcontrib-dev **and how to install codeblocks from Trusty repositories** in Xubuntu **?

Ta very much ;)

in a termial do the following:

```
sudo apt-get purge codeblocks-wxcontrib-dev
```
Then
```
sudo apt-get clean
```

```
sudo apt-get install codeblocks
```

---

### Post by slickymaster on 2014-11-13
> **Impavidus said:**
> Why install codeblocks 13.12 directly from the dev's site instead of installing the same release from the Ubuntu repositories? Codeblocks 13.12 is available from the Trusty repositories.

You somehow got a package named **codeblocks-wxcontrib-dev** installed on your system and it conflicts with the upgraded version of **codeblocks-contrib** from the repositories. Try to remove **codeblocks-wxcontrib-dev**.

This ^^^

**codeblocks-wxcontrib-dev** is an unofficial, third party package (provided by upstream). You'll have to uninstall it and use packages in the official repositories only.

---

### Post by alireza378 on 2014-11-13
> **kc1di said:**
> in a termial do the following:

```
sudo apt-get purge codeblocks-wxcontrib-dev
```
Then
```
sudo apt-get clean
```

```
sudo apt-get install codeblocks
```


but then again :(

Output of 
```
sudo apt-get purge codeblocks-wxcontrib-dev
```

Is :

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 codeblocks-contrib : Depends: libwxsmithlib0 (= 13.12-1) but 13.12-3 is to be installed
                      Depends: codeblocks (= 13.12-1) but 13.12-3 is to be installed
                      Recommends: valgrind but it is not going to be installed
                      Recommends: cppcheck but it is not going to be installed
                      Recommends: cscope but it is not going to be installed
                      Recommends: cccc but it is not going to be installed
 codeblocks-dbg : Depends: codeblocks-contrib (= 13.12-3) but 13.12-1 is to be installed
 codeblocks-wxcontrib-headers : Depends: codeblocks-wxcontrib-dev (>= 13.12-1) but it is not going to be installed
                                Depends: codeblocks-wxcontrib-dev (< 13.12-1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by kc1di on 2014-11-13
try running these commands first:
```
sudo dpkg --configure -a 
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update

```

Then try to purge again.

---

