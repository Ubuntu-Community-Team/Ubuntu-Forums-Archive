---
title: "Not able to install any packages in ubuntu 9.04"
date: 2010-07-20
forum: Installation &amp; Upgrades
---

### Post by dineshsriram on 2010-07-20
Hi,
   I was trying to install git the other day and I system shutdown because of a power cut. Later, when i tried installing git, I get the following error message. In fact, I am not able to install any .deb packages. I get the same error when I try installing them  :(

```

dineshsriram@dineshsriram-desktop:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libbsd0 ttf-liberation
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdigest-sha1-perl liberror-perl patch
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk
  gitweb diffutils-doc
The following NEW packages will be installed:
  git libdigest-sha1-perl liberror-perl patch
0 upgraded, 4 newly installed, 0 to remove and 938 not upgraded.
1 not fully installed or removed.
Need to get 0B/5902kB of archives.
After this operation, 12.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  patch libdigest-sha1-perl git
Install these packages without verification [y/N]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
[B]dpkg: `ldconfig' not found on PATH.
dpkg: 1 expected program(s) not found on PATH.
NB: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/B]dineshsriram@dineshsriram-desktop:~$ 

```I use Ubuntu 9.04 and my system information is below.

```
dineshsriram@dineshsriram-desktop:~$ uname -a
Linux dineshsriram-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux

```Any help would be highly appreciated. Thanks :)

---

### Post by dineshsriram on 2010-07-20
I get the same error message even if I try to remove/upgrade any packages :(

---

### Post by sohnythomas on 2010-07-21
try these commands 

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove
sudo deborphan | xargs sudo apt-get remove --purge

---

### Post by dineshsriram on 2010-07-25
@sohnythomas
Thanks. As I said, I am not able to install any packages. I get the following error message when I try to install clean.
```

dineshsriram@dineshsriram-desktop:~$ sudo apt-get clean
E: Lists directory /var/lib/apt/lists/partial is missing.
dineshsriram@dineshsriram-desktop:~$ 

```

I also ran a **fsck** and then **sudo apt-get --fix-broken**. That still didn't solve my problem :(
Any suggestions on the right direction would be of great help.

---

### Post by dino99 on 2010-07-25
[http://www.debianhelp.co.uk/debianproblem.htm](http://www.debianhelp.co.uk/debianproblem.htm)

---

