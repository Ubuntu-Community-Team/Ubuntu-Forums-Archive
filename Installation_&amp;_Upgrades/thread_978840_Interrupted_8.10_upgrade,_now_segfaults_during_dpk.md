---
title: "Interrupted 8.10 upgrade, now segfaults during dpkg (install-docs?)"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by staffordrau on 2008-11-11
I had an interrupted 8.04 to 8.10 upgrade, and I now have this server in a state where dpkg --configure -a (or any package) dies with one of the sub-processes segfaulting.

Lots of details to follow - I'm hoping to not have to completely reinstall this box, but will do whatever is necessary.

root@toolbox:~# uname -a
Linux toolbox 2.6.24-21-xen #1 SMP Wed Oct 22 02:11:27 UTC 2008 i686 GNU/Linux

root@toolbox:~# apt-get update
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Translation-en_US
*<snip>*
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid-updates/multiverse Sources
Fetched 8771kB in 2min23s (61.2kB/s)
Reading package lists... Done

root@toolbox:~# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libdbd-pg-perl libossp-uuid15 libcurl3 libxen3 xen-docs-3.2 zlib1g-dev libfreetype6-dev postgresql-common postgresql-8.2
  postgresql-8.3 python-xen-3.2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gcc-4.3-base libruby1.8 ruby1.8-dev
The following NEW packages will be installed:
  gcc-4.3-base
The following packages will be upgraded:
  libruby1.8 ruby1.8-dev
2 upgraded, 1 newly installed, 0 to remove and 832 not upgraded.
6 not fully installed or removed.
Need to get 0B/2127kB of archives.
After this operation, 610kB of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up findutils (4.4.0-2ubuntu3) ...
Segmentation fault
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
 findutils
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@toolbox:~# 
root@toolbox:~# dpkg --configure -a
dpkg: dependency problems prevent configuration of libncurses-ruby1.8:
 libncurses-ruby1.8 depends on libruby1.8 (>= 1.8.7.17); however:
  Version of libruby1.8 on system is 1.8.6.111-2ubuntu1.2.
dpkg: error processing libncurses-ruby1.8 (--configure):
 dependency problems - leaving unconfigured
Setting up findutils (4.4.0-2ubuntu3) ...
Segmentation fault
dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 139
Setting up postgresql-8.2 (8.2.9-0ubuntu0.7.10) ...
Segmentation fault
dpkg: error processing postgresql-8.2 (--configure):
 subprocess post-installation script returned error exit status 139
Setting up postgresql-8.3 (8.3.3-0ubuntu0.8.04) ...
Segmentation fault
dpkg: error processing postgresql-8.3 (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of libstdc++6:
 libstdc++6 depends on gcc-4.3-base (= 4.3.2-1ubuntu11); however:
  Package gcc-4.3-base is not installed.
dpkg: error processing libstdc++6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dselect:
 dselect depends on libstdc++6 (>= 4.1.1); however:
  Package libstdc++6 is not configured yet.
dpkg: error processing dselect (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libncurses-ruby1.8
 findutils
 postgresql-8.2
 postgresql-8.3
 libstdc++6
 dselect
root@toolbox:~# 

*Trying to figure out what's going on here:*

root@toolbox:~# strace dpkg --configure findutils 2> dpkg-findutils-segfault  

*From the strace output. I can post all of it if anyone cares, but this is what I'm guessing is the relevant section:*

rename("/var/lib/dpkg/updates/tmp.i", "/var/lib/dpkg/updates/0000") = 0
open("/var/lib/dpkg/updates/tmp.i", O_WRONLY|O_CREAT|O_TRUNC|O_LARGEFILE, 0666) = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7cf8000
write(4, "#padding\n#padding\n#padding\n#padd"..., 4096) = 4096
write(4, "padding\n#padding\n#padding\n#paddi"..., 512) = 512
_llseek(4, 0, [0], SEEK_SET)            = 0
stat64("/var/lib/dpkg/info/findutils.postinst", {st_mode=S_IFREG|0755, st_size=1544, ...}) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e20768) = 9979
rt_sigaction(SIGQUIT, {SIG_IGN}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGINT, {SIG_IGN}, {SIG_DFL}, 8) = 0
waitpid(9979, Segmentation fault
[{WIFEXITED(s) && WEXITSTATUS(s) == 139}], 0) = 9979
--- SIGCHLD (Child exited) @ 0 (0) ---
write(2, "dpkg: error processing findutils"..., 116dpkg: error processing findutils (--configure):
 subprocess post-installation script returned error exit status 139
) = 116

*So maybe the findutils.postinst script?*

root@toolbox:~# /var/lib/dpkg/info/findutils.postinst configure findutils
Segmentation fault
root@toolbox:~#

*So I copied findutils.postinst to my local directory, and added a "set -x" to it:*

root@toolbox:~# ./findutils.postinst configure findutils
+ [ configure = configure ]
+ dpkg --compare-versions findutils le-nl 4.1.7-2
+ [ -d /var/cache/locate/ ]
+ dpkg --compare-versions findutils le-nl 4.2.31-1
+ [ configure = configure ]
+ which install-docs
+ install-docs -i /usr/share/doc-base/findutils
Segmentation fault

*So it appears that install-docs is failing:*

root@toolbox:~# install-docs
Usage:
     install-docs [options] -i,--install | -r,--remove | -c,--check file [ file ... ]

     install-docs [options] -I,--install-all | -R,--remove-all

     install-docs [options] -s,--status docid [ docid ... ]

     install-docs -h | --help

root@toolbox:~# install-docs -i /usr/share/doc-base/findutils
Segmentation fault

*install-docs is a Perl script, but since I get the Usage: message with no params, I'm guessing that the problem is not necessarily with the Perl interpreter.*

Suggestions most highly welcome at this point. Thanks if you've read this far.

--Stafford

---

### Post by staffordrau on 2008-11-11
Just for a bit more info, here is the end of an install-docs strace run:

                             = 022
stat64("/var/lib/doc-base/info/FORCE-REREGISTER.flag", 0x81530c8) = -1 ENOENT (No such file or directory)
stat64("/usr/share/doc-base/findutils", {st_mode=S_IFREG|0644, st_size=323, ...}) = 0
open("/usr/share/doc-base/findutils", O_RDONLY|O_LARGEFILE) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfb77fb8) = -1 ENOTTY (Inappropriate ioctl for device)
_llseek(4, 0, [0], SEEK_CUR)            = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=323, ...}) = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
read(4, "Document: findutils\nTitle: findu"..., 4096) = 323
read(4, "", 4096)                       = 0
stat64("/usr/share/info/find.info.gz", {st_mode=S_IFREG|0644, st_size=85402, ...}) = 0
open("/usr/share/info/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = 5
fstat64(5, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(5, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents64(5, /* 30 entries */, 4096)   = 1064
lstat64("/usr/share/info/find.info.gz", {st_mode=S_IFREG|0644, st_size=85402, ...}) = 0
getdents64(5, /* 0 entries */, 4096)    = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 16429 detached

---

### Post by staffordrau on 2008-11-12
This turned out to be a Perl bug, with a stack overflow during deep recursion regex's.

This appears to be the specific bug:

[http://rt.perl.org/rt3/Public/Bug/Display.html?id=37230](http://rt.perl.org/rt3/Public/Bug/Display.html?id=37230)

My fix was to manually force install the perl-5.10 debs, then redo the whole apt-get update/apt-get -f install/apt-get dist-upgrade process.

---

### Post by iponeverything on 2008-11-12
good debugging. glad to see you give up.

---

