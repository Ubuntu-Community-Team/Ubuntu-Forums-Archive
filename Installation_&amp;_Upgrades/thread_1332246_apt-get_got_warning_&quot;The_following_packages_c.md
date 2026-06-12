---
title: "apt-get got warning &quot;The following packages cannot be authenticated!&quot;"
date: 2009-11-20
forum: Installation &amp; Upgrades
---

### Post by dodamn on 2009-11-20
Today, I made my own PPA. [https://launchpad.net/~dodamn/+archive/test]("https://launchpad.net/%7Edodamn/+archive/test")
And I uploaded my own source package to the PPA. Finally binary package was built successfully. The package name is 'rt3070-dkms'.


 I wanted to install my own package from my own PPA.
So first I registered signing key using following command.
 ```
$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys F6FE71D0
``` (F6FE71D0 is my signing key for my PPA)
 

And then I added the following two lines to /etc/apt/sources.list.
 ```
deb [http://ppa.launchpad.net/dodamn/test/ubuntu](http://ppa.launchpad.net/dodamn/test/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/dodamn/test/ubuntu](http://ppa.launchpad.net/dodamn/test/ubuntu) jaunty main
```
And I run update command.
 ```
$ sudo apt-get update
``` The result of this command had no errors.
 

And I run install command.
 ```
$ sudo apt-get install rt3070-dkms
``` But the result of this command has warning 'The following packages cannot be authenticated!'.



Why does this warning occur??
 

The following are full message when I run 'sudo apt-get install rt3070-dkms' command.
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  rt3070-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 693kB of archives.
After this operation, 3645kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  rt3070-dkms
Install these packages without verification [y/N]?

```

My Ubuntu is 9.04 (Jaunty). 
Please help me.

---

### Post by Bunnybugs on 2009-11-20
It doesn't recognize your signing key... like you've noticed.... what happens if you answer the final question with:

```
y
```

?

---

### Post by wilee-nilee on 2009-11-20
I might have missed it but did you put the key in software sources. It is strange though the update should have shown the same warning.

---

