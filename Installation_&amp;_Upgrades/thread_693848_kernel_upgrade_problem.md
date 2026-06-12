---
title: "kernel upgrade problem"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by gotodengo23 on 2008-02-11
When tying to apply latest kernel upgrade (via update manager) I'm getting following error:

> 
debconf: Perl may be unconfigured (Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 98951 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb) ...
Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 9
Unrecognized character \xDE at /usr/lib/perl/5.8/Cwd.pm line 1.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb


I'm a linux newbie, and it's all Greek to me. Any ideas?

---

### Post by Pumalite on 2008-02-11
Post:
uname -a

---

### Post by gotodengo23 on 2008-02-11
uname -a:
> Linux wlodek 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

---

### Post by Pumalite on 2008-02-11
What was your command?

---

### Post by gotodengo23 on 2008-02-11
$ uname -a

---

### Post by Pumalite on 2008-02-11
For the upgrade I mean.

---

### Post by gotodengo23 on 2008-02-11
silly me, I did not use any command, this is what I get whenever I'm trying to update via  update manager by clicking on notification icon

---

### Post by Pumalite on 2008-02-11
Update and upgrade are two different things. If you were updating I don't understand the need to compile anything.

---

### Post by gotodengo23 on 2008-02-11
Again my fault, the headline is misleading, I should have written "kernel update problem". There's security update available (linux-image-2.6.22-14-generic), but when I'm trying to install it I get the error message I've quoted in my first post. Moreover I can't install, or uninstall anything using synaptic package manager, because it fails to install the kernel update.

---

### Post by Pumalite on 2008-02-11
Your problem is with apt-get then. Maybe your update got interrupted. Post the output of:
sudo apt-get install -f

---

### Post by gotodengo23 on 2008-02-11
Thanks for your patience - 

> ~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.22-14-generic
Suggested packages:
  linux-doc-2.6.22 linux-source-2.6.22
The following packages will be upgraded:
  linux-image-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B/18.5MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
(Reading database ... 98958 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb) ...
Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 9
Unrecognized character \xDE at /usr/lib/perl/5.8/Cwd.pm line 1.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pumalite on 2008-02-11
Try this:
sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb
(it should be all one command)

---

### Post by gotodengo23 on 2008-02-11
~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb
[sudo] password for wlodek:
(Reading database ... 98958 files and directories currently installed.)
Preparing to replace linux-image-2.6.22-14-generic 2.6.22-14.47 (using .../linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb) ...
Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at /usr/share/perl5/Debconf/Template.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Template.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Question.pm line 8.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Question.pm line 8.
Compilation failed in require at /usr/share/perl5/Debconf/Config.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Config.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 10.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb (--install):
 subprocess pre-installation script returned error exit status 9
Unrecognized character \xDE at /usr/lib/perl/5.8/Cwd.pm line 1.
Compilation failed in require at /var/lib/dpkg/tmp.ci/postrm line 21.
BEGIN failed--compilation aborted at /var/lib/dpkg/tmp.ci/postrm line 21.
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 9
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.22-14-generic_2.6.22-14.51_i386.deb

---

### Post by Pumalite on 2008-02-11
Take a look at /var/lib/dpkg/status and see what's the status of the offending file. Report back.

---

### Post by gotodengo23 on 2008-02-11
Package: linux-image-2.6.22-14-generic
Status: install reinstreq half-installed
Priority: optional
Section: base
Installed-Size: 62352
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: i386
Source: linux-source-2.6.22
Version: 2.6.22-14.47
Config-Version: 2.6.22-14.47
Provides: linux-image, linux-image-2.6, fuse-module, kvm-api-4, rhcs-modules2-1, ivtv-modules
Depends: initramfs-tools (>= 0.36ubuntu6), coreutils | fileutils (>= 4.0), module-init-tools (>= 3.2.1-0ubuntu1)
Pre-Depends: dpkg (>= 1.10.24)
Recommends: lilo (>= 19.1) | grub
Suggests: fdutils, linux-doc-2.6.22 | linux-source-2.6.22
Conflicts: hotplug (<< 0.0.20040105-1)

---

### Post by Pumalite on 2008-02-11
We can attempt a partial under the table fix here that will let you continue using apt-get. Backup your file first:
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.old
gksudo gedit /var/lib/dpkg/status
Change the status of the file to: installed...ok...installed
Save, exit and see if you can use apt-get. You might need to reboot.
Report back.

---

### Post by gotodengo23 on 2008-02-12
Still no luck. 

> sudo apt-get --purge remove gnash
[sudo] password for wlodek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnucrypto-java libcairo-jni libgtk-jni libcairo-java libglib-jni
  libbcprov-java libglib-java libgtk-java
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnash* mozilla-plugin-gnash*
0 upgraded, 0 newly installed, 2 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1069kB disk space will be freed.
Do you want to continue [Y/n]? y
debconf: Perl may be unconfigured (Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.
Compilation failed in require at /usr/share/perl/5.8/FileHandle.pm line 9.
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
dpkg: parse error, in file `/var/lib/dpkg/status' near line 10375 package `linux-image-2.6.22-14-generic':
 Configured-Version for package with inappropriate Status
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

### Post by freymann on 2008-02-12
> **gotodengo23 said:**
> Still no luck.
debconf: Perl may be unconfigured (Unrecognized character \xDE at /usr/lib/perl/5.8/IO/File.pm line 1.

 I'm just having a look through this thread, and I am wondering if by chance there is something wrong with line 1 of the file indicated above?

 On my machine (I have a slightly newer version of Perl) line 1 is simply a # sign...

 I wonder if yours is out of whack?

 Something to consider....

---

### Post by gotodengo23 on 2008-02-13
Well, I gave up. I've just reinstalled the system, and everything is working smoothly now. Thanks anyway.

---

