---
title: "git-core failing to install on Lucid - libdigest-sha1-perl hanging"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by serenecloud on 2011-04-22
Yesterday I rebuilt my EeePC 701 to serve as a file server in the house. I'm most of the way there but it also needs to be a git repository, and I can't install git :(

Here's what I see now. The first time I tried to install git-core I got a similar result - hanging on libdigest-sha1-perl install.

root@hope:~# sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libdigest-sha1-perl patch
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk gitweb diffutils-doc
The following NEW packages will be installed:
  git-core patch
The following packages will be upgraded:
  libdigest-sha1-perl
1 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 5,761kB/5,787kB of archives.
After this operation, 12.0MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ubuntu.catalyst.net.nz/ubuntu/](http://ubuntu.catalyst.net.nz/ubuntu/) lucid-updates/main git-core 1:1.7.0.4-1ubuntu0.2 [5,638kB]
Get:2 [http://ubuntu.catalyst.net.nz/ubuntu/](http://ubuntu.catalyst.net.nz/ubuntu/) lucid/main patch 2.6-2ubuntu1 [123kB]
Fetched 5,761kB in 4s (1,201kB/s)
(Reading database ... 124391 files and directories currently installed.)
Preparing to replace libdigest-sha1-perl 2.12-1build1 (using .../libdigest-sha1-perl_2.12-1build1_i386.deb) ...
Unpacking replacement libdigest-sha1-perl ...


I can't remove it because when I try I'm told I need to install it properly first and I can't install it because it's hanging. I've tried clearing out my apt cache, a different mirror and I even tried installing the maverick and lucid versions using dpkg - all get me to the same result. I have 1.2GB free on the SSD so it's not a space issue either and I'm out of good ideas.

---

### Post by serenecloud on 2011-04-22
Well, I left the hung process and went to have lunch. When I returned I found that

1. The install had worked (it could have taken up to an hour, but certainly more than 15 minutes)
2. The copy/backup I was running had also finished

I'm wondering if having a big cp comment running was related to the hanging?

---

