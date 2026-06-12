---
title: "Update issue  - URGENT"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by joshlfisher on 2007-05-30
I had a lot of updates, so I selected to update. Then there was an error. Now this:


```
joshua@lyekka:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  konqueror vim-common
Suggested packages:
  libgcj7-awt libjessie-java
The following packages will be upgraded:
  konqueror vim-common
2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
4 not fully installed or removed.
Need to get 0B/3037kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 92281 files and directories currently installed.)
Preparing to replace vim-common 1:7.0-164+1ubuntu7 (using .../vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb) ...
Unpacking replacement vim-common ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 9
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Preparing to replace kate 4:3.5.6-0ubuntu20 (using .../kate_4%3a3.5.6-0ubuntu20_i386.deb) ...
Unpacking replacement kate ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/kate_4%3a3.5.6-0ubuntu20_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 9
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Preparing to replace konqueror 4:3.5.6-0ubuntu20 (using .../konqueror_4%3a3.5.6-0ubuntu20.1_i386.deb) ...
Unpacking replacement konqueror ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 9
dpkg - trying script from the new package instead ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/konqueror_4%3a3.5.6-0ubuntu20.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 9
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb
 /var/cache/apt/archives/kate_4%3a3.5.6-0ubuntu20_i386.deb
 /var/cache/apt/archives/konqueror_4%3a3.5.6-0ubuntu20.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
joshua@lyekka:~$   
```

What's up? How do I fix this?

I tried the sudo dpkg --configure -a
It configured a bunch, but stopped on Vim-common

---

### Post by glenroe on 2007-06-05
I'm seeing something similar. This machine is a server that has been updated from Breezy Badger through the intervening versions to feisty. It is conceivable that I might have skipped a version...would that cause this problem? What else can I check?

I am pasting two sets of errors below for apt-get remove and apt-get dist-upgrade - 

sudo apt-get remove vim-common gives the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  vim-common
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
19 not fully installed or removed.
Need to get 0B/146kB of archives.
After unpacking 578kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing vim-common (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 vim-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

XXXXXXXX@rhaegar:/etc/apt$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  vim-common vim-gui-common
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
19 not fully installed or removed.
Need to get 0B/332kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 49248 files and directories currently installed.)
Preparing to replace vim-common 1:7.0-164+1ubuntu7 (using .../vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb) ...
Unpacking replacement vim-common ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 5
dpkg - trying script from the new package instead ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb (--unpack):
 subprocess new post-removal script returned error exit status 5
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 5
Preparing to replace vim-gui-common 1:7.0-164+1ubuntu7 (using .../vim-gui-common_1%3a7.0-164+1ubuntu7.1_all.deb) ...
Unpacking replacement vim-gui-common ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: warning - old post-removal script returned error exit status 5
dpkg - trying script from the new package instead ...
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error processing /var/cache/apt/archives/vim-gui-common_1%3a7.0-164+1ubuntu7.1_all.deb (--unpack):
 subprocess new post-removal script returned error exit status 5
File/Glob.pm did not return a true value at /usr/sbin/update-mime line 54.
BEGIN failed--compilation aborted at /usr/sbin/update-mime line 54.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 5
Errors were encountered while processing:
 /var/cache/apt/archives/vim-common_1%3a7.0-164+1ubuntu7.1_i386.deb
 /var/cache/apt/archives/vim-gui-common_1%3a7.0-164+1ubuntu7.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
XXXXXXXX@rhaegar:/etc/apt$

---

