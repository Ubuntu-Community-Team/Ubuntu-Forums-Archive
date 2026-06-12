---
title: "Upgrade from Kubuntu 15.04 to 15.10 Segmentation Dumps &amp; Acces Violations"
date: 2015-11-21
forum: Installation &amp; Upgrades
---

### Post by Arlen_B_Taylor on 2015-11-21
I recently accepted the upgrade from Kubuntu 15.04 to 15.10.  Since that time, Firefox stopped working showing on Konsole as Segmentation Fault (core dumped).  From the desktop it simply runs briefly then stops.  KDbg initially would open but operate thereafter. I had to use System Monitor to kill the process. Later, it followed the path of Firefox.  I did discover that files needed were placed in an odd location /usr/lib/usr/lib/x86_64-linux-gnu.  GDB wouldn't work initially, but after moving libraries around it would at least open.  Lazarus-ide has been causing me constant trouble with access violations showing.  Initially, it would open run, then crash, but more recently not open at all showing access violations.  I downloaded the latest version and attempted to re-compile to start over.  After a great deal of effort, I have gotten Free Pascal running, but Lazarus-ide build always fails near the end of the process.  I have been in their forums for about a week.

Here is an example of trying to run in Konsole the program LazBuild:

```
arlen@Dumbledore:~/Development/FreePascal/lazarus$ ./lazbuild
An unhandled exception occurred at $00007FEB164074B7:
EAccessViolation: Access violation
An unhandled exception occurred at $00007FEB15C30F24:
EAccessViolation: Access violation
  $00007FEB15C30F24
```

Here is a stack trace for Firefox:

