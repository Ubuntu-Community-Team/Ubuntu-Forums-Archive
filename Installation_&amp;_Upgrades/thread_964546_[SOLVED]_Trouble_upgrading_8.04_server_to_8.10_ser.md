---
title: "[SOLVED] Trouble upgrading 8.04 server to 8.10 server"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by j3ff on 2008-10-31
I am currently unable to upgrade my 8.04 server to an 8.10 server.
In short, after following the instructions at

[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Servers%20(Recommended))

I see 

Checking for a new ubuntu release
No new release found

Any help or advice would be greatly appreciated.

Thanks,
Jeff

Here is a transcript of my terminal session:-

Confirm the identity of the distro and its version

```
jeff@meldte:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 8.04.1
Release:        8.04
Codename:       hardy

```

Check machine architecture
```
jeff@meldte:~$ uname -m
i686
```

Check kernel version
```
jeff@meldte:~$ uname -r
2.6.24-21-server
```

Make sure that the machine is currently up to date:-
```
jeff@meldte:~$ sudo apt-get update
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_AU
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_AU
Ign http://security.ubuntu.com hardy-security/universe Translation-en_AU
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_AU
Hit http://security.ubuntu.com hardy-security Release
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Ign http://au.archive.ubuntu.com hardy Release.gpg
Ign http://au.archive.ubuntu.com hardy/main Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/universe Translation-en_AU
Ign http://au.archive.ubuntu.com hardy/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com hardy-updates Release.gpg
Ign http://au.archive.ubuntu.com hardy-updates/main Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/restricted Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/universe Translation-en_AU
Ign http://au.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU
Hit http://au.archive.ubuntu.com hardy Release
Hit http://au.archive.ubuntu.com hardy-updates Release
Hit http://au.archive.ubuntu.com hardy/main Packages
Hit http://au.archive.ubuntu.com hardy/restricted Packages
Hit http://au.archive.ubuntu.com hardy/main Sources
Hit http://au.archive.ubuntu.com hardy/restricted Sources
Hit http://au.archive.ubuntu.com hardy/universe Packages
Hit http://au.archive.ubuntu.com hardy/universe Sources
Hit http://au.archive.ubuntu.com hardy/multiverse Packages
Hit http://au.archive.ubuntu.com hardy/multiverse Sources
Hit http://au.archive.ubuntu.com hardy-updates/main Packages
Hit http://au.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://au.archive.ubuntu.com hardy-updates/main Sources
Hit http://au.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://au.archive.ubuntu.com hardy-updates/universe Packages
Hit http://au.archive.ubuntu.com hardy-updates/universe Sources
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://au.archive.ubuntu.com hardy-updates/multiverse Sources
Reading package lists... Done
```

Upgrade anything that is out of date.  Nothing is.
```
jeff@meldte:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Step 1 of the official instructions ...
```
jeff@meldte:~$ sudo apt-get install update-manager-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Confirmation that I did step 2 ...
```
jeff@meldte:~$ cat /etc/update-manager/release-upgrades 
# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal

```
Step 3 ...  
```
jeff@meldte:~$ sudo do-release-upgrade
Checking for a new ubuntu release
No new release found
```

and that's all she wrote.

---

### Post by Coastal Confessions on 2008-10-31
do-release-upgrade is working for me, but I'm using us.archive.ubuntu.com. Maybe it's just that your servers aren't up-to-date yet.

---

### Post by Sherban on 2008-10-31
I had the same problem... as every six months.

I am behind a proxy and setting the proxy information on command line solved this for me:

export http_proxy=http://user:passwd@proxy:port/
export ftp_proxy=http://user:passwd@proxy:port/

This should really be part of the update instructions...

---

### Post by j3ff on 2008-11-02
Thanks Coastal confessions and Sherban for your replies.

Sherban, your suggestion seems to have done the trick.  The original 'hardy' installation asked for proxy details so I would not have thought of that.

Anyway, setting the http_proxy environment variable seems to have done the trick. 

Thanks very much.

---

