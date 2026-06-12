---
title: "man (manual) broken after upgrade to Ubuntu 24.04.1 LTS"
date: 2024-10-14
forum: Installation &amp; Upgrades
---

### Post by ryanbin2 on 2024-10-14
Hi,

I recently upgraded to Ubuntu 24.04.1 LTS and noticed that when I try to run the man command after the upgrade, I get the following error message:
[INDENT]```
man: error while loading shared libraries: libmandb-2.10.2.so: cannot open shared object file: No such file or directory
```
[/INDENT]

I've tried manually copying the file from another machine into the ```
/usr/lib/man-db/
``` directory. Also tried purging man and reinstalling. Still get the error.

Anyone else seeing this?

---

### Post by him610 on 2024-10-16
Not seeing what you are seeing about man-db. 
No need to copy from other machine. If necessary, just reinstall.
Show results between code tags -
```

apt show  man-db && apt policy man-db

```

---

### Post by ryanbin2 on 2024-10-16
Thanks for the reply. Already tried purging and reinstalling, no luck. Here's the output from apt:
```

ryan@home:~$ apt show  man-db && apt policy man-db
Package: man-db
Version: 2.12.0-4build2
Priority: standard
Section: doc
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Colin Watson <cjwatson@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 2998 kB
Provides: man, man-browser
Depends: bsdextrautils | bsdmainutils (<< 12.1.1~), groff-base, debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.38), libgdbm6t64 (>= 1.16), libpipeline1 (>= 1.5.0), libseccomp2 (>= 2.1.0), zlib1g (>= 1:1.1.4)
Suggests: apparmor, groff, less, www-browser
Conflicts: man
Replaces: man, nlsutils
Homepage: https://man-db.gitlab.io/man-db/
Task: standard, ubuntu-wsl
Download-Size: 1237 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
Description: tools for reading manual pages
 This package provides the man command, the primary way of examining the
 system help files (manual pages). Other utilities provided include the
 whatis and apropos commands for searching the manual page database, the
 manpath utility for determining the manual page search path, and the
 maintenance utilities mandb, catman and zsoelim. man-db uses the groff
 suite of programs to format and display the manual pages.
man-db:
  Installed: 2.12.0-4build2
  Candidate: 2.12.0-4build2
  Version table:
 *** 2.12.0-4build2 500
        500 http://us.archive.ubuntu.com/ubuntu noble/main amd64 Packages
        100 /var/lib/dpkg/status
ryan@home:~$ man man
man: error while loading shared libraries: libmandb-2.10.2.so: cannot open shared object file: No such file or directory
ryan@home:~$

```

---

### Post by him610 on 2024-10-17
This looks like root of your issue...
> man: error while loading shared libraries: libmandb-2.10.2.so: cannot open shared object file: No such file or directory
ryan@home:~$

Not sure , but maybe this will fix it...
```
sudo apt reinstall man-db
```

---

### Post by ryanbin2 on 2024-10-17
No luck:

```

ryan@home:~$ sudo apt reinstall man-db
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 3 not upgraded.
Need to get 1237 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu noble/main amd64 man-db amd64 2.12.0-4build2 [1237 kB]
Fetched 1237 kB in 1s (2287 kB/s)
debconf: delaying package configuration, since apt-utils is not installed
(Reading database ... 133795 files and directories currently installed.)
Preparing to unpack .../man-db_2.12.0-4build2_amd64.deb ...
Unpacking man-db (2.12.0-4build2) over (2.12.0-4build2) ...
Setting up man-db (2.12.0-4build2) ...
debconf: unable to initialize frontend: Dialog
debconf: (No usable dialog-like program is installed, so the dialog based frontend cannot be used. at /usr/share/perl5/Debconf/FrontEnd/Dialog.pm line 79.)
debconf: falling back to frontend: Readline
Updating database of manual pages ...
man-db.service is a disabled or a static unit not running, not starting it.
Scanning processes...
Scanning processor microcode...
Scanning linux images...
Running kernel seems to be up-to-date.
The processor microcode seems to be up-to-date.
No services need to be restarted.
No containers need to be restarted.
No user sessions are running outdated binaries.
No VM guests are running outdated hypervisor (qemu) binaries on this host.
ryan@home:~$ man man
man: error while loading shared libraries: libmandb-2.10.2.so: cannot open shared object file: No such file or directory
ryan@home:~$

