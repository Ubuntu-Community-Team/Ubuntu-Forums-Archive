---
title: "Cannot Upgrade Feisty [Connection Refused]"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by haargerman on 2007-10-18
I'm hoping someone can help me out here. 
I've been having troubles upgrading my Feisty Fawn through the Uprade Manager. 
This is the errors I get:

[B]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences. [/B]

[http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://us.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to us.archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg:) Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
[http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:](http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2:) Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/dapper/Release.gpg:](http://asher256-repository.tuxfamily.org/dists/dapper/Release.gpg:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/dapper/main/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/dapper/main/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/dapper/dupdate/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/dapper/french/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/dapper/french/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg:) Could not connect to archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:](http://archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to archive.ubuntu.com:80 (91.189.88.43). - connect (111 Connection refused) [IP: 91.189.88.43 80]
[http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gpg:](http://asher256-repository.tuxfamily.org/dists/ubuntu/Release.gpg:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/ubuntu/main/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/ubuntu/main/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/ubuntu/dupdate/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)
[http://asher256-repository.tuxfamily.org/dists/ubuntu/french/i18n/Translation-en_US.bz2:](http://asher256-repository.tuxfamily.org/dists/ubuntu/french/i18n/Translation-en_US.bz2:) Could not connect to asher256-repository.tuxfamily.org:80 (212.85.158.4). - connect (111 Connection refused)

Does anyone know why this is happening? I'm wondering if it is just my school's network being really lame because the proxy they have us use for the internet pretty much sucks. However I've tried turning the proxy on and off but I still have no luck.

I can also get to archive.ubuntu.com through FireFox and I am able to ping it. So this is having my head going in circles.

Any help is greatly appreciated. 

Thanks!

---

### Post by linuxwizard on 2007-10-18
Try removing or disable your extra repos. from source list.

Using packages from repositories not controlled by Ubuntu is not recommended as it can be a security risk and may break or complicate your upgrade.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by haargerman on 2007-10-19
I'll try it out.

Thanks for the reply.

---

