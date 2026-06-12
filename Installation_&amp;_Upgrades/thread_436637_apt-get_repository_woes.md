---
title: "apt-get repository woes"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Josiah4jc on 2007-05-08
I'm having some trouble getting a nice list of packages to install. I want to get Opera, and some dvd playback files and WMA support. I have a amd64 machine. My question is how to get these repositories, or equivalent, working.

Here's what is happening, copied from konsole, with added comments:

josiah@Josiah-kubuntu:~$ sudo apt-get update

// looking good so far...

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/multiverse Packages
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages [1304kB]

//problems start to occur

99% [4 Packages gzip 0] [Waiting for headers]                       19.9kB/s 0s
gzip: stdin: invalid compressed data--format violated
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
  Sub-process gzip returned an error code (1)
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages [183kB]
99% [Working]                                                       19.9kB/s 0s
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 5B in 9s (1B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/binary-amd64/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.



here is my source.list file:

# Automatically generated sources.list
# [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

# Ubuntu supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

---

### Post by zvacet on 2007-05-08
I tryed your links and they work for me.Try in terminal

```
sudo aptitude update & sudo aptitude upgrade
```

and maybe you can add backports to your source list or use this one 
[http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu:Feisty#How_to_add_extra_repositories")

---

### Post by Josiah4jc on 2007-05-09
I think part of my problem is that I'm using kubuntu, installed from a x86-64 combo DVD. There seems to be poor support for 64 bit systems at this point in time, and even though ubuntu and kubuntu are supposed to be very similar, I'm begining to suspect that part of the issues I have with packages come from using an alternative distro.

I wish there was a way to force the kubuntu installation DVD to install in 32 bt mode. I've ordered a new ubuntu disc, 32 bit, and that should clear up some issues.

---

### Post by Najand on 2007-05-09
Your gzip error can be fixed using:
```

sudo apt-get clean && sudo apt-get autoclean

```

---

### Post by taurus on 2007-05-09
Or just edit /etc/apt/sources.list

```
kdesu kate /etc/apt/sources.list
```
and remove the **us.** from your repos.  Save it and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by johnmudd on 2007-05-11
Thanks, removing the "us." prefix worked for me.  I'm surprised how much searching I had to do to find this.  Thanks, again.

John

---