```

---

### Post by Rubi1200 on 2024-10-17
As another step to help resolve this, let's try this:
```
sudo apt update
sudo apt --fix-broken install

```

Any luck?

---

### Post by ryanbin2 on 2024-10-18
No luck. 

```

ryan@home:~$ sudo apt update
Hit:1 http://security.ubuntu.com/ubuntu noble-security InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu noble InRelease
Hit:3 http://us.archive.ubuntu.com/ubuntu noble-updates InRelease
Hit:4 http://us.archive.ubuntu.com/ubuntu noble-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.
ryan@home:~$ apt list --upgradable
Listing... Done
libcephfs2/noble-updates 19.2.0-0ubuntu0.24.04.1 amd64 [upgradable from: 19.2.0~git20240301.4c76c50-0ubuntu6.1]
librados2/noble-updates 19.2.0-0ubuntu0.24.04.1 amd64 [upgradable from: 19.2.0~git20240301.4c76c50-0ubuntu6.1]
ryan@home:~$ sudo apt --fix-broken install
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
ryan@home:~$ man man
man: error while loading shared libraries: libmandb-2.10.2.so: cannot open shared object file: No such file or directory
ryan@home:~$

```

---

### Post by ActionParsnip on 2024-10-18
That file is in the man-db package
[https://packages.ubuntu.com/search?searchon=contents&keywords=libmandb&mode=filename&suite=noble&arch=any](https://packages.ubuntu.com/search?searchon=contents&keywords=libmandb&mode=filename&suite=noble&arch=any)
If you run:
```

updatedb
locate libmandb

```
What is the output?

---

### Post by ryanbin2 on 2024-10-18
```

ryan@home:~$ sudo updatedb
[sudo] password for ryan: 
ryan@home:~$ locate libmandb
/usr/lib/man-db/libmandb-2.12.0.so
/usr/lib/man-db/libmandb.so
ryan@home:~$ cd /usr/lib/man-db/
ryan@home:/usr/lib/man-db$ ls -l
total 296
-rw-r--r-- 1 root root 267008 Apr  8  2024 libman-2.12.0.so
lrwxrwxrwx 1 root root     16 Apr  8  2024 libman.so -> libman-2.12.0.so
-rw-r--r-- 1 root root  30864 Apr  8  2024 libmandb-2.12.0.so
lrwxrwxrwx 1 root root     18 Apr  8  2024 libmandb.so -> libmandb-2.12.0.so
lrwxrwxrwx 1 root root     13 Apr  8  2024 man -> ../../bin/man
lrwxrwxrwx 1 root root     15 Apr  8  2024 mandb -> ../../bin/mandb

```

For some reason, it wants libmandb-2.10.2.so, but libmandb-2.12.0.so is what's installed.

---

### Post by ActionParsnip on 2024-10-18
> **ryanbin2 said:**
> ```

ryan@home:~$ sudo updatedb
[sudo] password for ryan: 
ryan@home:~$ locate libmandb
/usr/lib/man-db/libmandb-2.12.0.so
/usr/lib/man-db/libmandb.so
ryan@home:~$ cd /usr/lib/man-db/
ryan@home:/usr/lib/man-db$ ls -l
total 296
-rw-r--r-- 1 root root 267008 Apr  8  2024 libman-2.12.0.so
lrwxrwxrwx 1 root root     16 Apr  8  2024 libman.so -> libman-2.12.0.so
-rw-r--r-- 1 root root  30864 Apr  8  2024 libmandb-2.12.0.so
lrwxrwxrwx 1 root root     18 Apr  8  2024 libmandb.so -> libmandb-2.12.0.so
lrwxrwxrwx 1 root root     13 Apr  8  2024 man -> ../../bin/man
lrwxrwxrwx 1 root root     15 Apr  8  2024 mandb -> ../../bin/mandb

