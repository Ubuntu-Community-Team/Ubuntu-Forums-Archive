---
title: "After update can't install apache2 anymore"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by zeehond on 2008-10-16
```
root@vm05:~# apt-get install php5
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
  libapr1 libaprutil1 libexpat1 libpq5 libxml2 php5-common
Suggested packages:
  apache2-doc php-pear
Recommended packages:
  xml-core
The following NEW packages will be installed:
  apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
  libapr1 libaprutil1 libexpat1 libpq5 libxml2 php5 php5-common
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/5290kB of archives.
After this operation, 13.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libexpat1.
(Reading database ... 22921 files and directories currently installed.)
Unpacking libexpat1 (from .../libexpat1_2.0.1-0ubuntu1_i386.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.2.11-1_i386.deb) ...
Selecting previously deselected package libpq5.
Unpacking libpq5 (from .../libpq5_8.3.3-0ubuntu0.8.04_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.12+dfsg-3_i386.deb) ...
Selecting previously deselected package apache2-utils.
Unpacking apache2-utils (from .../apache2-utils_2.2.8-1ubuntu0.3_i386.deb) ...
Selecting previously deselected package apache2.2-common.
Unpacking apache2.2-common (from .../apache2.2-common_2.2.8-1ubuntu0.3_i386.deb) ...
Selecting previously deselected package apache2-mpm-prefork.
Unpacking apache2-mpm-prefork (from .../apache2-mpm-prefork_2.2.8-1ubuntu0.3_i386.deb) ...
Selecting previously deselected package libxml2.
Unpacking libxml2 (from .../libxml2_2.6.31.dfsg-2ubuntu1.2_i386.deb) ...
Selecting previously deselected package php5-common.
Unpacking php5-common (from .../php5-common_5.2.4-2ubuntu5.3_i386.deb) ...
Selecting previously deselected package libapache2-mod-php5.
Unpacking libapache2-mod-php5 (from .../libapache2-mod-php5_5.2.4-2ubuntu5.3_i386.deb) ...
Selecting previously deselected package php5.
Unpacking php5 (from .../php5_5.2.4-2ubuntu5.3_all.deb) ...
Setting up libexpat1 (2.0.1-0ubuntu1) ...

Setting up libapr1 (1.2.11-1) ...

Setting up libpq5 (8.3.3-0ubuntu0.8.04) ...

Setting up libaprutil1 (1.2.12+dfsg-3) ...

Setting up apache2-utils (2.2.8-1ubuntu0.3) ...
Setting up apache2.2-common (2.2.8-1ubuntu0.3) ...
Segmentation fault
dpkg: error processing apache2.2-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.8-1ubuntu0.3); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
Setting up libxml2 (2.6.31.dfsg-2ubuntu1.2) ...

Setting up php5-common (5.2.4-2ubuntu5.3) ...
dpkg: dependency problems prevent configuration of libapache2-mod-php5:
 libapache2-mod-php5 depends on apache2-mpm-prefork (>> 2.0.52) | apache2-mpm-itk; however:
  Package apache2-mpm-prefork is not configured yet.
  Package apache2-mpm-itk is not installed.
 libapache2-mod-php5 depends on apache2.2-common; however:
  Package apache2.2-common is not configured yet.
dpkg: error processing libapache2-mod-php5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of php5:
 php5 depends on libapache2-mod-php5 (>= 5.2.4-2ubuntu5.3) | php5-cgi (>= 5.2.4-2ubuntu5.3); however:
  Package libapache2-mod-php5 is not configured yet.
  Package php5-cgi is not installed.
dpkg: error processing php5 (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 apache2.2-common
 apache2-mpm-prefork
 libapache2-mod-php5
 php5
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Running strace on /usr/sbin/apache2 yields

```
root@vm05:~# strace /usr/sbin/apache2
execve("/usr/sbin/apache2", ["/usr/sbin/apache2"], [/* 16 vars */]) = 0
brk(0)                                  = 0x80a0000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3d000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=20383, ...}) = 0
mmap2(NULL, 20383, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f38000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpcre.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\360\16"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=157240, ...}) = 0
mmap2(NULL, 156036, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f11000
mmap2(0xb7f37000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x26) = 0xb7f37000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libaprutil-1.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`_\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=103292, ...}) = 0
mmap2(NULL, 106196, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ef7000
mmap2(0xb7f10000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18) = 0xb7f10000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapr-1.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\225\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=146448, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ef6000
mmap2(NULL, 145240, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ed2000
mmap2(0xb7ef5000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb7ef5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=112354, ...}) = 0
mmap2(NULL, 94688, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7eba000
mmap2(0xb7ece000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7ece000
mmap2(0xb7ed0000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ed0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260e\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1364388, ...}) = 0
mmap2(NULL, 1369712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d6b000
mmap2(0xb7eb4000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x149) = 0xb7eb4000
mmap2(0xb7eb7000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7eb7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libldap_r-2.4.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\237\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=250884, ...}) = 0
mmap2(NULL, 258344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d2b000
mmap2(0xb7d68000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3c) = 0xb7d68000
mmap2(0xb7d69000, 4392, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7d69000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/liblber-2.4.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\"\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=48668, ...}) = 0
mmap2(NULL, 51548, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d1e000
mmap2(0xb7d2a000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb) = 0xb7d2a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdb-4.6.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P|\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1206852, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d1d000
mmap2(NULL, 1206136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bf6000
mmap2(0xb7d1b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x125) = 0xb7d1b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libpq.so.5", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0pT\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=127796, ...}) = 0
mmap2(NULL, 126632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7bd7000
mmap2(0xb7bf5000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e) = 0xb7bf5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/local/lib/libsqlite3.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\303\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1333219, ...}) = 0
mmap2(NULL, 404580, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b74000
mmap2(0xb7bd5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x60) = 0xb7bd5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libexpat.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220!\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=131652, ...}) = 0
mmap2(NULL, 134432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b53000
mmap2(0xb7b72000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e) = 0xb7b72000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libuuid.so.1", O_RDONLY)     = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\20\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13188, ...}) = 0
mmap2(NULL, 15896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b4f000
mmap2(0xb7b52000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xb7b52000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/librt.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\31"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30624, ...}) = 0
mmap2(NULL, 33360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b46000
mmap2(0xb7b4d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb7b4d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libcrypt.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\7\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38300, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7b45000
mmap2(NULL, 201052, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b13000
mmap2(0xb7b1c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7b1c000
mmap2(0xb7b1e000, 155996, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7b1e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7b0f000
mmap2(0xb7b11000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7b11000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libresolv.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@!\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=67408, ...}) = 0
mmap2(NULL, 75972, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7afc000
mmap2(0xb7b0b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf) = 0xb7b0b000
mmap2(0xb7b0d000, 6340, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7b0d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libsasl2.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p1\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=89192, ...}) = 0
mmap2(NULL, 92072, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ae5000
mmap2(0xb7afb000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb7afb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgnutls.so.13", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\33"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=484420, ...}) = 0
mmap2(NULL, 483196, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7a6f000
mmap2(0xb7ae0000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x71) = 0xb7ae0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libssl.so.0.9.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\300"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=264420, ...}) = 0
mmap2(NULL, 267320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7a2d000
mmap2(0xb7a6b000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3d) = 0xb7a6b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libcrypto.so.0.9.8", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\301"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1300836, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7a2c000
mmap2(NULL, 1317240, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb78ea000
mmap2(0xb7a14000, 86016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x129) = 0xb7a14000
mmap2(0xb7a29000, 10616, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7a29000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\346\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=573268, ...}) = 0
mmap2(NULL, 576132, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb785d000
mmap2(0xb78e8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8a) = 0xb78e8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libcom_err.so.2", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7444, ...}) = 0
mmap2(NULL, 10308, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb785a000
mmap2(0xb785c000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb785c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgssapi_krb5.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20@\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=167832, ...}) = 0
mmap2(NULL, 166716, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7831000
mmap2(0xb7859000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x28) = 0xb7859000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtasn1.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\21"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=61596, ...}) = 0
mmap2(NULL, 64900, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7821000
mmap2(0xb7830000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe) = 0xb7830000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libz.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=81240, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7820000
mmap2(NULL, 83968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb780b000
mmap2(0xb781f000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb781f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcrypt.so.11", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PD\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=310956, ...}) = 0
mmap2(NULL, 314504, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb77be000
mmap2(0xb7809000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4a) = 0xb7809000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libk5crypto.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0204\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=143008, ...}) = 0
mmap2(NULL, 142464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb779b000
mmap2(0xb77bd000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x22) = 0xb77bd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkrb5support.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\25\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=27524, ...}) = 0
mmap2(NULL, 30344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7793000
mmap2(0xb779a000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb779a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libkeyutils.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\10"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=5644, ...}) = 0
mmap2(NULL, 8524, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7790000
mmap2(0xb7792000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7792000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgpg-error.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\6\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=11468, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb778f000
mmap2(NULL, 14352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb778b000
mmap2(0xb778e000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xb778e000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb778a000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7789000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7789700, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7eb4000, 4096, PROT_READ)   = 0
munmap(0xb7f38000, 20383)               = 0
set_tid_address(0xb7789748)             = 5150
set_robust_list(0xb7789750, 0xc)        = 0
futex(0xbffa0090, 0x81 /* FUTEX_??? */, 1) = -1 ENOSYS (Function not implemented)
rt_sigaction(SIGRTMIN, {0xb7ebe2c0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7ebe340, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="vm05", ...})  = 0
brk(0)                                  = 0x80a0000
brk(0x80c1000)                          = 0x80c1000
brk(0x80e3000)                          = 0x80e3000
socket(PF_NETLINK, SOCK_RAW, 0)         = 3
bind(3, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, pid=5150, groups=00000000}, [12]) = 0
time(NULL)                              = 1224185560
sendto(3, "\24\0\0\0\26\0\1\3\330\226\367H\0\0\0\0\0\0\0\0", 20, 0, {sa_family=AF_NETLINK, pid=0, groups=00000000}, 12) = 20
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"0\0\0\0\24\0\2\0\330\226\367H\36\24\0\0\2\10\200\376\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 108
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"@\0\0\0\24\0\2\0\330\226\367H\36\24\0\0\n\200\200\376\1"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 128
recvmsg(3, {msg_name(12)={sa_family=AF_NETLINK, pid=0, groups=00000000}, msg_iov(1)=[{"\24\0\0\0\3\0\2\0\330\226\367H\36\24\0\0\0\0\0\0\1\0\0"..., 4096}], msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
stat64("/etc/apache2/apache2.conf", {st_mode=S_IFREG|0644, st_size=10587, ...}) = 0
open("/etc/apache2/apache2.conf", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=10587, ...}) = 0
brk(0x8105000)                          = 0x8105000
read(3, "#\n# Based upon the NCSA server c"..., 4096) = 4096
stat64("/etc/apache2", {st_mode=S_IFDIR|0755, st_size=320, ...}) = 0
read(3, "t number of worker threads in ea"..., 4096) = 4096
stat64("/etc/apache2/mods-enabled", {st_mode=S_IFDIR|0755, st_size=48, ...}) = 0
open("/etc/apache2/mods-enabled", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|0x80000) = 4
fstat64(4, {st_mode=S_IFDIR|0755, st_size=48, ...}) = 0
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
getdents(4, /* 2 entries */, 4096)      = 32
getdents(4, /* 0 entries */, 4096)      = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++
Process 5150 detached

```

Any advices?

---

### Post by cariboo on 2008-10-16
For some reason dpkg seg faulted in the middle of your installation see quote:

> Setting up apache2-utils (2.2.8-1ubuntu0.3) ...
Setting up apache2.2-common (2.2.8-1ubuntu0.3) ...
**Segmentation fault**
dpkg: error processing apache2.2-common (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of apache2-mpm-prefork:
 apache2-mpm-prefork depends on apache2.2-common (= 2.2.8-1ubuntu0.3); however:
  Package apache2.2-common is not configured yet.
dpkg: error processing apache2-mpm-prefork (--configure):
 dependency problems - leaving unconfigured
Setting up libxml2 (2.6.31.dfsg-2ubuntu1.2) .

Can you still install a package using dpkg?

Jim

---

### Post by zeehond on 2008-10-17
Nope.

It seems like last libc6 update broke everything (?).

I tried installing feisty (7.10) with debootstrap, then apt-get install update-manager-core, then do-release-upgrade - and it fails on many packages with segfaults...

---

