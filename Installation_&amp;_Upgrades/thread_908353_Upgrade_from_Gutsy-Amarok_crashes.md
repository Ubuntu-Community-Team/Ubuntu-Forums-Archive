---
title: "Upgrade from Gutsy-Amarok crashes"
date: 2008-09-02
forum: Installation &amp; Upgrades
---

### Post by wczimmerman on 2008-09-02
I finally got around to upgrading my laptop from Gutsy this past weekend.  I had an issue with kmix giving a "Bus Error" when run on the command line which was fixed by reinstalling kmix and removing all traces of kmixrc and directories in $HOME/.kde/...

I'm now getting a Bus Error with Amarok.  I've tried the same steps with this app, but it's still giving that error.  

Here's the strace output:

~/.kde/share/config$ strace amarokapp
execve("/usr/bin/amarokapp", ["amarokapp"], [/* 35 vars */]) = 0
brk(0)                                  = 0x8077000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f92000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 5
fstat64(5, {st_mode=S_IFREG|0644, st_size=84362, ...}) = 0
mmap2(NULL, 84362, PROT_READ, MAP_PRIVATE, 5, 0) = 0xb7f7d000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libamarok.so.0", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240z\22"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=5379856, ...}) = 0
mmap2(NULL, 5435256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb7a4e000
mmap2(0xb7f44000, 184320, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x4f5) = 0xb7f44000
mmap2(0xb7f71000, 49016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f71000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkutils.so.1", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200p\2"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=395984, ...}) = 0
mmap2(NULL, 394896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb79ed000
mmap2(0xb7a49000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x5c) = 0xb7a49000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkio.so.4", O_RDONLY)  = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20*\17"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=3360564, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb79ec000
mmap2(NULL, 3366708, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb76b6000
mmap2(0xb79d0000, 114688, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x319) = 0xb79d0000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkdeui.so.4", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\262"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=2972104, ...}) = 0
mmap2(NULL, 2977644, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb73df000
mmap2(0xb768d000, 167936, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x2ad) = 0xb768d000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkdecore.so.4", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\306"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=2300968, ...}) = 0
mmap2(NULL, 2309152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb71ab000
mmap2(0xb73cf000, 57344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x224) = 0xb73cf000
mmap2(0xb73dd000, 7200, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb73dd000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkhtml.so.4", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\352\f"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=4056056, ...}) = 0
mmap2(NULL, 4061340, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6dcb000
mmap2(0xb717e000, 180224, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x3b2) = 0xb717e000
mmap2(0xb71aa000, 2204, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb71aa000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libknewstuff.so.1", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260b\1"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=250940, ...}) = 0
mmap2(NULL, 253848, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6d8d000
mmap2(0xb6dc9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x3b) = 0xb6dc9000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtag.so.1", O_RDONLY)  = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\330"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=306008, ...}) = 0
mmap2(NULL, 306152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6d42000
mmap2(0xb6d8b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x49) = 0xb6d8b000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 D\1\000"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=394924, ...}) = 0
mmap2(NULL, 398984, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6ce0000
mmap2(0xb6d3b000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x5b) = 0xb6d3b000
mmap2(0xb6d41000, 1672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6d41000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libsqlite3.so.0", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\316"..., 512) = 512
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6cdf000
fstat64(5, {st_mode=S_IFREG|0644, st_size=410036, ...}) = 0
mmap2(NULL, 413188, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6c7a000
mmap2(0xb6cdd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x62) = 0xb6cdd000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libtunepimp.so.5", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\301"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=270932, ...}) = 0
mmap2(NULL, 269612, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6c38000
mmap2(0xb6c79000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x41) = 0xb6c79000
close(5)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/sse2", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686/cmov", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/lib/tls/i686/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/i686", {st_mode=S_IFDIR|0755, st_size=17, ...}) = 0
open("/lib/tls/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/lib/tls/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/sse2", 0xbfe2a98c)     = -1 ENOENT (No such file or directory)
open("/lib/tls/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls/cmov", 0xbfe2a98c)     = -1 ENOENT (No such file or directory)
open("/lib/tls/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/tls", {st_mode=S_IFDIR|0755, st_size=17, ...}) = 0
open("/lib/i686/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/lib/i686/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/sse2", 0xbfe2a98c)    = -1 ENOENT (No such file or directory)
open("/lib/i686/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686/cmov", 0xbfe2a98c)    = -1 ENOENT (No such file or directory)
open("/lib/i686/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/i686", 0xbfe2a98c)         = -1 ENOENT (No such file or directory)
open("/lib/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2/cmov", 0xbfe2a98c)    = -1 ENOENT (No such file or directory)
open("/lib/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/sse2", 0xbfe2a98c)         = -1 ENOENT (No such file or directory)
open("/lib/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib/cmov", 0xbfe2a98c)         = -1 ENOENT (No such file or directory)
open("/lib/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/lib", {st_mode=S_IFDIR|0755, st_size=8192, ...}) = 0
open("/usr/lib/tls/i686/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/sse2", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/i686/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/i686", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/sse2", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/tls/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/tls", 0xbfe2a98c)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/sse2", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/i686/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686/cmov", {st_mode=S_IFDIR|0755, st_size=53, ...}) = 0
open("/usr/lib/i686/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/i686", {st_mode=S_IFDIR|0755, st_size=17, ...}) = 0
open("/usr/lib/sse2/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2/cmov", 0xbfe2a98c) = -1 ENOENT (No such file or directory)
open("/usr/lib/sse2/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/sse2", 0xbfe2a98c)     = -1 ENOENT (No such file or directory)
open("/usr/lib/cmov/libmysqlclient.so.15", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/cmov", 0xbfe2a98c)     = -1 ENOENT (No such file or directory)
open("/usr/lib/libmysqlclient.so.15", O_RDONLY) = 5
read(5, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200\231"..., 512) = 512
fstat64(5, {st_mode=S_IFREG|0644, st_size=1159168, ...}) = 0
mmap2(NULL, 1963360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 5, 0) = 0xb6a58000
mmap2(0xb6bf4000, 274432, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 5, 0x19b) = 0xb6bf4000
--- SIGBUS (Bus error) @ 0 (0) ---
+++ killed by SIGBUS +++
Process 12584 detached

---

