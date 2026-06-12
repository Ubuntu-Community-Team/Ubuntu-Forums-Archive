---
title: "Can't fix GPG error"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by torswin on 2007-09-25
torswin@xxHERKULEZxx:~$ sudo apt-get update
Password:
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Get:2 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Get:3 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/restricted Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/universe Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty/multiverse Sources
Get:4 [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates Release [32.4kB]
Ign [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates Release
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates/restricted Sources
Fetched 32.6kB in 0s (84.7kB/s)
Reading package lists... Done
W: GPG error: [http://no.archive.ubuntu.com](http://no.archive.ubuntu.com) feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

I get that error when i use sudo apt-get update. I don't know what's wrong, and I tried to look through /etc/apt/source.list but I don't know what to look for.
Could anyone tell me what to do? I'm using Ubuntu Feisty Fawn.

And the name of the computer is supposed to be lame :-\"

---

### Post by Seisen on 2007-09-25
Post your source list.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by wilkinsd on 2007-09-25
Hi,

I am having the same problem with the GPG error and the BADSIG. I had the problem all day yesterday and it continues today. I looked all through forums etc and some people say "just to wait" and so I did but the problem is still there.  I have tried changing my "sources.list" from using "us.archive" to just "archive" but this did not help so Iput it back. I recreated my "sources.list" file from [http://www-ubuntu-nl.com/source-o-matic/](http://www-ubuntu-nl.com/source-o-matic/) which is the one I am now using (see below) but this did not help. I have also tried running the "gpg" commands mentioned in the automatially genereated "sources.list" file related to GPG errors but i always get a timeout error from the "subkeys.pgp.net" key server (see below).  I had no problems at the end of last week, they just appear to have started yesterday (Monday Sep 24t).  If anyone has any ideas I would be grateful as I need to complete building a new server.

**_SOURCES.LIST FILE_**

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

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) feisty-updates universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe multiverse

# Canonical Commercial packages
# GPG key: 437D05B5
deb [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main 

deb-src [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial main

**_KEY SERVER TIMEOUT ERROR_**

**gpg --keyserver hkp://subkeys.pgp.net --recv-keys 437D05B5**
gpg: requesting key 437D05B5 from hkp server subkeys.pgp.net
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

---

### Post by Seisen on 2007-09-25
Comment this line out

```
deb http://archive.canonical.com feisty-commercial main 
``` put one of these (#) in front of it. Then 

```
sudo apt-get update
``` if you get no errors uncomment that same line and then do another ```
sudo apt-get update
``` and let me know if it fixed the problem.

---

### Post by wilkinsd on 2007-09-26
Hi,

I commented out this entry but still got the same error.  I then went through a process of commenting out all the feisty-update entries running "apt-get update" then uncommenting them one at a time and this worked for the first run of "apt-get update" after the "sources.list" file was back to it's orginal state, but then on the second run I got a new error related to MD5Sum mismatch error for Packages.bz2.  In the meantime I got the latest security updates and was able to install them, so hopefully I can at least install the packages I need to get the server working and the MD5Sum mismatch error will sort itself out.

Thanks for all your help.

---