```
$ strace firefox
execve("/usr/bin/firefox", ["firefox"], [/* 54 vars */]) = 0
brk(0)                                  = 0x55da19d94000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f70d2ad3000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=156356, ...}) = 0
mmap(NULL, 156356, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f70d2aac000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\v\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1869392, ...}) = 0
mmap(NULL, 3972864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f70d24e8000
mprotect(0x7f70d26a8000, 2097152, PROT_NONE) = 0
mmap(0x7f70d28a8000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c0000) = 0x7f70d28a8000
mmap(0x7f70d28ae000, 16128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f70d28ae000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f70d2aab000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f70d2aaa000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f70d2aa9000
arch_prctl(ARCH_SET_FS, 0x7f70d2aaa700) = 0
mprotect(0x7f70d28a8000, 16384, PROT_READ) = 0
mprotect(0x55da1920a000, 8192, PROT_READ) = 0
mprotect(0x7f70d2ad5000, 4096, PROT_READ) = 0
munmap(0x7f70d2aac000, 156356)          = 0
getuid()                                = 1000
getgid()                                = 1000
getpid()                                = 21219
rt_sigaction(SIGCHLD, {0x55da19001030, ~[RTMIN RT_1], SA_RESTORER, 0x7f70d251d2f0}, NULL, 8) = 0
geteuid()                               = 1000
brk(0)                                  = 0x55da19d94000
brk(0x55da19db5000)                     = 0x55da19db5000
getppid()                               = 21216
stat("/home/arlen/Development/FreePascal/lazarus", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
open("/usr/bin/firefox", O_RDONLY)      = 3
fcntl(3, F_DUPFD, 10)                   = 10
close(3)                                = 0
fcntl(10, F_SETFD, FD_CLOEXEC)          = 0
geteuid()                               = 1000
getegid()                               = 1000
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x55da19001030, ~[RTMIN RT_1], SA_RESTORER, 0x7f70d251d2f0}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f70d251d2f0}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {SIG_DFL, ~[RTMIN RT_1], SA_RESTORER, 0x7f70d251d2f0}, NULL, 8) = 0
read(10, "#!/bin/sh\n\nset -e\n\n# Firefox lau"..., 8192) = 2667
pipe([3, 4])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f70d2aaa9d0) = 21220
close(4)                                = 0
read(3, "/usr/bin/firefox\n", 128)      = 17
read(3, "", 128)                        = 0
--- SIGCHLD {si_signo=SIGCHLD, si_code=CLD_EXITED, si_pid=21220, si_status=0, si_utime=0, si_stime=0} ---
rt_sigreturn()                          = 0
close(3)                                = 0
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 21220
geteuid()                               = 1000
faccessat(AT_FDCWD, "/usr/lib/firefox/firefox", X_OK) = 0
execve("/usr/lib/firefox/firefox", ["/usr/lib/firefox/firefox"], [/* 55 vars */]) = 0
brk(0)                                  = 0x55f24dd18000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfad8000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=156356, ...}) = 0
mmap(NULL, 156356, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fcecfab1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340`\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=142080, ...}) = 0
mmap(NULL, 2217232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcecf699000
mprotect(0x7fcecf6b1000, 2097152, PROT_NONE) = 0
mmap(0x7fcecf8b1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0x7fcecf8b1000
mmap(0x7fcecf8b3000, 13584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecf8b3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14592, ...}) = 0
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcecf495000
mprotect(0x7fcecf498000, 2093056, PROT_NONE) = 0
mmap(0x7fcecf697000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fcecf697000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libstdc++.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \240\10\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1566568, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfab0000
mmap(NULL, 3675328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcecf113000
mprotect(0x7fcecf286000, 2093056, PROT_NONE) = 0
mmap(0x7fcecf485000, 49152, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x172000) = 0x7fcecf485000
mmap(0x7fcecf491000, 13504, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecf491000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240U\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1084840, ...}) = 0
mmap(NULL, 3174760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcecee0b000
mprotect(0x7fcecef12000, 2093056, PROT_NONE) = 0
mmap(0x7fcecf111000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x106000) = 0x7fcecf111000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcc_s.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360*\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=92504, ...}) = 0
mmap(NULL, 2188352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcecebf4000
mprotect(0x7fcecec0a000, 2093056, PROT_NONE) = 0
mmap(0x7fcecee09000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7fcecee09000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\v\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1869392, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfaaf000
mmap(NULL, 3972864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcece82a000
mprotect(0x7fcece9ea000, 2097152, PROT_NONE) = 0
mmap(0x7fcecebea000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c0000) = 0x7fcecebea000
mmap(0x7fcecebf0000, 16128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecebf0000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfaae000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfaac000
arch_prctl(ARCH_SET_FS, 0x7fcecfaac740) = 0
mprotect(0x7fcecebea000, 16384, PROT_READ) = 0
mprotect(0x7fcecee09000, 4096, PROT_READ) = 0
mprotect(0x7fcecf111000, 4096, PROT_READ) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfaab000
mprotect(0x7fcecf485000, 40960, PROT_READ) = 0
mprotect(0x7fcecf697000, 4096, PROT_READ) = 0
mprotect(0x7fcecf8b1000, 4096, PROT_READ) = 0
mprotect(0x55f24d335000, 4096, PROT_READ) = 0
mprotect(0x7fcecfada000, 4096, PROT_READ) = 0
munmap(0x7fcecfab1000, 156356)          = 0
set_tid_address(0x7fcecfaaca10)         = 21219
set_robust_list(0x7fcecfaaca20, 24)     = 0
rt_sigaction(SIGRTMIN, {0x7fcecf69ebb0, [], SA_RESTORER|SA_SIGINFO, 0x7fcecf6a9d10}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7fcecf69ec40, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7fcecf6a9d10}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
readlink("/etc/malloc.conf", 0x7ffcfb2f17d7, 4096) = -1 ENOENT (No such file or directory)
mmap(NULL, 1048576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecf9ab000
munmap(0x7fcecf9ab000, 1048576)         = 0
mmap(NULL, 2093056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcece62b000
munmap(0x7fcece62b000, 872448)          = 0
munmap(0x7fcece800000, 172032)          = 0
mmap(NULL, 1048576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecf9ab000
munmap(0x7fcecf9ab000, 1048576)         = 0
mmap(NULL, 2093056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcece501000
munmap(0x7fcece501000, 1044480)         = 0
getrusage(RUSAGE_SELF, {ru_utime={0, 4000}, ru_stime={0, 0}, ...}) = 0
lstat("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
lstat("/usr/lib/firefox", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
stat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
access("/usr/lib/firefox/libxul.so", R_OK) = 0
open("/usr/lib/firefox/dependentlibs.list", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=127, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfad7000
read(3, "libnspr4.so\nlibplc4.so\nlibplds4."..., 4096) = 127
open("/usr/lib/firefox/libnspr4.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\315\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 252488)                 = 0
close(4)                                = 0
futex(0x7fcecf6980c8, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/firefox/libnspr4.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\315\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=254408, ...}) = 0
mmap(NULL, 2360224, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcece3bf000
mprotect(0x7fcece3fa000, 2097152, PROT_NONE) = 0
mmap(0x7fcece5fa000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3b000) = 0x7fcece5fa000
mmap(0x7fcece5fd000, 9120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcece5fd000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=156356, ...}) = 0
mmap(NULL, 156356, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7fcecfa84000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220!\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=31680, ...}) = 0
mmap(NULL, 2128864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcece1b7000
mprotect(0x7fcece1be000, 2093056, PROT_NONE) = 0
mmap(0x7fcece3bd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6000) = 0x7fcece3bd000
close(4)                                = 0
mprotect(0x7fcece3bd000, 4096, PROT_READ) = 0
mprotect(0x7fcece5fa000, 8192, PROT_READ) = 0
munmap(0x7fcecfa84000, 156356)          = 0
open("/usr/lib/firefox/libplc4.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\25\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 16504)                  = 0
close(4)                                = 0
open("/usr/lib/firefox/libplc4.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\25\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=18344, ...}) = 0
mmap(NULL, 2113680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecdfb2000
mprotect(0x7fcecdfb6000, 2093056, PROT_NONE) = 0
mmap(0x7fcece1b5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3000) = 0x7fcece1b5000
close(4)                                = 0
mprotect(0x7fcece1b5000, 4096, PROT_READ) = 0
open("/usr/lib/firefox/libplds4.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\20\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 12440)                  = 0
close(4)                                = 0
open("/usr/lib/firefox/libplds4.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\20\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14280, ...}) = 0
mmap(NULL, 2109648, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecddae000
mprotect(0x7fcecddb1000, 2093056, PROT_NONE) = 0
mmap(0x7fcecdfb0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcecdfb0000
close(4)                                = 0
mprotect(0x7fcecdfb0000, 4096, PROT_READ) = 0
open("/usr/lib/firefox/libnssutil3.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\275\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 163856)                 = 0
close(4)                                = 0
open("/usr/lib/firefox/libnssutil3.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\275\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=165856, ...}) = 0
mmap(NULL, 2262432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecdb85000
mprotect(0x7fcecdba7000, 2097152, PROT_NONE) = 0
mmap(0x7fcecdda7000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x22000) = 0x7fcecdda7000
close(4)                                = 0
mprotect(0x7fcecdda7000, 24576, PROT_READ) = 0
open("/usr/lib/firefox/libnss3.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \205\1\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 1022968)                = 0
close(4)                                = 0
open("/usr/lib/firefox/libnss3.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \205\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1024968, ...}) = 0
mmap(NULL, 3126120, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecd889000
mprotect(0x7fcecd97d000, 2093056, PROT_NONE) = 0
mmap(0x7fcecdb7c000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xf3000) = 0x7fcecdb7c000
mmap(0x7fcecdb83000, 4968, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecdb83000
close(4)                                = 0
mprotect(0x7fcecdb7c000, 24576, PROT_READ) = 0
open("/usr/lib/firefox/libsmime3.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\221\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 139840)                 = 0
close(4)                                = 0
open("/usr/lib/firefox/libsmime3.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\221\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=141840, ...}) = 0
mmap(NULL, 2237152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecd666000
mprotect(0x7fcecd685000, 2097152, PROT_NONE) = 0
mmap(0x7fcecd885000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1f000) = 0x7fcecd885000
close(4)                                = 0
mprotect(0x7fcecd885000, 12288, PROT_READ) = 0
open("/usr/lib/firefox/libssl3.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\254\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 217472)                 = 0
close(4)                                = 0
open("/usr/lib/firefox/libssl3.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\254\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=219472, ...}) = 0
mmap(NULL, 2317128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecd430000
mprotect(0x7fcecd462000, 2093056, PROT_NONE) = 0
mmap(0x7fcecd661000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x31000) = 0x7fcecd661000
close(4)                                = 0
mprotect(0x7fcecd661000, 16384, PROT_READ) = 0
open("/usr/lib/firefox/libmozsqlite3.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\240\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 638544)                 = 0
close(4)                                = 0
open("/usr/lib/firefox/libmozsqlite3.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\240\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=640472, ...}) = 0
mmap(NULL, 2737480, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecd193000
mprotect(0x7fcecd22b000, 2093056, PROT_NONE) = 0
mmap(0x7fcecd42a000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x97000) = 0x7fcecd42a000
mmap(0x7fcecd42f000, 1352, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecd42f000
close(4)                                = 0
mprotect(0x7fcecd42a000, 12288, PROT_READ) = 0
open("/usr/lib/firefox/liblgpllibs.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@6\0\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 53264)                  = 0
close(4)                                = 0
open("/usr/lib/firefox/liblgpllibs.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@6\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=55184, ...}) = 0
mmap(NULL, 2674688, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fceccf06000
mprotect(0x7fceccf12000, 2097152, PROT_NONE) = 0
mmap(0x7fcecd112000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xc000) = 0x7fcecd112000
mmap(0x7fcecd114000, 520192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecd114000
close(4)                                = 0
mprotect(0x7fcecd112000, 4096, PROT_READ) = 0
open("/usr/lib/firefox/libxul.so", O_RDONLY) = 4
read(4, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0pY\223\0\0\0\0\0"..., 4096) = 4096
readahead(4, 0, 76641640)               = 0
close(4)                                = 0
open("/usr/lib/firefox/libxul.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0pY\223\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=76643640, ...}) = 0
mmap(NULL, 79507888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec8332000
mprotect(0x7fcecc724000, 2097152, PROT_NONE) = 0
mmap(0x7fcecc924000, 5398528, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x43f2000) = 0x7fcecc924000
mmap(0x7fcecce4a000, 766384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcecce4a000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=156356, ...}) = 0
mmap(NULL, 156356, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7fcecfa84000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfreetype.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\273\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=678368, ...}) = 0
mmap(NULL, 2773496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec808c000
mprotect(0x7fcec812c000, 2093056, PROT_NONE) = 0
mmap(0x7fcec832b000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x9f000) = 0x7fcec832b000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfontconfig.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240l\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=252896, ...}) = 0
mmap(NULL, 2348744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7e4e000
mprotect(0x7fcec7e8a000, 2093056, PROT_NONE) = 0
mmap(0x7fcec8089000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3b000) = 0x7fcec8089000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrender.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\32\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39416, ...}) = 0
mmap(NULL, 2134696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7c44000
mprotect(0x7fcec7c4d000, 2093056, PROT_NONE) = 0
mmap(0x7fcec7e4c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7fcec7e4c000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXext.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2205\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=73640, ...}) = 0
mmap(NULL, 2169496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7a32000
mprotect(0x7fcec7a43000, 2093056, PROT_NONE) = 0
mmap(0x7fcec7c42000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x10000) = 0x7fcec7c42000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdamage.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\v\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=10248, ...}) = 0
mmap(NULL, 2105528, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec782f000
mprotect(0x7fcec7831000, 2093056, PROT_NONE) = 0
mmap(0x7fcec7a30000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0x7fcec7a30000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXfixes.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\25\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=22584, ...}) = 0
mmap(NULL, 2117896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7629000
mprotect(0x7fcec762e000, 2093056, PROT_NONE) = 0
mmap(0x7fcec782d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4000) = 0x7fcec782d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXcomposite.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\f\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=10232, ...}) = 0
mmap(NULL, 2105496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7426000
mprotect(0x7fcec7428000, 2093056, PROT_NONE) = 0
mmap(0x7fcec7627000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0x7fcec7627000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libasound.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\241\2\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1003152, ...}) = 0
mmap(NULL, 3098664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec7131000
mprotect(0x7fcec721e000, 2097152, PROT_NONE) = 0
mmap(0x7fcec741e000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xed000) = 0x7fcec741e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\234\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=160488, ...}) = 0
mmap(NULL, 2255992, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec6f0a000
mprotect(0x7fcec6f2f000, 2097152, PROT_NONE) = 0
mmap(0x7fcec712f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x25000) = 0x7fcec712f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdbus-1.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\250\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=309392, ...}) = 0
mmap(NULL, 2405040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec6cbe000
mprotect(0x7fcec6d08000, 2097152, PROT_NONE) = 0
mmap(0x7fcec6f08000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4a000) = 0x7fcec6f08000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\257\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=338984, ...}) = 0
mmap(NULL, 2436872, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec6a6b000
mprotect(0x7fcec6abd000, 2093056, PROT_NONE) = 0
mmap(0x7fcec6cbc000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x51000) = 0x7fcec6cbc000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libglib-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\250\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1106880, ...}) = 0
mmap(NULL, 3204456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec675c000
mprotect(0x7fcec6869000, 2093056, PROT_NONE) = 0
mmap(0x7fcec6a68000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x10c000) = 0x7fcec6a68000
mmap(0x7fcec6a6a000, 1384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec6a6a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\242\6\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=4493736, ...}) = 0
mmap(NULL, 6599064, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec6110000
mprotect(0x7fcec654e000, 2097152, PROT_NONE) = 0
mmap(0x7fcec674e000, 45056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x43e000) = 0x7fcec674e000
mmap(0x7fcec6759000, 8600, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec6759000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libatk-1.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\250\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=150408, ...}) = 0
mmap(NULL, 2246680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec5eeb000
mprotect(0x7fcec5f0d000, 2093056, PROT_NONE) = 0
mmap(0x7fcec610c000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x21000) = 0x7fcec610c000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgio-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000O\3\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1570760, ...}) = 0
mmap(NULL, 3672776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec5b6a000
mprotect(0x7fcec5ce4000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5ee3000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x179000) = 0x7fcec5ee3000
mmap(0x7fcec5ee9000, 6856, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec5ee9000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\331\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=740664, ...}) = 0
mmap(NULL, 2837176, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec58b5000
mprotect(0x7fcec5965000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5b64000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xaf000) = 0x7fcec5b64000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 I\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=52560, ...}) = 0
mmap(NULL, 2147904, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec56a8000
mprotect(0x7fcec56b4000, 2093056, PROT_NONE) = 0
mmap(0x7fcec58b3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xb000) = 0x7fcec58b3000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpango-1.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\336\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=319832, ...}) = 0
mmap(NULL, 2415832, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec545a000
mprotect(0x7fcec54a5000, 2097152, PROT_NONE) = 0
mmap(0x7fcec56a5000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4b000) = 0x7fcec56a5000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libcairo.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\34\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1119664, ...}) = 0
mmap(NULL, 3220704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec5147000
mprotect(0x7fcec5255000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5454000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x10d000) = 0x7fcec5454000
mmap(0x7fcec5458000, 5344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec5458000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220a\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=138640, ...}) = 0
mmap(NULL, 2234080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4f25000
mprotect(0x7fcec4f46000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5145000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec5145000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libstartup-notification-1.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000,\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=35136, ...}) = 0
mmap(NULL, 2130712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4d1c000
mprotect(0x7fcec4d24000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4f23000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7000) = 0x7fcec4f23000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\210\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1285552, ...}) = 0
mmap(NULL, 3382584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec49e2000
mprotect(0x7fcec4b17000, 2097152, PROT_NONE) = 0
mmap(0x7fcec4d17000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x135000) = 0x7fcec4d17000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXt.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2601\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=426320, ...}) = 0
mmap(NULL, 2524896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4779000
mprotect(0x7fcec47db000, 2097152, PROT_NONE) = 0
mmap(0x7fcec49db000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x62000) = 0x7fcec49db000
mmap(0x7fcec49e1000, 1760, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec49e1000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\6\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=6112, ...}) = 0
mmap(NULL, 2101320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4577000
mprotect(0x7fcec4578000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4777000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0x7fcec4777000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\35\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=104824, ...}) = 0
mmap(NULL, 2199880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec435d000
mprotect(0x7fcec4376000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4575000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x18000) = 0x7fcec4575000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpng12.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0;\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=153944, ...}) = 0
mmap(NULL, 2249104, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4137000
mprotect(0x7fcec415c000, 2093056, PROT_NONE) = 0
mmap(0x7fcec435b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x24000) = 0x7fcec435b000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libexpat.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220;\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=166000, ...}) = 0
mmap(NULL, 2261128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3f0e000
mprotect(0x7fcec3f34000, 2097152, PROT_NONE) = 0
mmap(0x7fcec4134000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x26000) = 0x7fcec4134000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libsystemd.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=524024, ...}) = 0
mmap(NULL, 528356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecfa03000
mmap(0x7fcecfa80000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7c000) = 0x7fcecfa80000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\27\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=31016, ...}) = 0
mmap(NULL, 2127464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3d06000
mprotect(0x7fcec3d0d000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3f0c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6000) = 0x7fcec3f0c000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\26\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=444344, ...}) = 0
mmap(NULL, 2539784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3a99000
mprotect(0x7fcec3b05000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3d04000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6b000) = 0x7fcec3d04000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\21\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14624, ...}) = 0
mmap(NULL, 2109880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3895000
mprotect(0x7fcec3898000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3a97000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec3a97000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320s\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=90184, ...}) = 0
mmap(NULL, 2185760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec367f000
mprotect(0x7fcec3693000, 2097152, PROT_NONE) = 0
mmap(0x7fcec3893000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x14000) = 0x7fcec3893000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300[\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=138400, ...}) = 0
mmap(NULL, 2242312, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec345b000
mprotect(0x7fcec347c000, 2093056, PROT_NONE) = 0
mmap(0x7fcec367b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec367b000
mmap(0x7fcec367d000, 5896, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec367d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\3209\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=105328, ...}) = 0
mmap(NULL, 2210632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec323f000
mprotect(0x7fcec3256000, 2097152, PROT_NONE) = 0
mmap(0x7fcec3456000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x17000) = 0x7fcec3456000
mmap(0x7fcec3459000, 6984, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec3459000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXinerama.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\n\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=10376, ...}) = 0
mmap(NULL, 2105640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec303c000
mprotect(0x7fcec303e000, 2093056, PROT_NONE) = 0
mmap(0x7fcec323d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0x7fcec323d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXi.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340!\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=63912, ...}) = 0
mmap(NULL, 2159368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2e2c000
mprotect(0x7fcec2e3b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec303a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xe000) = 0x7fcec303a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrandr.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\34\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=43288, ...}) = 0
mmap(NULL, 2138536, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2c21000
mprotect(0x7fcec2c2b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2e2a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x9000) = 0x7fcec2e2a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXcursor.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 $\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39232, ...}) = 0
mmap(NULL, 2134496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2a17000
mprotect(0x7fcec2a20000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2c1f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7fcec2c1f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libthai.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\33\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=36936, ...}) = 0
mmap(NULL, 2132200, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec280e000
mprotect(0x7fcec2816000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2a15000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7000) = 0x7fcec2a15000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpixman-1.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\231\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=706576, ...}) = 0
mmap(NULL, 2802008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2561000
mprotect(0x7fcec2606000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2805000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa4000) = 0x7fcec2805000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-shm.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\r\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14432, ...}) = 0
mmap(NULL, 2109560, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec235d000
mprotect(0x7fcec235f000, 2097152, PROT_NONE) = 0
mmap(0x7fcec255f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec255f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-render.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2404\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39008, ...}) = 0
mmap(NULL, 2134136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2153000
mprotect(0x7fcec215b000, 2097152, PROT_NONE) = 0
mmap(0x7fcec235b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7fcec235b000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \226\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=133584, ...}) = 0
mmap(NULL, 2228904, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1f32000
mprotect(0x7fcec1f52000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2151000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1f000) = 0x7fcec2151000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-util.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`%\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=22744, ...}) = 0
mmap(NULL, 2117896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1d2c000
mprotect(0x7fcec1d31000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1f30000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4000) = 0x7fcec1f30000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\5\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=5992, ...}) = 0
mmap(NULL, 2101304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1b2a000
mprotect(0x7fcec1b2b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1d2a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0x7fcec1d2a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libSM.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\33\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=30960, ...}) = 0
mmap(NULL, 2126192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1922000
mprotect(0x7fcec1929000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1b28000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6000) = 0x7fcec1b28000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libICE.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260F\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=93824, ...}) = 0
mmap(NULL, 2203520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1708000
mprotect(0x7fcec171e000, 2093056, PROT_NONE) = 0
mmap(0x7fcec191d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x15000) = 0x7fcec191d000
mmap(0x7fcec191f000, 12160, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec191f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320 \0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=137400, ...}) = 0
mmap(NULL, 2232456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec14e6000
mprotect(0x7fcec1507000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1706000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec1706000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcrypt.so.20", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\216\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=924096, ...}) = 0
mmap(NULL, 3020448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1204000
mprotect(0x7fcec12dc000, 2097152, PROT_NONE) = 0
mmap(0x7fcec14dc000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xd8000) = 0x7fcec14dc000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libharfbuzz.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240f\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=383920, ...}) = 0
mmap(NULL, 2480208, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0fa6000
mprotect(0x7fcec1002000, 2097152, PROT_NONE) = 0
mmap(0x7fcec1202000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x5c000) = 0x7fcec1202000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libdatrie.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\21\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=26512, ...}) = 0
mmap(NULL, 2121744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0d9f000
mprotect(0x7fcec0da5000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0fa4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x5000) = 0x7fcec0fa4000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXau.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14456, ...}) = 0
mmap(NULL, 2109720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0b9b000
mprotect(0x7fcec0b9d000, 2097152, PROT_NONE) = 0
mmap(0x7fcec0d9d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec0d9d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdmcp.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\22\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=22592, ...}) = 0
mmap(NULL, 2117800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0995000
mprotect(0x7fcec099a000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0b99000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4000) = 0x7fcec0b99000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libuuid.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\25\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=18920, ...}) = 0
mmap(NULL, 2113920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0790000
mprotect(0x7fcec0794000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0993000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3000) = 0x7fcec0993000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgpg-error.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320&\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=76328, ...}) = 0
mmap(NULL, 2171440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec057d000
mprotect(0x7fcec058f000, 2093056, PROT_NONE) = 0
mmap(0x7fcec078e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x11000) = 0x7fcec078e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgraphite2.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20$\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=112968, ...}) = 0
mmap(NULL, 2208112, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0361000
mprotect(0x7fcec037b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec057a000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x19000) = 0x7fcec057a000
close(4)                                = 0
mprotect(0x7fcec057a000, 8192, PROT_READ) = 0
mprotect(0x7fcec078e000, 4096, PROT_READ) = 0
mprotect(0x7fcec0993000, 4096, PROT_READ) = 0
mprotect(0x7fcec0b99000, 4096, PROT_READ) = 0
mprotect(0x7fcec0d9d000, 4096, PROT_READ) = 0
mprotect(0x7fcec0fa4000, 4096, PROT_READ) = 0
mprotect(0x7fcec4575000, 4096, PROT_READ) = 0
mprotect(0x7fcec435b000, 4096, PROT_READ) = 0
mprotect(0x7fcec832b000, 24576, PROT_READ) = 0
mprotect(0x7fcec3d04000, 4096, PROT_READ) = 0
mprotect(0x7fcec6a68000, 4096, PROT_READ) = 0
mprotect(0x7fcec1202000, 4096, PROT_READ) = 0
mprotect(0x7fcec14dc000, 4096, PROT_READ) = 0
mprotect(0x7fcec1706000, 4096, PROT_READ) = 0
mprotect(0x7fcec191d000, 4096, PROT_READ) = 0
mprotect(0x7fcec1b28000, 4096, PROT_READ) = 0
mprotect(0x7fcec1d2a000, 4096, PROT_READ) = 0
mprotect(0x7fcec2151000, 4096, PROT_READ) = 0
mprotect(0x7fcec1f30000, 4096, PROT_READ) = 0
mprotect(0x7fcec235b000, 4096, PROT_READ) = 0
mprotect(0x7fcec255f000, 4096, PROT_READ) = 0
mprotect(0x7fcec2805000, 32768, PROT_READ) = 0
mprotect(0x7fcec2a15000, 4096, PROT_READ) = 0
mprotect(0x7fcec4d17000, 4096, PROT_READ) = 0
mprotect(0x7fcec7e4c000, 4096, PROT_READ) = 0
mprotect(0x7fcec782d000, 4096, PROT_READ) = 0
mprotect(0x7fcec2c1f000, 4096, PROT_READ) = 0
mprotect(0x7fcec7c42000, 4096, PROT_READ) = 0
mprotect(0x7fcec2e2a000, 4096, PROT_READ) = 0
mprotect(0x7fcec303a000, 4096, PROT_READ) = 0
mprotect(0x7fcec323d000, 4096, PROT_READ) = 0
mprotect(0x7fcec3456000, 8192, PROT_READ) = 0
mprotect(0x7fcec367b000, 4096, PROT_READ) = 0
mprotect(0x7fcec4134000, 8192, PROT_READ) = 0
mprotect(0x7fcec8089000, 8192, PROT_READ) = 0
mprotect(0x7fcec3f0c000, 4096, PROT_READ) = 0
mprotect(0x7fcec6cbc000, 4096, PROT_READ) = 0
mprotect(0x7fcec3a97000, 4096, PROT_READ) = 0
mprotect(0x7fcec56a5000, 8192, PROT_READ) = 0
mprotect(0x7fcec3893000, 4096, PROT_READ) = 0
mprotect(0x7fcecfa80000, 12288, PROT_READ) = 0
mprotect(0x7fcec4777000, 4096, PROT_READ) = 0
mprotect(0x7fcec49db000, 4096, PROT_READ) = 0
mprotect(0x7fcec4f23000, 4096, PROT_READ) = 0
mprotect(0x7fcec5ee3000, 16384, PROT_READ) = 0
mprotect(0x7fcec5145000, 4096, PROT_READ) = 0
mprotect(0x7fcec5454000, 12288, PROT_READ) = 0
mprotect(0x7fcec58b3000, 4096, PROT_READ) = 0
mprotect(0x7fcec7a30000, 4096, PROT_READ) = 0
mprotect(0x7fcec7627000, 4096, PROT_READ) = 0
mprotect(0x7fcec5b64000, 16384, PROT_READ) = 0
mprotect(0x7fcec610c000, 12288, PROT_READ) = 0
mprotect(0x7fcec674e000, 28672, PROT_READ) = 0
mprotect(0x7fcec6f08000, 4096, PROT_READ) = 0
mprotect(0x7fcec712f000, 4096, PROT_READ) = 0
mprotect(0x7fcec741e000, 28672, PROT_READ) = 0
mprotect(0x7fcecc924000, 4882432, PROT_READ) = 0
statfs("/sys/fs/selinux", 0x7ffcfb2eee10) = -1 ENOENT (No such file or directory)
statfs("/selinux", 0x7ffcfb2eee10)      = -1 ENOENT (No such file or directory)
open("/proc/filesystems", O_RDONLY)     = 4
fstat(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfad6000
read(4, "nodev\tsysfs\nnodev\trootfs\nnodev\tr"..., 1024) = 419
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0x7fcecfad6000, 4096)            = 0
futex(0x7fcec6a6a428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fcec6a6a428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
prctl(PR_SET_SECCOMP, 0x2, 0, 0x46, 0x1000) = -1 EFAULT (Bad address)
syscall_317(0x1, 0x1, 0, 0x2000, 0x7fcece61b000, 0x7fcecc9241e8) = -1 (errno 14)
access("/proc/self/ns/user", F_OK)      = 0
access("/proc/self/ns/pid", F_OK)       = 0
access("/proc/self/ns/net", F_OK)       = 0
access("/proc/self/ns/ipc", F_OK)       = 0
unshare(0)                              = 0
clone(child_stack=0, flags=CLONE_NEWUSER|SIGCHLD) = 21221
wait4(21221, NULL, 0, NULL)             = 21221
--- SIGCHLD {si_signo=SIGCHLD, si_code=CLD_EXITED, si_pid=21221, si_status=0, si_utime=0, si_stime=0} ---
futex(0x7fcecf49226c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fcecf492278, FUTEX_WAKE_PRIVATE, 2147483647) = 0
munmap(0x7fcecfa84000, 156356)          = 0
gettid()                                = 21219
rt_sigaction(SIGPIPE, {SIG_IGN, [], SA_RESTORER, 0x7fcecf6a9d10}, NULL, 8) = 0
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fcecfad7000, 4096)            = 0
getrusage(RUSAGE_SELF, {ru_utime={0, 20000}, ru_stime={0, 8000}, ...}) = 0
lstat("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
lstat("/usr/lib/firefox", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
stat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2919792, ...}) = 0
mmap(NULL, 2919792, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fcec0098000
close(3)                                = 0
open("/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26258, ...}) = 0
mmap(NULL, 26258, PROT_READ, MAP_SHARED, 3, 0) = 0x7fcecfad1000
close(3)                                = 0
futex(0x7fcecebefa10, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/x86_64-linux-gnu/gconv/UTF-16.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\7\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=17944, ...}) = 0
mmap(NULL, 2109544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcebfe94000
mprotect(0x7fcebfe95000, 2101248, PROT_NONE) = 0
mprotect(0x7fcebfe94000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC) = 0
mprotect(0x7fcebfe94000, 4096, PROT_READ|PROT_EXEC) = 0
mmap(0x7fcebfe95000, 4604, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcebfe95000
mmap(0x7fcec0096000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fcec0096000
mmap(0x7fcec0097000, 104, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec0097000
close(3)                                = 0
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x8} ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)

This is a partial stack trace on kdbg:

mmap(NULL, 3220704, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec5147000
mprotect(0x7fcec5255000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5454000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x10d000) = 0x7fcec5454000
mmap(0x7fcec5458000, 5344, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec5458000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220a\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=138640, ...}) = 0
mmap(NULL, 2234080, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4f25000
mprotect(0x7fcec4f46000, 2093056, PROT_NONE) = 0
mmap(0x7fcec5145000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec5145000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libstartup-notification-1.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000,\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=35136, ...}) = 0
mmap(NULL, 2130712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4d1c000
mprotect(0x7fcec4d24000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4f23000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7000) = 0x7fcec4f23000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\210\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=1285552, ...}) = 0
mmap(NULL, 3382584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec49e2000
mprotect(0x7fcec4b17000, 2097152, PROT_NONE) = 0
mmap(0x7fcec4d17000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x135000) = 0x7fcec4d17000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXt.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2601\1\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=426320, ...}) = 0
mmap(NULL, 2524896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4779000
mprotect(0x7fcec47db000, 2097152, PROT_NONE) = 0
mmap(0x7fcec49db000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x62000) = 0x7fcec49db000
mmap(0x7fcec49e1000, 1760, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec49e1000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgthread-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\6\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=6112, ...}) = 0
mmap(NULL, 2101320, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4577000
mprotect(0x7fcec4578000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4777000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0x7fcec4777000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\35\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=104824, ...}) = 0
mmap(NULL, 2199880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec435d000
mprotect(0x7fcec4376000, 2093056, PROT_NONE) = 0
mmap(0x7fcec4575000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x18000) = 0x7fcec4575000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpng12.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0;\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=153944, ...}) = 0
mmap(NULL, 2249104, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec4137000
mprotect(0x7fcec415c000, 2093056, PROT_NONE) = 0
mmap(0x7fcec435b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x24000) = 0x7fcec435b000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libexpat.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220;\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=166000, ...}) = 0
mmap(NULL, 2261128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3f0e000
mprotect(0x7fcec3f34000, 2097152, PROT_NONE) = 0
mmap(0x7fcec4134000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x26000) = 0x7fcec4134000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libsystemd.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=524024, ...}) = 0
mmap(NULL, 528356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcecfa03000
mmap(0x7fcecfa80000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7c000) = 0x7fcecfa80000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\27\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=31016, ...}) = 0
mmap(NULL, 2127464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3d06000
mprotect(0x7fcec3d0d000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3f0c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6000) = 0x7fcec3f0c000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\26\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=444344, ...}) = 0
mmap(NULL, 2539784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3a99000
mprotect(0x7fcec3b05000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3d04000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6b000) = 0x7fcec3d04000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\21\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14624, ...}) = 0
mmap(NULL, 2109880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec3895000
mprotect(0x7fcec3898000, 2093056, PROT_NONE) = 0
mmap(0x7fcec3a97000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec3a97000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320s\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=90184, ...}) = 0
mmap(NULL, 2185760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec367f000
mprotect(0x7fcec3693000, 2097152, PROT_NONE) = 0
mmap(0x7fcec3893000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x14000) = 0x7fcec3893000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300[\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=138400, ...}) = 0
mmap(NULL, 2242312, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec345b000
mprotect(0x7fcec347c000, 2093056, PROT_NONE) = 0
mmap(0x7fcec367b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec367b000
mmap(0x7fcec367d000, 5896, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec367d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\3209\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=105328, ...}) = 0
mmap(NULL, 2210632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec323f000
mprotect(0x7fcec3256000, 2097152, PROT_NONE) = 0
mmap(0x7fcec3456000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x17000) = 0x7fcec3456000
mmap(0x7fcec3459000, 6984, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec3459000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXinerama.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\n\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=10376, ...}) = 0
mmap(NULL, 2105640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec303c000
mprotect(0x7fcec303e000, 2093056, PROT_NONE) = 0
mmap(0x7fcec323d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1000) = 0x7fcec323d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXi.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340!\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=63912, ...}) = 0
mmap(NULL, 2159368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2e2c000
mprotect(0x7fcec2e3b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec303a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xe000) = 0x7fcec303a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrandr.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\34\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=43288, ...}) = 0
mmap(NULL, 2138536, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2c21000
mprotect(0x7fcec2c2b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2e2a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x9000) = 0x7fcec2e2a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXcursor.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 $\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39232, ...}) = 0
mmap(NULL, 2134496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2a17000
mprotect(0x7fcec2a20000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2c1f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7fcec2c1f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libthai.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\33\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=36936, ...}) = 0
mmap(NULL, 2132200, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec280e000
mprotect(0x7fcec2816000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2a15000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x7000) = 0x7fcec2a15000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libpixman-1.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\231\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=706576, ...}) = 0
mmap(NULL, 2802008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2561000
mprotect(0x7fcec2606000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2805000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa4000) = 0x7fcec2805000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-shm.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\r\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14432, ...}) = 0
mmap(NULL, 2109560, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec235d000
mprotect(0x7fcec235f000, 2097152, PROT_NONE) = 0
mmap(0x7fcec255f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec255f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-render.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2404\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39008, ...}) = 0
mmap(NULL, 2134136, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec2153000
mprotect(0x7fcec215b000, 2097152, PROT_NONE) = 0
mmap(0x7fcec235b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7fcec235b000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \226\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=133584, ...}) = 0
mmap(NULL, 2228904, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1f32000
mprotect(0x7fcec1f52000, 2093056, PROT_NONE) = 0
mmap(0x7fcec2151000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1f000) = 0x7fcec2151000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb-util.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`%\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=22744, ...}) = 0
mmap(NULL, 2117896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1d2c000
mprotect(0x7fcec1d31000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1f30000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4000) = 0x7fcec1f30000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11-xcb.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\5\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=5992, ...}) = 0
mmap(NULL, 2101304, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1b2a000
mprotect(0x7fcec1b2b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1d2a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0) = 0x7fcec1d2a000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libSM.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\33\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=30960, ...}) = 0
mmap(NULL, 2126192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1922000
mprotect(0x7fcec1929000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1b28000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x6000) = 0x7fcec1b28000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libICE.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260F\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=93824, ...}) = 0
mmap(NULL, 2203520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1708000
mprotect(0x7fcec171e000, 2093056, PROT_NONE) = 0
mmap(0x7fcec191d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x15000) = 0x7fcec191d000
mmap(0x7fcec191f000, 12160, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec191f000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320 \0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=137400, ...}) = 0
mmap(NULL, 2232456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec14e6000
mprotect(0x7fcec1507000, 2093056, PROT_NONE) = 0
mmap(0x7fcec1706000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x20000) = 0x7fcec1706000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcrypt.so.20", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\216\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=924096, ...}) = 0
mmap(NULL, 3020448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec1204000
mprotect(0x7fcec12dc000, 2097152, PROT_NONE) = 0
mmap(0x7fcec14dc000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xd8000) = 0x7fcec14dc000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libharfbuzz.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240f\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=383920, ...}) = 0
mmap(NULL, 2480208, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0fa6000
mprotect(0x7fcec1002000, 2097152, PROT_NONE) = 0
mmap(0x7fcec1202000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x5c000) = 0x7fcec1202000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libdatrie.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\21\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=26512, ...}) = 0
mmap(NULL, 2121744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0d9f000
mprotect(0x7fcec0da5000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0fa4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x5000) = 0x7fcec0fa4000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXau.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=14456, ...}) = 0
mmap(NULL, 2109720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0b9b000
mprotect(0x7fcec0b9d000, 2097152, PROT_NONE) = 0
mmap(0x7fcec0d9d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x2000) = 0x7fcec0d9d000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdmcp.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\22\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=22592, ...}) = 0
mmap(NULL, 2117800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0995000
mprotect(0x7fcec099a000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0b99000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4000) = 0x7fcec0b99000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libuuid.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\25\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=18920, ...}) = 0
mmap(NULL, 2113920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0790000
mprotect(0x7fcec0794000, 2093056, PROT_NONE) = 0
mmap(0x7fcec0993000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3000) = 0x7fcec0993000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgpg-error.so.0", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320&\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=76328, ...}) = 0
mmap(NULL, 2171440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec057d000
mprotect(0x7fcec058f000, 2093056, PROT_NONE) = 0
mmap(0x7fcec078e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x11000) = 0x7fcec078e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgraphite2.so.3", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20$\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=112968, ...}) = 0
mmap(NULL, 2208112, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7fcec0361000
mprotect(0x7fcec037b000, 2093056, PROT_NONE) = 0
mmap(0x7fcec057a000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x19000) = 0x7fcec057a000
close(4)                                = 0
mprotect(0x7fcec057a000, 8192, PROT_READ) = 0
mprotect(0x7fcec078e000, 4096, PROT_READ) = 0
mprotect(0x7fcec0993000, 4096, PROT_READ) = 0
mprotect(0x7fcec0b99000, 4096, PROT_READ) = 0
mprotect(0x7fcec0d9d000, 4096, PROT_READ) = 0
mprotect(0x7fcec0fa4000, 4096, PROT_READ) = 0
mprotect(0x7fcec4575000, 4096, PROT_READ) = 0
mprotect(0x7fcec435b000, 4096, PROT_READ) = 0
mprotect(0x7fcec832b000, 24576, PROT_READ) = 0
mprotect(0x7fcec3d04000, 4096, PROT_READ) = 0
mprotect(0x7fcec6a68000, 4096, PROT_READ) = 0
mprotect(0x7fcec1202000, 4096, PROT_READ) = 0
mprotect(0x7fcec14dc000, 4096, PROT_READ) = 0
mprotect(0x7fcec1706000, 4096, PROT_READ) = 0
mprotect(0x7fcec191d000, 4096, PROT_READ) = 0
mprotect(0x7fcec1b28000, 4096, PROT_READ) = 0
mprotect(0x7fcec1d2a000, 4096, PROT_READ) = 0
mprotect(0x7fcec2151000, 4096, PROT_READ) = 0
mprotect(0x7fcec1f30000, 4096, PROT_READ) = 0
mprotect(0x7fcec235b000, 4096, PROT_READ) = 0
mprotect(0x7fcec255f000, 4096, PROT_READ) = 0
mprotect(0x7fcec2805000, 32768, PROT_READ) = 0
mprotect(0x7fcec2a15000, 4096, PROT_READ) = 0
mprotect(0x7fcec4d17000, 4096, PROT_READ) = 0
mprotect(0x7fcec7e4c000, 4096, PROT_READ) = 0
mprotect(0x7fcec782d000, 4096, PROT_READ) = 0
mprotect(0x7fcec2c1f000, 4096, PROT_READ) = 0
mprotect(0x7fcec7c42000, 4096, PROT_READ) = 0
mprotect(0x7fcec2e2a000, 4096, PROT_READ) = 0
mprotect(0x7fcec303a000, 4096, PROT_READ) = 0
mprotect(0x7fcec323d000, 4096, PROT_READ) = 0
mprotect(0x7fcec3456000, 8192, PROT_READ) = 0
mprotect(0x7fcec367b000, 4096, PROT_READ) = 0
mprotect(0x7fcec4134000, 8192, PROT_READ) = 0
mprotect(0x7fcec8089000, 8192, PROT_READ) = 0
mprotect(0x7fcec3f0c000, 4096, PROT_READ) = 0
mprotect(0x7fcec6cbc000, 4096, PROT_READ) = 0
mprotect(0x7fcec3a97000, 4096, PROT_READ) = 0
mprotect(0x7fcec56a5000, 8192, PROT_READ) = 0
mprotect(0x7fcec3893000, 4096, PROT_READ) = 0
mprotect(0x7fcecfa80000, 12288, PROT_READ) = 0
mprotect(0x7fcec4777000, 4096, PROT_READ) = 0
mprotect(0x7fcec49db000, 4096, PROT_READ) = 0
mprotect(0x7fcec4f23000, 4096, PROT_READ) = 0
mprotect(0x7fcec5ee3000, 16384, PROT_READ) = 0
mprotect(0x7fcec5145000, 4096, PROT_READ) = 0
mprotect(0x7fcec5454000, 12288, PROT_READ) = 0
mprotect(0x7fcec58b3000, 4096, PROT_READ) = 0
mprotect(0x7fcec7a30000, 4096, PROT_READ) = 0
mprotect(0x7fcec7627000, 4096, PROT_READ) = 0
mprotect(0x7fcec5b64000, 16384, PROT_READ) = 0
mprotect(0x7fcec610c000, 12288, PROT_READ) = 0
mprotect(0x7fcec674e000, 28672, PROT_READ) = 0
mprotect(0x7fcec6f08000, 4096, PROT_READ) = 0
mprotect(0x7fcec712f000, 4096, PROT_READ) = 0
mprotect(0x7fcec741e000, 28672, PROT_READ) = 0
mprotect(0x7fcecc924000, 4882432, PROT_READ) = 0
statfs("/sys/fs/selinux", 0x7ffcfb2eee10) = -1 ENOENT (No such file or directory)
statfs("/selinux", 0x7ffcfb2eee10)      = -1 ENOENT (No such file or directory)
open("/proc/filesystems", O_RDONLY)     = 4
fstat(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fcecfad6000
read(4, "nodev\tsysfs\nnodev\trootfs\nnodev\tr"..., 1024) = 419
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0x7fcecfad6000, 4096)            = 0
futex(0x7fcec6a6a428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fcec6a6a428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
prctl(PR_SET_SECCOMP, 0x2, 0, 0x46, 0x1000) = -1 EFAULT (Bad address)
syscall_317(0x1, 0x1, 0, 0x2000, 0x7fcece61b000, 0x7fcecc9241e8) = -1 (errno 14)
access("/proc/self/ns/user", F_OK)      = 0
access("/proc/self/ns/pid", F_OK)       = 0
access("/proc/self/ns/net", F_OK)       = 0
access("/proc/self/ns/ipc", F_OK)       = 0
unshare(0)                              = 0
clone(child_stack=0, flags=CLONE_NEWUSER|SIGCHLD) = 21221
wait4(21221, NULL, 0, NULL)             = 21221
--- SIGCHLD {si_signo=SIGCHLD, si_code=CLD_EXITED, si_pid=21221, si_status=0, si_utime=0, si_stime=0} ---
futex(0x7fcecf49226c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fcecf492278, FUTEX_WAKE_PRIVATE, 2147483647) = 0
munmap(0x7fcecfa84000, 156356)          = 0
gettid()                                = 21219
rt_sigaction(SIGPIPE, {SIG_IGN, [], SA_RESTORER, 0x7fcecf6a9d10}, NULL, 8) = 0
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0x7fcecfad7000, 4096)            = 0
getrusage(RUSAGE_SELF, {ru_utime={0, 20000}, ru_stime={0, 8000}, ...}) = 0
lstat("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib", {st_mode=S_IFDIR|0755, st_size=20480, ...}) = 0
lstat("/usr/lib/firefox", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
stat("/usr/lib/firefox/firefox", {st_mode=S_IFREG|0755, st_size=121056, ...}) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2919792, ...}) = 0
mmap(NULL, 2919792, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fcec0098000
close(3)                                = 0
open("/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26258, ...}) = 0
mmap(NULL, 26258, PROT_READ, MAP_SHARED, 3, 0) = 0x7fcecfad1000
close(3)                                = 0
futex(0x7fcecebefa10, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/x86_64-linux-gnu/gconv/UTF-16.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\7\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=17944, ...}) = 0
mmap(NULL, 2109544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fcebfe94000
mprotect(0x7fcebfe95000, 2101248, PROT_NONE) = 0
mprotect(0x7fcebfe94000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC) = 0
mprotect(0x7fcebfe94000, 4096, PROT_READ|PROT_EXEC) = 0
mmap(0x7fcebfe95000, 4604, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcebfe95000
mmap(0x7fcec0096000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fcec0096000
mmap(0x7fcec0097000, 104, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fcec0097000
close(3)                                = 0
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x8} ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)
arlen@Dumbledore:~/Development/FreePascal/lazarus$  strace kdbg | tee kdbg.txt
No command ' strace' found, did you mean:
 Command 'fstrace' from package 'openafs-client' (universe)
 Command 'strace' from package 'strace' (main)
 strace: command not found
arlen@Dumbledore:~/Development/FreePascal/lazarus$ strace kdbg | tee kdbg.txt  
execve("/usr/bin/kdbg", ["kdbg"], [/* 54 vars */]) = 0
brk(0)                                  = 0xcbc000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43dab1000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=156356, ...}) = 0
mmap(NULL, 156356, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd43da8a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkdecore.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000*\t\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=3026472, ...}) = 0
mmap(NULL, 5123936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43d3ad000
mprotect(0x7fd43d67c000, 2097152, PROT_NONE) = 0
mmap(0x7fd43d87c000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2cf000) = 0x7fd43d87c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkio.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\221\n\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=2919936, ...}) = 0
mmap(NULL, 5017568, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43cee4000
mprotect(0x7fd43d198000, 2093056, PROT_NONE) = 0
mmap(0x7fd43d397000, 90112, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2b3000) = 0x7fd43d397000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libutil.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10608, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da89000
mmap(NULL, 2105624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43cce1000
mprotect(0x7fd43cce3000, 2093056, PROT_NONE) = 0
mmap(0x7fd43cee2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7fd43cee2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libkdeui.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240 \24\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=4689656, ...}) = 0
mmap(NULL, 6792552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43c666000
mprotect(0x7fd43cab3000, 2093056, PROT_NONE) = 0
mmap(0x7fd43ccb2000, 184320, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x44c000) = 0x7fd43ccb2000
mmap(0x7fd43ccdf000, 5480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43ccdf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtCore.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\36\7\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=3086416, ...}) = 0
mmap(NULL, 5184712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43c174000
mprotect(0x7fd43c45b000, 2093056, PROT_NONE) = 0
mmap(0x7fd43c65a000, 45056, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2e6000) = 0x7fd43c65a000
mmap(0x7fd43c665000, 3272, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43c665000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtGui.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\36\33\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=11458432, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da88000
mmap(NULL, 13566752, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43b483000
mprotect(0x7fd43bf2c000, 2093056, PROT_NONE) = 0
mmap(0x7fd43c12b000, 282624, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xaa8000) = 0x7fd43c12b000
mmap(0x7fd43c170000, 13088, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43c170000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libstdc++.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \240\10\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1566568, ...}) = 0
mmap(NULL, 3675328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43b101000
mprotect(0x7fd43b274000, 2093056, PROT_NONE) = 0
mmap(0x7fd43b473000, 49152, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x172000) = 0x7fd43b473000
mmap(0x7fd43b47f000, 13504, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43b47f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\v\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1869392, ...}) = 0
mmap(NULL, 3972864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43ad37000
mprotect(0x7fd43aef7000, 2097152, PROT_NONE) = 0
mmap(0x7fd43b0f7000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c0000) = 0x7fd43b0f7000
mmap(0x7fd43b0fd000, 16128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43b0fd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtNetwork.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@ \3\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1391328, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da87000
mmap(NULL, 3488128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43a9e3000
mprotect(0x7fd43ab30000, 2093056, PROT_NONE) = 0
mmap(0x7fd43ad2f000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14c000) = 0x7fd43ad2f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtDBus.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260<\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=537736, ...}) = 0
mmap(NULL, 2633352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43a760000
mprotect(0x7fd43a7e1000, 2097152, PROT_NONE) = 0
mmap(0x7fd43a9e1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x81000) = 0x7fd43a9e1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360\35\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=104824, ...}) = 0
mmap(NULL, 2199880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43a546000
mprotect(0x7fd43a55f000, 2093056, PROT_NONE) = 0
mmap(0x7fd43a75e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0x7fd43a75e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libbz2.so.1.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\23\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=66800, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da86000
mmap(NULL, 2161928, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43a336000
mprotect(0x7fd43a345000, 2093056, PROT_NONE) = 0
mmap(0x7fd43a544000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0x7fd43a544000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/liblzma.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320 \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=137400, ...}) = 0
mmap(NULL, 2232456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43a114000
mprotect(0x7fd43a135000, 2093056, PROT_NONE) = 0
mmap(0x7fd43a334000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x20000) = 0x7fd43a334000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340`\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=142080, ...}) = 0
mmap(NULL, 2217232, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd439ef6000
mprotect(0x7fd439f0e000, 2097152, PROT_NONE) = 0
mmap(0x7fd43a10e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0x7fd43a10e000
mmap(0x7fd43a110000, 13584, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43a110000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdlrestrictions.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\20\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18704, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da85000
mmap(NULL, 2114888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd439cf1000
mprotect(0x7fd439cf4000, 2097152, PROT_NONE) = 0
mmap(0x7fd439ef4000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7fd439ef4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240U\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1084840, ...}) = 0
mmap(NULL, 3174760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4399e9000
mprotect(0x7fd439af0000, 2093056, PROT_NONE) = 0
mmap(0x7fd439cef000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x106000) = 0x7fd439cef000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcc_s.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360*\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=92504, ...}) = 0
mmap(NULL, 2188352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4397d2000
mprotect(0x7fd4397e8000, 2093056, PROT_NONE) = 0
mmap(0x7fd4399e7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7fd4399e7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtXml.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \374\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=285720, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da84000
mmap(NULL, 2380776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43958c000
mprotect(0x7fd4395cf000, 2097152, PROT_NONE) = 0
mmap(0x7fd4397cf000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x43000) = 0x7fd4397cf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libQtSvg.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000/\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=365864, ...}) = 0
mmap(NULL, 2460912, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd439333000
mprotect(0x7fd439389000, 2097152, PROT_NONE) = 0
mmap(0x7fd439589000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x56000) = 0x7fd439589000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libX11.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\210\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1285552, ...}) = 0
mmap(NULL, 3382584, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438ff9000
mprotect(0x7fd43912e000, 2097152, PROT_NONE) = 0
mmap(0x7fd43932e000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x135000) = 0x7fd43932e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstreamanalyzer.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2008\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=503560, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da83000
mmap(NULL, 2606664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438d7c000
mprotect(0x7fd438df4000, 2097152, PROT_NONE) = 0
mmap(0x7fd438ff4000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x78000) = 0x7fd438ff4000
mmap(0x7fd438ff7000, 5704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd438ff7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libsolid.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\211\3\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1082880, ...}) = 0
mmap(NULL, 3178664, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438a73000
mprotect(0x7fd438b68000, 2097152, PROT_NONE) = 0
mmap(0x7fd438d68000, 77824, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf5000) = 0x7fd438d68000
mmap(0x7fd438d7b000, 168, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd438d7b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libacl.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\34\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=35264, ...}) = 0
mmap(NULL, 2130432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43886a000
mprotect(0x7fd438871000, 2097152, PROT_NONE) = 0
mmap(0x7fd438a71000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7fd438a71000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libattr.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\20\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18624, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da82000
mmap(NULL, 2113760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438665000
mprotect(0x7fd438669000, 2093056, PROT_NONE) = 0
mmap(0x7fd438868000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7fd438868000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXrender.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\32\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=39416, ...}) = 0
mmap(NULL, 2134696, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43845b000
mprotect(0x7fd438464000, 2093056, PROT_NONE) = 0
mmap(0x7fd438663000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7fd438663000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libSM.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\33\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=30960, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da81000
mmap(NULL, 2126192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438253000
mprotect(0x7fd43825a000, 2093056, PROT_NONE) = 0
mmap(0x7fd438459000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fd438459000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libICE.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260F\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=93824, ...}) = 0
mmap(NULL, 2203520, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd438039000
mprotect(0x7fd43804f000, 2093056, PROT_NONE) = 0
mmap(0x7fd43824e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15000) = 0x7fd43824e000
mmap(0x7fd438250000, 12160, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd438250000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libattica.so.0.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360~\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=773792, ...}) = 0
mmap(NULL, 2868840, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd437d7c000
mprotect(0x7fd437e34000, 2097152, PROT_NONE) = 0
mmap(0x7fd438034000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xb8000) = 0x7fd438034000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libdbusmenu-qt.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\202\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=196536, ...}) = 0
mmap(NULL, 2291624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd437b4c000
mprotect(0x7fd437b7a000, 2093056, PROT_NONE) = 0
mmap(0x7fd437d79000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2d000) = 0x7fd437d79000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXfixes.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22584, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da80000
mmap(NULL, 2117896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd437946000
mprotect(0x7fd43794b000, 2093056, PROT_NONE) = 0
mmap(0x7fd437b4a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7fd437b4a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14592, ...}) = 0
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd437742000
mprotect(0x7fd437745000, 2093056, PROT_NONE) = 0
mmap(0x7fd437944000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fd437944000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libglib-2.0.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\250\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1106880, ...}) = 0
mmap(NULL, 3204456, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd437433000
mprotect(0x7fd437540000, 2093056, PROT_NONE) = 0
mmap(0x7fd43773f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10c000) = 0x7fd43773f000
mmap(0x7fd437741000, 1384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd437741000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da7f000
open("/lib/x86_64-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31680, ...}) = 0
mmap(NULL, 2128864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43722b000
mprotect(0x7fd437232000, 2093056, PROT_NONE) = 0
mmap(0x7fd437431000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fd437431000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfontconfig.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240l\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=252896, ...}) = 0
mmap(NULL, 2348744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436fed000
mprotect(0x7fd437029000, 2093056, PROT_NONE) = 0
mmap(0x7fd437228000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3b000) = 0x7fd437228000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libaudio.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0N\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=100920, ...}) = 0
mmap(NULL, 2196680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436dd4000
mprotect(0x7fd436dec000, 2093056, PROT_NONE) = 0
mmap(0x7fd436feb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7fd436feb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpng12.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0;\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=153944, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da7e000
mmap(NULL, 2249104, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436bae000
mprotect(0x7fd436bd3000, 2093056, PROT_NONE) = 0
mmap(0x7fd436dd2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24000) = 0x7fd436dd2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libfreetype.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\273\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=678368, ...}) = 0
mmap(NULL, 2773496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436908000
mprotect(0x7fd4369a8000, 2093056, PROT_NONE) = 0
mmap(0x7fd436ba7000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9f000) = 0x7fd436ba7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\257\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=338984, ...}) = 0
mmap(NULL, 2436872, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4366b5000
mprotect(0x7fd436707000, 2093056, PROT_NONE) = 0
mmap(0x7fd436906000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x51000) = 0x7fd436906000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340!\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=63912, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da7d000
mmap(NULL, 2159368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4364a5000
mprotect(0x7fd4364b4000, 2093056, PROT_NONE) = 0
mmap(0x7fd4366b3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xe000) = 0x7fd4366b3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXext.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2205\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=73640, ...}) = 0
mmap(NULL, 2169496, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436293000
mprotect(0x7fd4362a4000, 2093056, PROT_NONE) = 0
mmap(0x7fd4364a3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10000) = 0x7fd4364a3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdbus-1.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\250\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=309392, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da7c000
mmap(NULL, 2405040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd436047000
mprotect(0x7fd436091000, 2097152, PROT_NONE) = 0
mmap(0x7fd436291000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4a000) = 0x7fd436291000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxcb.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \226\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=133584, ...}) = 0
mmap(NULL, 2228904, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd435e26000
mprotect(0x7fd435e46000, 2093056, PROT_NONE) = 0
mmap(0x7fd436045000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f000) = 0x7fd436045000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstreams.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000\304\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=228416, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da7b000
mmap(NULL, 2324096, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd435bee000
mprotect(0x7fd435c24000, 2097152, PROT_NONE) = 0
mmap(0x7fd435e24000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x36000) = 0x7fd435e24000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libxml2.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\331\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1797368, ...}) = 0
mmap(NULL, 3897784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd435836000
mprotect(0x7fd4359e3000, 2097152, PROT_NONE) = 0
mmap(0x7fd435be3000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1ad000) = 0x7fd435be3000
mmap(0x7fd435bed000, 2488, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd435bed000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libudev.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=122624, ...}) = 0
mmap(NULL, 126432, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43da5c000
mmap(0x7fd43da79000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1c000) = 0x7fd43da79000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da5b000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libuuid.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=18920, ...}) = 0
mmap(NULL, 2113920, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd435631000
mprotect(0x7fd435635000, 2093056, PROT_NONE) = 0
mmap(0x7fd435834000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3000) = 0x7fd435834000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\26\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=444344, ...}) = 0
mmap(NULL, 2539784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4353c4000
mprotect(0x7fd435430000, 2093056, PROT_NONE) = 0
mmap(0x7fd43562f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6b000) = 0x7fd43562f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libexpat.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220;\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=166000, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da5a000
mmap(NULL, 2261128, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43519b000
mprotect(0x7fd4351c1000, 2097152, PROT_NONE) = 0
mmap(0x7fd4353c1000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x26000) = 0x7fd4353c1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXt.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\2601\1\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=426320, ...}) = 0
mmap(NULL, 2524896, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd434f32000
mprotect(0x7fd434f94000, 2097152, PROT_NONE) = 0
mmap(0x7fd435194000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x62000) = 0x7fd435194000
mmap(0x7fd43519a000, 1760, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43519a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXau.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14456, ...}) = 0
mmap(NULL, 2109720, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd434d2e000
mprotect(0x7fd434d30000, 2097152, PROT_NONE) = 0
mmap(0x7fd434f30000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fd434f30000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43da59000
open("/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\27\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31016, ...}) = 0
mmap(NULL, 2127464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd434b26000
mprotect(0x7fd434b2d000, 2093056, PROT_NONE) = 0
mmap(0x7fd434d2c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7fd434d2c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libsystemd.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\0\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=524024, ...}) = 0
mmap(NULL, 528356, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43d9d8000
mmap(0x7fd43da55000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7c000) = 0x7fd43da55000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libXdmcp.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\22\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=22592, ...}) = 0
mmap(NULL, 2117800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd434920000
mprotect(0x7fd434925000, 2093056, PROT_NONE) = 0
mmap(0x7fd434b24000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0x7fd434b24000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d7000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libicuuc.so.55", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320V\5\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1636360, ...}) = 0
mmap(NULL, 3750688, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd43458c000
mprotect(0x7fd43470b000, 2097152, PROT_NONE) = 0
mmap(0x7fd43490b000, 69632, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17f000) = 0x7fd43490b000
mmap(0x7fd43491c000, 15136, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd43491c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgcrypt.so.20", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0\216\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=924096, ...}) = 0
mmap(NULL, 3020448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4342aa000
mprotect(0x7fd434382000, 2097152, PROT_NONE) = 0
mmap(0x7fd434582000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd8000) = 0x7fd434582000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libicudata.so.55", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p\5\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=25913104, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d6000
mmap(NULL, 28008464, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4327f3000
mprotect(0x7fd4340a9000, 2093056, PROT_NONE) = 0
mmap(0x7fd4342a8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18b5000) = 0x7fd4342a8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libgpg-error.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320&\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=76328, ...}) = 0
mmap(NULL, 2171440, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd4325e0000
mprotect(0x7fd4325f2000, 2093056, PROT_NONE) = 0
mmap(0x7fd4327f1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11000) = 0x7fd4327f1000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d5000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d4000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d3000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d2000
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9d1000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9cf000
arch_prctl(ARCH_SET_FS, 0x7fd43d9cf840) = 0
mprotect(0x7fd43b0f7000, 16384, PROT_READ) = 0
mprotect(0x7fd4327f1000, 4096, PROT_READ) = 0
mprotect(0x7fd4342a8000, 4096, PROT_READ) = 0
mprotect(0x7fd434582000, 4096, PROT_READ) = 0
mprotect(0x7fd439cef000, 4096, PROT_READ) = 0
mprotect(0x7fd4399e7000, 4096, PROT_READ) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7fd43d9ce000
mprotect(0x7fd43b473000, 40960, PROT_READ) = 0
mprotect(0x7fd437944000, 4096, PROT_READ) = 0
mprotect(0x7fd43490b000, 65536, PROT_READ) = 0
mprotect(0x7fd434b24000, 4096, PROT_READ) = 0
mprotect(0x7fd43a334000, 4096, PROT_READ) = 0
mprotect(0x7fd43a10e000, 4096, PROT_READ) = 0
mprotect(0x7fd437431000, 4096, PROT_READ) = 0
mprotect(0x7fd43da55000, 12288, PROT_READ) = 0
mprotect(0x7fd434d2c000, 4096, PROT_READ) = 0
mprotect(0x7fd434f30000, 4096, PROT_READ) = 0
mprotect(0x7fd436045000, 4096, PROT_READ) = 0
mprotect(0x7fd43932e000, 4096, PROT_READ) = 0
mprotect(0x7fd43824e000, 4096, PROT_READ) = 0
mprotect(0x7fd435834000, 4096, PROT_READ) = 0
mprotect(0x7fd438459000, 4096, PROT_READ) = 0
mprotect(0x7fd435194000, 4096, PROT_READ) = 0
mprotect(0x7fd4353c1000, 8192, PROT_READ) = 0
mprotect(0x7fd43562f000, 4096, PROT_READ) = 0
mprotect(0x7fd43da79000, 4096, PROT_READ) = 0
mprotect(0x7fd43a75e000, 4096, PROT_READ) = 0
mprotect(0x7fd435be3000, 32768, PROT_READ) = 0
mprotect(0x7fd43a544000, 4096, PROT_READ) = 0
mprotect(0x7fd435e24000, 4096, PROT_READ) = 0
mprotect(0x7fd436291000, 4096, PROT_READ) = 0
mprotect(0x7fd4364a3000, 4096, PROT_READ) = 0
mprotect(0x7fd4366b3000, 4096, PROT_READ) = 0
mprotect(0x7fd43773f000, 4096, PROT_READ) = 0
mprotect(0x7fd436906000, 4096, PROT_READ) = 0
mprotect(0x7fd436dd2000, 4096, PROT_READ) = 0
mprotect(0x7fd436ba7000, 24576, PROT_READ) = 0
mprotect(0x7fd436feb000, 4096, PROT_READ) = 0
mprotect(0x7fd437228000, 8192, PROT_READ) = 0
mprotect(0x7fd437b4a000, 4096, PROT_READ) = 0
mprotect(0x7fd43c65a000, 40960, PROT_READ) = 0
mprotect(0x7fd438663000, 4096, PROT_READ) = 0
mprotect(0x7fd43c12b000, 253952, PROT_READ) = 0
mprotect(0x7fd4397cf000, 8192, PROT_READ) = 0
mprotect(0x7fd43a9e1000, 4096, PROT_READ) = 0
mprotect(0x7fd437d79000, 8192, PROT_READ) = 0
mprotect(0x7fd43ad2f000, 24576, PROT_READ) = 0
mprotect(0x7fd438034000, 16384, PROT_READ) = 0
mprotect(0x7fd438868000, 4096, PROT_READ) = 0
mprotect(0x7fd438a71000, 4096, PROT_READ) = 0
mprotect(0x7fd438d68000, 73728, PROT_READ) = 0
mprotect(0x7fd438ff4000, 8192, PROT_READ) = 0
mprotect(0x7fd439589000, 8192, PROT_READ) = 0
mprotect(0x7fd439ef4000, 4096, PROT_READ) = 0
mprotect(0x7fd43d87c000, 65536, PROT_READ) = 0
mprotect(0x7fd43ccb2000, 155648, PROT_READ) = 0
mprotect(0x7fd43cee2000, 4096, PROT_READ) = 0
mprotect(0x7fd43d397000, 69632, PROT_READ) = 0
mprotect(0x671000, 4096, PROT_READ)     = 0
mprotect(0x7fd43dab3000, 4096, PROT_READ) = 0
munmap(0x7fd43da8a000, 156356)          = 0
set_tid_address(0x7fd43d9cfb10)         = 21241
set_robust_list(0x7fd43d9cfb20, 24)     = 0
rt_sigaction(SIGRTMIN, {0x7fd439efbbb0, [], SA_RESTORER|SA_SIGINFO, 0x7fd439f06d10}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7fd439efbc40, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7fd439f06d10}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
brk(0)                                  = 0xcbc000
brk(0xcdd000)                           = 0xcdd000
futex(0x7fd43b48026c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fd43b480278, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fd437741428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fd437741428, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0x7fd43c665158, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2919792, ...}) = 0
mmap(NULL, 2919792, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7fd432317000
close(3)                                = 0
brk(0xcfe000)                           = 0xcfe000
stat(".", {st_mode=S_IFDIR|0700, st_size=4096, ...}) = 0
getcwd("/home/arlen/Development/FreePascal/lazarus", 4096) = 43
open("/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26258, ...}) = 0
mmap(NULL, 26258, PROT_READ, MAP_SHARED, 3, 0) = 0x7fd43daaa000
close(3)                                = 0
futex(0x7fd43b0fca10, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/x86_64-linux-gnu/gconv/UTF-16.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\7\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=17944, ...}) = 0
mmap(NULL, 2109544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7fd432113000
mprotect(0x7fd432114000, 2101248, PROT_NONE) = 0
mprotect(0x7fd432113000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC) = 0
mprotect(0x7fd432113000, 4096, PROT_READ|PROT_EXEC) = 0
mmap(0x7fd432114000, 4604, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd432114000
mmap(0x7fd432315000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7fd432315000
mmap(0x7fd432316000, 104, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7fd432316000
close(3)                                = 0
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x8} ---
+++ killed by SIGSEGV (core dumped) +++
```

---

