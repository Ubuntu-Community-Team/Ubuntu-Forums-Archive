---
title: "Dhelp with segmentation fault"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by acepoint on 2005-10-18
Hi folks,

did a fresh installation a few days ago. Everything is fine besides one package: dhelp

> Building HTML tree .../var/lib/dpkg/info/dhelp.postinst: line 45:  2265 Segmentation fault      /usr/sbin/dhelp_parse -r
dpkg: error processing dhelp (--configure):
subprocess post-installation script returned error exit status 139
Errors were encountered while processing:
dhelp
E: Sub-process /usr/bin/dpkg returned an error code (1)


A "[COLOR="Blue"]strace /usr/sbin/dhelp_parse -r[/COLOR]" gives the following output:

> ...
lstat64("/usr/share/doc/libdigest-sha1-perl/changelog.Debian.gz", {st_mode=S_IFREG|0644, st_size=624, ...}) = 0
getdents64(4, /* 0 entries */, 4096)    = 0
close(4)                                = 0
getdents64(3, /* 0 entries */, 4096)    = 0
brk(0x806d000)                          = 0x806d000
close(3)                                = 0
open("/var/lib/dhelp/dbase", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1626112, ...}) = 0
_llseek(3, 0, [0], SEEK_SET)            = 0
read(3, "\0\0\0\0\0\0\0\0\0\0\0\0b1\5\0\10\0\0\0\0\20\0\0\0\t\0"..., 256) = 256
close(3)                                = 0
stat64("/var/tmp", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=91, ...}) = 0
open("/var/lib/dhelp/dbase", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1626112, ...}) = 0
mmap2(NULL, 1626112, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7b86000
open("/var/lib/dhelp/titles", O_RDWR|O_CREAT|O_EXCL|O_LARGEFILE, 0644) = -1 EEXIST (File exists)
open("/var/lib/dhelp/titles", O_RDWR|O_LARGEFILE) = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=266240, ...}) = 0
_llseek(4, 0, [0], SEEK_SET)            = 0
read(4, "\0\0\0\0\0\0\0\0\0\0\0\0a\25\6\0\7\0\0\0\0\20\0\0\0\10"..., 256) = 256
close(4)                                = 0
stat64("/var/tmp", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=91, ...}) = 0
open("/var/lib/dhelp/titles", O_RDWR|O_LARGEFILE) = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=266240, ...}) = 0
brk(0x808e000)                          = 0x808e000
pread64(4, "\0\0\0\0\0\0\0\0\0\0\0\0a\25\6\0\7\0\0\0\0\20\0\0\0\10"..., 4096, 0) = 4096
open("/usr/share/doc/HTML", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 5
fstat64(5, {st_mode=S_IFDIR|0755, st_size=31, ...}) = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
getdents64(5, /* 4 entries */, 4096)    = 112
lstat64("/usr/share/doc/HTML/README", {st_mode=S_IFREG|0644, st_size=144, ...}) = 0
unlink("/usr/share/doc/HTML/README")    = 0
lstat64("/usr/share/doc/HTML/HOWTO", {st_mode=S_IFDIR|0755, st_size=23, ...}) = 0
open("/usr/share/doc/HTML/HOWTO", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 6
fstat64(6, {st_mode=S_IFDIR|0755, st_size=23, ...}) = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
getdents64(6, /* 3 entries */, 4096)    = 80
lstat64("/usr/share/doc/HTML/HOWTO/index.html", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
unlink("/usr/share/doc/HTML/HOWTO/index.html") = 0
getdents64(6, /* 0 entries */, 4096)    = 0
close(6)                                = 0
rmdir("/usr/share/doc/HTML/HOWTO")      = 0
getdents64(5, /* 0 entries */, 4096)    = 0
close(5)                                = 0
mkdir("/usr/share/doc/HTML", 0755)      = -1 EEXIST (File exists)
chdir("/usr/share/doc/HTML")            = 0
open("README", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 5
fstat64(5, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b85000
write(5, "\nDon\'t put files in this directo"..., 144) = 144
close(5)                                = 0
munmap(0xb7b85000, 4096)                = 0
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=142, ...}) = 0
lstat64("/usr/share", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
lstat64("/usr/share/doc", {st_mode=S_IFDIR|0755, st_size=69632, ...}) = 0
lstat64("/usr/share/doc/HTML", {st_mode=S_IFDIR|0755, st_size=19, ...}) = 0
getcwd("/usr/share/doc/HTML", 4096)     = 20
mkdir("HOWTO", 0755)                    = 0
chdir("HOWTO")                          = 0
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=142, ...}) = 0
lstat64("/usr/share", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
lstat64("/usr/share/doc", {st_mode=S_IFDIR|0755, st_size=69632, ...}) = 0
lstat64("/usr/share/doc/HTML", {st_mode=S_IFDIR|0755, st_size=31, ...}) = 0
getcwd("/usr/share/doc/HTML/HOWTO", 4096) = 26
open("index.html", O_WRONLY|O_CREAT|O_TRUNC, 0666) = 5
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=142, ...}) = 0
lstat64("/usr/share", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
lstat64("/usr/share/doc", {st_mode=S_IFDIR|0755, st_size=69632, ...}) = 0
lstat64("/usr/share/doc/HTML", {st_mode=S_IFDIR|0755, st_size=31, ...}) = 0
getcwd("/usr/share/doc/HTML/HOWTO", 4096) = 26
pread64(4, "\0\0\0\0\0\0\0\0\34\0\0\0\0\0\0\0\0\0\0\0\f\0\205\17\0"..., 4096, 114688) = 4096
fstat64(5, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b85000
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=142, ...}) = 0
lstat64("/usr/share", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
lstat64("/usr/share/doc", {st_mode=S_IFDIR|0755, st_size=69632, ...}) = 0
lstat64("/usr/share/doc/HTML", {st_mode=S_IFDIR|0755, st_size=31, ...}) = 0
getcwd("/usr/share/doc/HTML/HOWTO", 4096) = 26
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++


The index.html is not created. Any ideas?

Ciao

acepoint

---

### Post by Tomas_IV on 2006-01-26
No ideas. ;-)
But I can confirm you are not alone. Exactly the same beaviour when trying to install package dhelp.

---