```

For some reason, it wants libmandb-2.10.2.so, but libmandb-2.12.0.so is what's installed.

Could try a symlink. Worth a shot

---

### Post by ryanbin2 on 2024-10-18
Ran an strace on man. It really really wants that libmandb-2.10.2.so.  I tried copying it from another machine into /usr/lib/man-db and /lib/glibc-hwcaps/x86-64-v2/ but still no luck.

```

ryan@home:~$ strace man
execve("/usr/bin/man", ["man"], 0x7ffd03ec8580 /* 21 vars */) = 0
brk(NULL)                               = 0x5adf36b3c000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7d037f91d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/man-db/glibc-hwcaps/x86-64-v3/libmandb-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/man-db/glibc-hwcaps/x86-64-v3/", 0x7ffc05524750, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/man-db/glibc-hwcaps/x86-64-v2/libmandb-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/man-db/glibc-hwcaps/x86-64-v2/", 0x7ffc05524750, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/man-db/libmandb-2.10.2.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=30864, ...}) = 0
mmap(NULL, 33072, PROT_READ, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7d037f914000
mprotect(0x7d037f916000, 20480, PROT_NONE) = 0
mmap(0x7d037f916000, 12288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7d037f916000
mmap(0x7d037f919000, 4096, PROT_READ, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5000) = 0x7d037f919000
mmap(0x7d037f91b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7d037f91b000
close(3)                                = 0
openat(AT_FDCWD, "/usr/lib/man-db/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=36319, ...}) = 0
mmap(NULL, 36319, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7d037f90b000
close(3)                                = 0
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v3/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v3/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v2/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v2/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/x86_64-linux-gnu/", {st_mode=S_IFDIR|0755, st_size=61440, ...}, 0) = 0
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v3/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v3/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v2/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/glibc-hwcaps/x86-64-v2/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/", {st_mode=S_IFDIR|0755, st_size=61440, ...}, 0) = 0
openat(AT_FDCWD, "/lib/glibc-hwcaps/x86-64-v3/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/glibc-hwcaps/x86-64-v3/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/glibc-hwcaps/x86-64-v2/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/glibc-hwcaps/x86-64-v2/", {st_mode=S_IFDIR|0755, st_size=4096, ...}, 0) = 0
openat(AT_FDCWD, "/lib/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/lib/", {st_mode=S_IFDIR|0755, st_size=4096, ...}, 0) = 0
openat(AT_FDCWD, "/usr/lib/glibc-hwcaps/x86-64-v3/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/glibc-hwcaps/x86-64-v3/", 0x7ffc05524730, 0) = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/glibc-hwcaps/x86-64-v2/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/glibc-hwcaps/x86-64-v2/", {st_mode=S_IFDIR|0755, st_size=4096, ...}, 0) = 0
openat(AT_FDCWD, "/usr/lib/libman-2.10.2.so", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
newfstatat(AT_FDCWD, "/usr/lib/", {st_mode=S_IFDIR|0755, st_size=4096, ...}, 0) = 0
writev(2, [{iov_base="man", iov_len=3}, {iov_base=": ", iov_len=2}, {iov_base="error while loading shared libra"..., iov_len=36}, {iov_base=": ", iov_len=2}, {iov_base="libman-2.10.2.so", iov_len=16}, {iov_base=": ", iov_len=2}, {iov_base="cannot open shared object file", iov_len=30}, {iov_base=": ", iov_len=2}, {iov_base="No such file or directory", iov_len=25}, {iov_base="\n", iov_len=1}], 10man: error while loading shared libraries: libman-2.10.2.so: cannot open shared object file: No such file or directory
) = 119
exit_group(127)                         = ?
+++ exited with 127 +++

```

---

### Post by ryanbin2 on 2024-11-02
Thought I fixed it with sudo based on [this post]("https://www.linuxquestions.org/questions/linux-software-2/error-while-loading-shared-libraries-no-such-file-or-directory-4175717461/page2.html"), but still having the same issue. Doesn't work with sudo either.

---

