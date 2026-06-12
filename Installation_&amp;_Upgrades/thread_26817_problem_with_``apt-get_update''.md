---
title: "problem with ``apt-get update''"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by chaitatp on 2005-04-14
Friends, I've got some problems... Y_Y

I had a fresh installation of ``Hoary''. Then I tried to install more packages with ``apt'' by

``sudo apt-get update''

And the following is the output.

--------
chaitatp@taladnoi:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release.gpg [189B]
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release
Ign [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary/restricted Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/main Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/main Sources
Hit [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates/restricted Sources
Fetched 567B in 0s (791B/s)
Reading package lists... Done

W: GPG error: [http://th.archive.ubuntu.com](http://th.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems

chaitatp@taladnoi:~$
---------

What should I do? ...

I've already done this:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)


Please help.  Thanks in advance

---

