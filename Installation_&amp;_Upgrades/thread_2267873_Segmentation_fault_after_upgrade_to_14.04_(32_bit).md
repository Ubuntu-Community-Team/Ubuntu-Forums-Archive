---
title: "Segmentation fault after upgrade to 14.04 (32 bit)"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by philipp14 on 2015-03-04
gskcrypt library, as I get the following information from gdb: 


```
(gdb) run 
Starting program: /opt/tivoli/tsm/client/ba/bin/dsmc 
[Thread debugging using libthread_db enabled] 
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1". 
[New Thread 0xb6d5cb40 (LWP 3134)] 


Program received signal SIGSEGV, Segmentation fault. 
0x082f0a19 in psCreateCryptoKey(unsigned char*, char*) () 


(gdb) backtrace 
#0 0x082f0a19 in psCreateCryptoKey(unsigned char*, char*) () 
#1 0x082f0bfa in psSetUpCryptoKey(unsigned char*, char*) () 
#2 0x082f3a1f in psSetUpPswdFI(Sess_o*, int) () 
#3 0x0824918e in Sess_o::sessNewpswdFI() () 
#4 0x0824d217 in Sess_o::Sess_o(clientOptions*, int) () 
#5 0x0824d32e in new_SessionObject(clientOptions*, int) () 
#6 0x08062571 in dscInit(int, char**, cliType_t) () 
#7 0x08062fda in dscmain(int, char**) () 
#8 0x0805fa71 in main () 


(gdb) x 0x082f0a19 
0x82f0a19 <_Z17psCreateCryptoKeyPhPc+169>:0x8b02508b
```
 Dear forum,

I have a problem with the IBM TSM client, which was previously running fine on my 12.10 installation (32 bit). I upgraded to 14.04 (32 bit) and the client is not producing segmentation faults. I get the following in the log file:

ANS0361I DIAG: main thread, fatal error, signal 11


Trying to start dsmc by hand, I get:


Aborted (core dumped)

Version of the client is [COLOR=#141414][FONT=Georgia] 6.2.5-4, installed from RPM packages via alien. 

I already asked the question at adsm.org, but nobody was able to help. A similar issue was reported here: [/FONT][/COLOR][https://adsm.org/forum/index.php?threads/ubuntu-32-bit.29324/](https://adsm.org/forum/index.php?threads/ubuntu-32-bit.29324/)
[COLOR=#141414][FONT=Georgia]Unfortunately, I cannot get help from IBM, because [/FONT][/COLOR][COLOR=#141414][FONT=Georgia]I don't have the required privileges...

I believe the problem is related to [/FONT][/COLOR]gskcrypt library, as I get the following information from gdb: 


```
(gdb) run 
Starting program: /opt/tivoli/tsm/client/ba/bin/dsmc 
[Thread debugging using libthread_db enabled] 
Using host libthread_db library "/lib/i386-linux-gnu/libthread_db.so.1". 
[New Thread 0xb6d5cb40 (LWP 3134)] 


Program received signal SIGSEGV, Segmentation fault. 
0x082f0a19 in psCreateCryptoKey(unsigned char*, char*) () 


(gdb) backtrace 
#0 0x082f0a19 in psCreateCryptoKey(unsigned char*, char*) () 
#1 0x082f0bfa in psSetUpCryptoKey(unsigned char*, char*) () 
#2 0x082f3a1f in psSetUpPswdFI(Sess_o*, int) () 
#3 0x0824918e in Sess_o::sessNewpswdFI() () 
#4 0x0824d217 in Sess_o::Sess_o(clientOptions*, int) () 
#5 0x0824d32e in new_SessionObject(clientOptions*, int) () 
#6 0x08062571 in dscInit(int, char**, cliType_t) () 
#7 0x08062fda in dscmain(int, char**) () 
#8 0x0805fa71 in main () 


(gdb) x 0x082f0a19 
0x82f0a19 <_Z17psCreateCryptoKeyPhPc+169>:0x8b02508b
```

Unfortunately, this doesn't really help me to solve the problem. 

Do you have any advice how I could get to the bottom of this?

Thank you very much,
Philipp

PS: Here is also an strace

Here is an strace as well:

```
execve("./dsmc", ["./dsmc"], [/* 27 vars */]) = 0
brk(0)                                  = 0x9f1c000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb775a000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=42622, ...}) = 0
mmap2(NULL, 42622, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb774f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libcrypt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\t\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=38456, ...}) = 0
mmap2(NULL, 196956, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb771e000
mmap2(0xb7726000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0xb7726000
mmap2(0xb7728000, 155996, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7728000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320]\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=134614, ...}) = 0
mmap2(NULL, 111276, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7702000
mmap2(0xb771a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0xb771a000
mmap2(0xb771c000, 4780, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb771c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13856, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7701000
mmap2(NULL, 16512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb76fc000
mmap2(0xb76ff000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0xb76ff000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libstdc++.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20f\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=922096, ...}) = 0
mmap2(NULL, 951840, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7613000
mprotect(0xb76ef000, 4096, PROT_NONE)   = 0
mmap2(0xb76f0000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xdc000) = 0xb76f0000
mmap2(0xb76f5000, 26144, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb76f5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgpfs.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320-\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0555, st_size=39165, ...}) = 0
mmap2(NULL, 35364, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb760a000
mmap2(0xb7612000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0xb7612000
mprotect(0xbffb7000, 4096, PROT_READ|PROT_WRITE|PROT_EXEC|PROT_GROWSDOWN) = 0
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdmapi.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0555, st_size=23864, ...}) = 0
mmap2(NULL, 24036, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7604000
mmap2(0xb7609000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x4000) = 0xb7609000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30696, ...}) = 0
mmap2(NULL, 33352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75fb000
mmap2(0xb7602000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0xb7602000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgsk8ssl.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\206\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1140600, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75fa000
mmap2(NULL, 1138260, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74e4000
mmap2(0xb75f3000, 28672, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x10f000) = 0xb75f3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgsk8iccs.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0Pq\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=327060, ...}) = 0
mmap2(NULL, 338948, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7491000
mmap2(0xb74d9000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x47000) = 0xb74d9000
mmap2(0xb74e2000, 7172, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb74e2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgsk8cms.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\313\t\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=2736868, ...}) = 0
mmap2(NULL, 2735352, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71f5000
mmap2(0xb747c000, 86016, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x286000) = 0xb747c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgsk8sys.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \v\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=7708, ...}) = 0
mmap2(NULL, 10268, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71f2000
mmap2(0xb71f4000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb71f4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0F\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=280108, ...}) = 0
mmap2(NULL, 282784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb71ac000
mmap2(0xb71f0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x43000) = 0xb71f0000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libgcc_s.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240 \0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=113588, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb71ab000
mmap2(NULL, 116756, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb718e000
mmap2(0xb71aa000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0xb71aa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\233\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1754876, ...}) = 0
mmap2(NULL, 1759868, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6fe0000
mmap2(0xb7188000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a8000) = 0xb7188000
mmap2(0xb718b000, 10876, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb718b000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6fdf000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6fde000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb6fde700, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7188000, 8192, PROT_READ)   = 0
mprotect(0xb71f0000, 4096, PROT_READ)   = 0
mprotect(0xb771a000, 4096, PROT_READ)   = 0
mprotect(0xb76ff000, 4096, PROT_READ)   = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6fdd000
mprotect(0xb76f0000, 16384, PROT_READ)  = 0
mprotect(0xb7602000, 4096, PROT_READ)   = 0
mprotect(0xb7604000, 20480, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7604000, 20480, PROT_READ|PROT_EXEC) = 0
mprotect(0xb760a000, 32768, PROT_READ|PROT_WRITE) = 0
mprotect(0xb760a000, 32768, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7726000, 4096, PROT_READ)   = 0
mprotect(0xb777d000, 4096, PROT_READ)   = 0
munmap(0xb774f000, 42622)               = 0
set_tid_address(0xb6fde768)             = 13911
set_robust_list(0xb6fde770, 12)         = 0
futex(0xbffb6d24, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, b6fde700) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xb77077d0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7707850, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="ide-vm", ...}) = 0
futex(0xb76fa2b4, FUTEX_WAKE_PRIVATE, 2147483647) = 0
futex(0xb76fa2bc, FUTEX_WAKE_PRIVATE, 2147483647) = 0
brk(0)                                  = 0x9f1c000
brk(0x9f3d000)                          = 0x9f3d000
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/lib", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
lstat64("/usr/lib/libgsk8cms.so", {st_mode=S_IFLNK|0777, st_size=37, ...}) = 0
readlink("/usr/lib/libgsk8cms.so", "/usr/local/ibm/gsk8/lib/libgsk8c"..., 4095) = 37
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8/lib/libgsk8cms.so", {st_mode=S_IFREG|0755, st_size=2736868, ...}) = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, {B9600 opost isig icanon echo ...}) = 0
stat64("/dev/console", {st_mode=S_IFCHR|0600, st_rdev=makedev(5, 1), ...}) = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
ioctl(1, TIOCGWINSZ, {ws_row=36, ws_col=124, ws_xpixel=868, ws_ypixel=504}) = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=10550800, ...}) = 0
mmap2(NULL, 2097152, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ddd000
mmap2(NULL, 249856, PROT_READ, MAP_PRIVATE, 3, 0x439000) = 0xb6da0000
close(3)                                = 0
open("/usr/lib/i386-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=26256, ...}) = 0
mmap2(NULL, 26256, PROT_READ, MAP_SHARED, 3, 0) = 0xb7753000
close(3)                                = 0
futex(0xb718afa8, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/i386-linux-gnu/gconv/ISO8859-1.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\4\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9608, ...}) = 0
mmap2(NULL, 12324, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb774f000
mmap2(0xb7751000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7751000
close(3)                                = 0
mprotect(0xb7751000, 4096, PROT_READ)   = 0
open("/dev/tty", O_RDONLY|O_LARGEFILE)  = 3
ioctl(3, SNDCTL_TMR_TEMPO or SNDRV_TIMER_IOCTL_GSTATUS or TCGETA, {B9600 opost isig icanon echo ...}) = 0
close(3)                                = 0
brk(0x9f61000)                          = 0x9f61000
geteuid32()                             = 0
uname({sys="Linux", node="ide-vm", ...}) = 0
access("/usr/bin/lsb_release", X_OK)    = 0
pipe2([3, 4], O_CLOEXEC)                = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb6fde768) = 13912
close(4)                                = 0
fcntl64(3, F_SETFD, 0)                  = 0
fstat64(3, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6d9f000
read(3, "Ubuntu 14.04.2 LTS\n", 4096)   = 19
read(3, "", 4096)                       = 0
--- SIGCHLD {si_signo=SIGCHLD, si_code=CLD_EXITED, si_pid=13912, si_status=0, si_utime=0, si_stime=0} ---
close(3)                                = 0
waitpid(13912, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 13912
munmap(0xb6d9f000, 4096)                = 0
open("/etc/TIVGUID", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=70, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6d9f000
read(3, "This is the Tivoli GUID file do "..., 4096) = 70
close(3)                                = 0
munmap(0xb6d9f000, 4096)                = 0
getcwd("/opt/tivoli/tsm/client/ba/bin", 1024) = 30
stat64("/opt/tivoli/tsm/client/ba/bin/./dsmc", {st_mode=S_IFREG|0555, st_size=6352958, ...}) = 0
access("./dsmc", X_OK)                  = 0
getuid32()                              = 0
getgid32()                              = 0
geteuid32()                             = 0
getegid32()                             = 0
stat64("/opt/tivoli/tsm/client/ba/bin/./dsmc", {st_mode=S_IFREG|0555, st_size=6352958, ...}) = 0
setresuid32(-1, 0, -1)                  = 0
getcwd("/opt/tivoli/tsm/client/ba/bin", 1024) = 30
stat64("/opt/tivoli/tsm/client/ba/bin/./dsmc", {st_mode=S_IFREG|0555, st_size=6352958, ...}) = 0
access("./dsmc", X_OK)                  = 0
open("/opt/tivoli/tsm/client/ba/bin/EN_US/dsmclientV3.cat", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=849988, ...}) = 0
mmap2(NULL, 849988, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6cd0000
close(3)                                = 0
open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ccf000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ccf000, 4096)                = 0
open("/usr/share/locale/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/libc.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
rt_sigaction(SIGPIPE, {SIG_IGN, [], 0}, NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [QUIT TERM XCPU XFSZ PWR], NULL, 8) = 0
rt_sigaction(SIGILL, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGFPE, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGBUS, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGSEGV, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGUSR1, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGABRT, {0x82fb484, [], 0}, NULL, 8) = 0
rt_sigaction(SIGTRAP, {0x82fb484, [], 0}, NULL, 8) = 0
open("/opt/tivoli/tsm/client/ba/bin/dsm.opt", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=737, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6ccf000
read(3, "********************************"..., 4096) = 737
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6ccf000, 4096)                = 0
open("/opt/tivoli/tsm/client/ba/bin/EN_US/dsmclientV3.cat", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=849988, ...}) = 0
mmap2(NULL, 849988, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6c00000
close(3)                                = 0
open("/opt/tivoli/tsm/client/ba/bin/EN_US/dsmclientV3.cat", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=849988, ...}) = 0
mmap2(NULL, 849988, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6b30000
close(3)                                = 0
open("/opt/tivoli/tsm/client/ba/bin/dsm.sys", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=1217, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b2f000
read(3, "********************************"..., 4096) = 1217
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb6b2f000, 4096)                = 0
readlink("/var/log/dsmerror.log", 0xbffb3adb, 1025) = -1 EINVAL (Invalid argument)
open("/var/log/dsmerror.log", O_RDONLY|O_LARGEFILE) = 3
close(3)                                = 0
open("/var/log/dsmerror.log", O_WRONLY|O_CREAT|O_APPEND|O_LARGEFILE, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=36683735, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b2f000
fstat64(3, {st_mode=S_IFREG|0644, st_size=36683735, ...}) = 0
_llseek(3, 36683735, [36683735], SEEK_SET) = 0
close(3)                                = 0
munmap(0xb6b2f000, 4096)                = 0
open("/var/log/dsmerror.log", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=36683735, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b2f000
read(3, "14.09.2011 17:12:56 ANS1036S The"..., 4096) = 4096
close(3)                                = 0
munmap(0xb6b2f000, 4096)                = 0
open("/var/log/dsmerror.log", O_WRONLY|O_CREAT|O_APPEND|O_LARGEFILE, 0666) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=36683735, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6b2f000
fstat64(3, {st_mode=S_IFREG|0644, st_size=36683735, ...}) = 0
_llseek(3, 36683735, [36683735], SEEK_SET) = 0
munmap(0xb6b2f000, 4096)                = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
stat64("/opt/tivoli/tsm/client/ba/bin/plugins", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
openat(AT_FDCWD, "/opt/tivoli/tsm/client/ba/bin/plugins", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 4
getdents64(4, /* 4 entries */, 32768)   = 112
getdents64(4, /* 0 entries */, 32768)   = 0
close(4)                                = 0
futex(0xb7700058, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/opt/tivoli/tsm/client/ba/bin/plugins/libPiSNAP.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260w\1\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0555, st_size=411695, ...}) = 0
mmap2(NULL, 376256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6ad4000
mmap2(0xb6b23000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x4e000) = 0xb6b23000
mmap2(0xb6b27000, 36288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6b27000
close(4)                                = 0
stat64("/opt/tivoli/tsm/client/ba/bin/plugins", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/opt/tivoli/tsm/client/ba/bin/plugins/libPiIMG.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\220\1\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0555, st_size=588754, ...}) = 0
mmap2(NULL, 536544, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6a51000
mmap2(0xb6ac8000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x77000) = 0xb6ac8000
mmap2(0xb6acb000, 36832, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6acb000
close(4)                                = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=42622, ...}) = 0
mmap2(NULL, 42622, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb6a46000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libApiDS.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\321\1\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0555, st_size=5116059, ...}) = 0
mmap2(NULL, 4742784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb65c0000
mmap2(0xb69f8000, 126976, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x438000) = 0xb69f8000
mmap2(0xb6a17000, 192128, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6a17000
close(4)                                = 0
munmap(0xb6a46000, 42622)               = 0
stat64("/opt/tivoli/tsm/client/ba/bin/plugins", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
geteuid32()                             = 0
uname({sys="Linux", node="ide-vm", ...}) = 0
open("/opt/tivoli/tsm/client/ba/bin/dsm.opt", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=737, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "********************************"..., 4096) = 737
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/opt/tivoli/tsm/client/ba/bin/dsm.sys", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=1217, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "********************************"..., 4096) = 1217
_llseek(4, 0, [0], SEEK_SET)            = 0
read(4, "********************************"..., 4096) = 1217
open("/opt/tivoli/tsm/client/ba/bin/inclexcl", O_RDONLY|O_LARGEFILE) = 5
fstat64(5, {st_mode=S_IFREG|0644, st_size=138, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a4f000
read(5, "exclude /.../*\nexclude /*\ninclud"..., 4096) = 138
brk(0x9f82000)                          = 0x9f82000
read(5, "", 4096)                       = 0
close(5)                                = 0
munmap(0xb6a4f000, 4096)                = 0
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
stat64("/opt/tivoli/tsm/client/hsm/bin/dsmrecalld", 0xbffb410c) = -1 ENOENT (No such file or directory)
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/lib", {st_mode=S_IFDIR|0755, st_size=16384, ...}) = 0
lstat64("/usr/lib/libgsk8iccs.so", {st_mode=S_IFLNK|0777, st_size=38, ...}) = 0
readlink("/usr/lib/libgsk8iccs.so", "/usr/local/ibm/gsk8/lib/libgsk8i"..., 4095) = 38
lstat64("/usr", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
lstat64("/usr/local/ibm/gsk8/lib/libgsk8iccs.so", {st_mode=S_IFREG|0755, st_size=327060, ...}) = 0
open("/usr/local/ibm/gsk8/lib/N/icc/icclib/libicclib083.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`m\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0755, st_size=290308, ...}) = 0
mmap2(NULL, 293996, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6578000
mmap2(0xb65b6000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3e000) = 0xb65b6000
mmap2(0xb65bf000, 3180, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb65bf000
close(4)                                = 0
time(NULL)                              = 1425498940
open("/usr/local/ibm/gsk8/lib/C/icc/icclib/libicclib082.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200i\0\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0755, st_size=232520, ...}) = 0
mmap2(NULL, 243788, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb653c000
mmap2(0xb656e000, 32768, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x31000) = 0xb656e000
mmap2(0xb6576000, 6220, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6576000
close(4)                                = 0
time(NULL)                              = 1425498940
time(NULL)                              = 1425498940
open("/usr/local/ibm/gsk8/lib/C/icc/osslib/libcryptoIBM082.so.1.0.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2007\3\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0755, st_size=1264932, ...}) = 0
mmap2(NULL, 1260220, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb6408000
mmap2(0xb6526000, 77824, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x11e000) = 0xb6526000
mmap2(0xb6539000, 10940, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6539000
close(4)                                = 0
uname({sys="Linux", node="ide-vm", ...}) = 0
gettimeofday({1425498940, 235933}, NULL) = 0
open("/usr/local/ibm/gsk8/lib/C/icc/icclib/libicclib082.so", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0755, st_size=232520, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200i\0\0004\0\0\0"..., 16384) = 16384
read(4, "\10\0\0\0dh\3\0\10\0\0\0lh\3\0\10\0\0\0th\3\0\10\0\0\0|h\3\0"..., 16384) = 16384
read(4, "U\211\345S\203\354\24\213E\10\3508\352\377\377\201\303q\244\2\0\205\300u\v\203\304\24\270\376\377\377"..., 16384) = 16384
read(4, "E\f\211\4$\377\322\203\304\4[]\303\215v\0\213\203\364\377\377\377\213\0\205\300t\323\203\304\0041"..., 16384) = 16384
read(4, "\17\266M\350\270\1\0\0\0\323\340\213M\350\205E\360un\213M\350\353\f\270\1\0\0\0\323\340\205"..., 16384) = 16384
read(4, "E\210\205\300\17\204\371\0\0\0\213E\210\211t$\4\307D$\10\0\1\0\0\211\4$\350[(\377"..., 16384) = 16384
read(4, "\202\244\1\0\211u\370\211}\374\350A\351\377\377\213\2130Q\0\0\203\273\264\215\0\0\1\211\306tP"..., 16384) = 16384
read(4, "\307E\354\0\0\0\0\307E\360\0\0\0\0\203\270\254\3\0\0\7\17\207E\1\0\0\213\200\254\3\0"..., 16384) = 16384
read(4, "\4\213\206\264\3\0\0\211\4$\350\1\235\376\377\213E\330\211D$\10\213E\340\211D$\4\213\206\264"..., 16384) = 16384
read(4, "l\213OH\213WDf\211\4J\213G`\203\350\1\205\300\211G`u\257\203Gl\1\213E\350\205"..., 16384) = 16384
read(4, "Init_ex\0C101_EVP_EncryptUpdate\0C"..., 16384) = 16384
read(4, "-prng/SP800-90.c:1219\0\0\0The data"..., 16384) = 16384
read(4, "\324\236\355(\261\371Q\220_V\344\202:1X:\203\t\217\247\346n3\37\10\301\206\rm\246:\265"..., 16384) = 16384
read(4, "\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 16384) = 16384
read(4, "*\3\255\30\340\210nWr\305\243\37'\34\331p\210\345\2\0\323\233\2\0\1\0\0\0\1\0\0\0"..., 16384) = 3144
read(4, "", 12288)                      = 0
read(4, "", 16384)                      = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/usr/local/ibm/gsk8/lib/C/icc/osslib/libcryptoIBM082.so.1.0.1", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0755, st_size=1264932, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2007\3\0004\0\0\0"..., 16384) = 16384
read(4, "\0\0\0\0\0\0\0\0\357\1\0\0\f\3\0\0\0\0\0\0\0\0\0\0\206\3\0\0\204\1\0\0"..., 16384) = 16384
read(4, "@^\4\0\22\0\0\0\22\0\n\0\235\200\0\0`\177\20\0001\0\0\0\21\0\f\0\23i\0\0"..., 16384) = 16384
read(4, "\0\242\4\0 \0\0\0\22\0\n\0Y\n\1\0\260\0\16\0<\0\0\0\22\0\n\0u\301\0\0"..., 16384) = 16384
read(4, "\20d\n\0 \0\0\0\22\0\n\0\377W\0\0\0208\7\0\363\0\0\0\22\0\n\0\255W\0\0"..., 16384) = 16384
read(4, "101_BN_is_prime_fasttest_ex\0C101"..., 16384) = 16384
read(4, "1_EC_POINT_set_to_infinity\0C101_"..., 16384) = 16384
read(4, "_free\0C101_policy_data_free\0C101"..., 16384) = 16384
read(4, "KEY_USAGE_PERIOD_free\0C101_PKEY_"..., 16384) = 16384
read(4, "\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0\1\0"..., 16384) = 16384
read(4, "\10+\22\0\10\0\0\0\20+\22\0\10\0\0\0\24+\22\0\10\0\0\0 +\22\0\10\0\0\0"..., 16384) = 16384
read(4, "\340v\22\0\10\0\0\0\fw\22\0\10\0\0\0\20w\22\0\10\0\0\0 w\22\0\10\0\0\0"..., 16384) = 16384
read(4, "<\322\22\0\10\0\0\0D\322\22\0\10\0\0\0L\322\22\0\10\0\0\0T\322\22\0\10\0\0\0"..., 16384) = 16384
read(4, "$\350\212\260\0\0\213D$\0241\377\307D$\20\363\0\0\0\211l$\10\307D$\4\217\0\0\0"..., 16384) = 16384
read(4, "\0\0)\301\211D$ \215D$4\211D$\f\215D$0\211D$\10\215l$ \215D$8"..., 16384) = 16384
read(4, "\0\0\205\300t\26\211\4$\350\342Z\5\0\213\206\370\0\0\0\211\4$\350\244\\\5\0\2114$\307"..., 16384) = 16384
read(4, "<\rt\4<\tu\32\203\302\0019\312\215v\0\17\204/\2\0\0\17\266\0042<\37v\336<~"..., 16384) = 16384
read(4, "\274\0\0\0\351\n\376\377\377\215F\340<\20\17\206\37\3\0\0\307D$l\2\0\0\0\351\331\375\377"..., 16384) = 16384
read(4, "G\10\0\0\0\0\3513\375\377\377\213L$`\307D$\4\10\0\0\0\213A$\211\4$\350\216\24"..., 16384) = 16384
read(4, "\0\0\215\206\214\0\0\0\205\311t\10\211\4$\350\214l\0\0\213\226\240\0\0\0\215\206\240\0\0\0"..., 16384) = 16384
read(4, "\377u\322\203D$\24\1\203\356\4\213T$\f\203l$\10 9T$\24u\244\213|$\0209|"..., 16384) = 16384
read(4, "\n\0\211G\f\215F\375\205\300~k\203\305\20\213T$8\203\356\4\213E\0\203\307\20\203D$0"..., 16384) = 16384
read(4, "\301\375\3\215\263\326\200\375\377\307D$\10\206\0\0\0\211t$\4\211,$\350\2431\4\0\205\300\211"..., 16384) = 16384
read(4, "\0\0\211\4$\350\226\24\4\0\350\201\246\1\0\211\4$\350\t\r\4\0\350\204\246\1\0\211\4$\350"..., 16384) = 16384
read(4, "\213N\f\205\311t$\215\24\0101\377\353\4\211\366\211\367\17\266B\377\17\276\360\1\300\t\370\301\356\37"..., 16384) = 16384
read(4, "\265\350*\260\5\0\205\300\211\6u\264\215t&\0001\377\353\206\215\266\0\0\0\0\215\277\0\0\0\0"..., 16384) = 16384
read(4, "\3\0\213T$8\213B\10\205\300t\10\211\4$\350[3\3\0\213L$8\211\f$\350O3\3"..., 16384) = 16384
read(4, "\211\306\3519\376\377\377\211\306\351\222\376\377\377\211\366\211\306\351Y\376\377\377\213D$(\213T$\34\211"..., 16384) = 16384
read(4, "\312\0\0\0\213L$@\213D$H\213T$\\\211L$\10\211D$\4\211\24$\350\0\261\375\377"..., 16384) = 16384
read(4, "Y\377\377\377\215\266\0\0\0\0\215\277\0\0\0\0\203\354,\211t$ \213t$0\211\\$\34\211"..., 16384) = 16384
read(4, "C\270\373\377\201\303\24>\v\0\213E\0\213x\0049\327w;)\3721\366\211T$\30\215t&\0"..., 16384) = 16384
read(4, "\4$\350\231\372\377\377\203\304\30[\303\215t&\0\203\354,\211\\$\34\213D$0\350'x\373\377"..., 16384) = 16384
read(4, "\0\0\0\211D$\f\307\4$\20\0\0\0\350m\375\0\0\353\207\213D$D\277\1\0\0\0\213T"..., 16384) = 16384
read(4, "\0\0\0\350x\275\0\0001\300\351g\377\377\377\220\203\354,\211|$(\213|$0\211\\$ \350"..., 16384) = 16384
read(4, "\205\300\17\204\335\376\377\377\213D$D\213T$T\211|$\20\211D$\f\215\203\336\27\376\377\211D"..., 16384) = 16384
read(4, "\205\300\17\204~\373\377\377\351\306\375\377\377\213D$\\\203\300,\353\250\211t$\10\211T$\4\211\24"..., 16384) = 16384
read(4, "\4\213\\$ \211\320\213t$$\213|$(\203\304,\303\215\273\211\32\376\377\307D$\f'\1\0"..., 16384) = 16384
read(4, "\0\0\307\4$\6\0\0\0\350r\275\377\377\351[\377\377\377\215\203p*\376\377\307D$\20\226\0\0"..., 16384) = 16384
read(4, "$\211L$\4\377RH\211<$\211\306\350nX\375\377\353\254\213D$x\213\224$\224\0\0\0\213"..., 16384) = 16384
read(4, "\0\211|$\10\307D$\4\24\0\0\0\307\4$\t\0\0\0\350\247\350\374\377\213\203\214i\0\0\213"..., 16384) = 16384
read(4, "\10\213D$$\211D$\4\213D$ \211\4$\350\33-\2\0\203\304\30[\303\215\266\0\0\0\0"..., 16384) = 16384
read(4, "[\303\215\264&\0\0\0\0\215\274'\0\0\0\0S\3501\370\370\377\201\303\2~\10\0\203\354\30\213"..., 16384) = 16384
read(4, "\4$\350\371\"\372\377\205\300\211\306td\213D$0\307D$\10\0\0\0\0\307D$\4j\0\0"..., 16384) = 16384
read(4, "\211D$\4\211<$\350\264\361\376\377\205\300\211\306\17\204\33\4\0\0\211D$\4\213D$H\211\4"..., 16384) = 16384
read(4, "\211D$\10\213D$\30\1\370\211D$\4\213D$\24\211\4$\350\n7\370\377\203\370\0t\30\177"..., 16384) = 16384
read(4, "\370\3\303\220\220\220\220\220\220\220\220\220\220\220\220\220UWVS\350.\370\367\377\201\303\377}\7\0\203"..., 16384) = 16384
read(4, "\4\0\0\0\0\307@\24\0\0\0\0\307@\30\0\0\0\0\307@ \0\0\0\0\211F\24\203\300\10"..., 16384) = 16384
read(4, "\201\303\30\376\6\0\211\264$\204\0\0\0\205\377td\215t$\20\2114$\350\343\372\377\377\213\204$"..., 16384) = 16384
read(4, "\213D$D\367\305\1\0\0\0\213\0\211D$(\17\204J\1\0\0\367\305\2\0\0\0\17\204\226\1"..., 16384) = 16384
read(4, "t$0\213|$4\213l$8\203\304<\303\220\213M\0\205\311u\315\353\342\215\264&\0\0\0\0"..., 16384) = 16384
read(4, "3\375\377\203>\3u\246\213F\20\211\4$\350]3\375\377\213F\24\211\4$\350R3\375\377\213F"..., 16384) = 16384
read(4, "L$\4\350H\376\377\377\211\306\353\250\215t&\0\203\354,\211\\$$\213D$0\350'x\366\377"..., 16384) = 16384
read(4, "D$\10\211\4$\350\305\376\377\377\203\304\f[^_]\303\213D$,\211t$\10\2118\353\306\213"..., 16384) = 16384
read(4, "t$\24\350?\370\365\377\201\303\20~\5\0\366G)\1tQ\213O(\211\316\203\346\2t\6\366G"..., 16384) = 16384
read(4, ">\5\0\211D$\20\213D$,\211D$\f\213D$(\211D$\10\213D$$\211D$\4\213"..., 16384) = 16384
read(4, "\377\17\204\271\0\0\0\211\4$\350\221n\377\377\203x\4\377u\33\211,$\350Sw\377\377\203\370\377"..., 16384) = 16384
read(4, "$\4\213D$ \211\4$\350\2\376\377\377\2114$\211\307\350XB\374\377\211\370\213\\$\20\213t"..., 16384) = 16384
read(4, "\350+\355\375\377\203\304\30[\303\215\266\0\0\0\0S\3501\370\364\377\201\303\2~\4\0\203\354\30\213"..., 16384) = 16384
read(4, "B\3\203\300\1\204\300\210B\3u\37\17\266B\2\203\300\1\204\300\210B\2u\21\17\266B\1\203\300"..., 16384) = 16384
read(4, "\344\344\344\00099\0009\16\16\16\0\203\203\0\203sss\0\334\334\0\334\252\252\252\0\252\252\0\252"..., 16384) = 16384
read(4, "\213D$\4\213T$\10\350\0\0\0\0Y\215\211\363\3\0\0\363\17o\0f\17o)\17\20\22f"..., 16384) = 16384
read(4, ">\0\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220\220"..., 16384) = 16384
read(4, "Z\270\377\377\377\377\301\303\6\1\373\1\327\211\352)\330!\332!\310\t\302\213D$\4\301\305\n\215\274"..., 16384) = 16384
read(4, "\0\0\0\0\1\0\4\0\0\1\4\4\0\1\0\0\1\1\0\0\1\1\4\4\0\0\4\0\1\0\0\4"..., 16384) = 16384
read(4, "D2I\0ASN1_TIME_adj\0ASN1_TIME_set\0"..., 16384) = 16384
read(4, "cast\0CAST-cbc\0cast-cbc\0AES-128-C"..., 16384) = 16384
read(4, " \0s:   \0priv:\0pub: \0P:   \0Q:   \0"..., 16384) = 16384
read(4, "@4\3@4\3@4\3@4\3@4\3@4\3@4\3@4\3@4\3#\303\23\372\265"..., 16384) = 16384
read(4, "-aa-macValue\0id-smime-aa-equival"..., 16384) = 16384
read(4, "+\3\0\0001\3\0\0,\3\0\0002\3\0\0)\3\0\0000\3\0\0'\3\0\0U\3\0\0"..., 16384) = 16384
read(4, "requestExtensions\0tbsRequest\0opt"..., 16384) = 16384
read(4, "y.c\0v3_alt.c\0URI\0IP\0dirName\0move"..., 16384) = 16384
read(4, "\300\2\0\0\300\220\20\0\0\0\0\0\f\211\20\0\301\2\0\0@\221\20\0\0\0\0\0008\211\20\0"..., 16384) = 16384
read(4, "i\2\0\0\4\0\0\0Ll\21\0\0\0\0\0k\33\21\0k\33\21\0j\2\0\0\4\0\0\0"..., 16384) = 16384
read(4, "\367\2\0\0\1\0\0\0 \0\0\0\20\0\0\0\3\0\0\0@n\7\0\360t\7\0\0\0\0\0"..., 16384) = 16384
read(4, "\0\260\6\r\27\375\17\0\0\200\v\r)\375\17\0\0\340\6\r5\375\17\0\0\360\6\rA\375\17\0"..., 16384) = 16384
read(4, "\372\301\21\0\3\0\0\0\n\302\21\0\34\302\21\0\4\0\0\0-\302\21\0;\302\21\0\5\0\0\0"..., 16384) = 16384
read(4, "\0GCC: (GNU) 4.1.2 20070115 (SUSE"..., 16384) = 3364
read(4, "", 12288)                      = 0
read(4, "", 16384)                      = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
time(NULL)                              = 1425498940
gettimeofday({1425498940, 307295}, NULL) = 0
gettimeofday({1425498940, 313869}, NULL) = 0
gettimeofday({1425498940, 319121}, NULL) = 0
gettimeofday({1425498940, 325663}, NULL) = 0
time(NULL)                              = 1425498940
time(NULL)                              = 1425498940
time(NULL)                              = 1425498940
time(NULL)                              = 1425498940
time(NULL)                              = 1425498940
gettimeofday({1425498940, 401784}, NULL) = 0
gettimeofday({1425498940, 411567}, NULL) = 0
gettimeofday({1425498940, 420139}, NULL) = 0
gettimeofday({1425498940, 420478}, NULL) = 0
gettimeofday({1425498940, 425776}, NULL) = 0
gettimeofday({1425498940, 431273}, NULL) = 0
gettimeofday({1425498940, 431579}, NULL) = 0
gettimeofday({1425498940, 438045}, NULL) = 0
gettimeofday({1425498940, 443689}, NULL) = 0
gettimeofday({1425498940, 444055}, NULL) = 0
gettimeofday({1425498940, 451345}, NULL) = 0
gettimeofday({1425498940, 456055}, NULL) = 0
gettimeofday({1425498940, 456367}, NULL) = 0
gettimeofday({1425498940, 461675}, NULL) = 0
gettimeofday({1425498940, 465800}, NULL) = 0
gettimeofday({1425498940, 466088}, NULL) = 0
gettimeofday({1425498940, 472009}, NULL) = 0
gettimeofday({1425498940, 476171}, NULL) = 0
gettimeofday({1425498940, 476587}, NULL) = 0
gettimeofday({1425498940, 483441}, NULL) = 0
gettimeofday({1425498940, 491071}, NULL) = 0
gettimeofday({1425498940, 491366}, NULL) = 0
gettimeofday({1425498940, 496975}, NULL) = 0
gettimeofday({1425498940, 501873}, NULL) = 0
gettimeofday({1425498940, 502209}, NULL) = 0
gettimeofday({1425498940, 511185}, NULL) = 0
gettimeofday({1425498940, 518903}, NULL) = 0
gettimeofday({1425498940, 519230}, NULL) = 0
gettimeofday({1425498940, 529628}, NULL) = 0
gettimeofday({1425498940, 536961}, NULL) = 0
gettimeofday({1425498940, 537350}, NULL) = 0
gettimeofday({1425498940, 543093}, NULL) = 0
gettimeofday({1425498940, 548457}, NULL) = 0
gettimeofday({1425498940, 548760}, NULL) = 0
gettimeofday({1425498940, 556443}, NULL) = 0
gettimeofday({1425498940, 562417}, NULL) = 0
gettimeofday({1425498940, 562807}, NULL) = 0
gettimeofday({1425498940, 568779}, NULL) = 0
gettimeofday({1425498940, 573652}, NULL) = 0
gettimeofday({1425498940, 574008}, NULL) = 0
gettimeofday({1425498940, 577098}, NULL) = 0
gettimeofday({1425498940, 580926}, NULL) = 0
gettimeofday({1425498940, 581279}, NULL) = 0
gettimeofday({1425498940, 583991}, NULL) = 0
gettimeofday({1425498940, 586082}, NULL) = 0
gettimeofday({1425498940, 586434}, NULL) = 0
gettimeofday({1425498940, 589800}, NULL) = 0
gettimeofday({1425498940, 592865}, NULL) = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
futex(0xb718be2c, FUTEX_WAKE_PRIVATE, 2147483647) = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
brk(0x9fa8000)                          = 0x9fa8000
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
brk(0x9fd9000)                          = 0x9fd9000
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/proc/mounts", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "rootfs / rootfs rw 0 0\nsysfs /sy"..., 1024) = 1024
read(4, "lv001 /data ext4 rw,relatime,dat"..., 1024) = 46
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
brk(0x9fc0000)                          = 0x9fc0000
brk(0x9fa8000)                          = 0x9fa8000
brk(0x9f8f000)                          = 0x9f8f000
openat(AT_FDCWD, "/tmp/TSM", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
mmap2(NULL, 512000, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb638b000
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/proc/mounts", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "rootfs / rootfs rw 0 0\nsysfs /sy"..., 1024) = 1024
read(4, "lv001 /data ext4 rw,relatime,dat"..., 1024) = 46
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
statfs64("/", 84, {f_type="EXT2_SUPER_MAGIC", f_bsize=4096, f_blocks=3063340, f_bfree=708785, f_bavail=547416, f_files=786432, f_ffree=540306, f_fsid={-371423568, -29257012}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
statfs64("/proc", 84, {f_type="PROC_SUPER_MAGIC", f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4142}) = 0
stat64("/proc", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
statfs64("/sys", 84, {f_type="SYSFS_MAGIC", f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4142}) = 0
stat64("/sys", {st_mode=S_IFDIR|0555, st_size=0, ...}) = 0
statfs64("/sys/fs/cgroup", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=1, f_bfree=1, f_bavail=1, f_files=202220, f_ffree=202218, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/sys/fs/cgroup", {st_mode=S_IFDIR|0755, st_size=60, ...}) = 0
statfs64("/sys/fs/fuse/connections", 84, {f_type=0x65735543, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/sys/fs/fuse/connections", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
statfs64("/sys/kernel/debug", 84, {f_type=0x64626720, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/sys/kernel/debug", {st_mode=S_IFDIR|0700, st_size=0, ...}) = 0
statfs64("/sys/kernel/security", 84, {f_type=0x73636673, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/sys/kernel/security", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
statfs64("/dev", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=1033006, f_bfree=1033003, f_bavail=1033003, f_files=197227, f_ffree=196785, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/dev", {st_mode=S_IFDIR|0755, st_size=4240, ...}) = 0
open("/etc/fstab", O_RDONLY|O_CLOEXEC)  = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=989, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "# /etc/fstab: static file system"..., 4096) = 989
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
statfs64("/run", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=207101, f_bfree=206972, f_bavail=206972, f_files=202220, f_ffree=201823, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4138}) = 0
stat64("/run", {st_mode=S_IFDIR|0755, st_size=660, ...}) = 0
statfs64("/run/lock", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=1280, f_bfree=1280, f_bavail=1280, f_files=202220, f_ffree=202214, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4142}) = 0
stat64("/run/lock", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=120, ...}) = 0
statfs64("/run/shm", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=1035503, f_bfree=1035503, f_bavail=1035503, f_files=202220, f_ffree=202219, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4134}) = 0
stat64("/run/shm", {st_mode=S_IFDIR|S_ISVTX|0777, st_size=40, ...}) = 0
statfs64("/run/user", 84, {f_type=0x1021994, f_bsize=4096, f_blocks=25600, f_bfree=25600, f_bavail=25600, f_files=202220, f_ffree=202217, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4142}) = 0
stat64("/run/user", {st_mode=S_IFDIR|0755, st_size=80, ...}) = 0
statfs64("/sys/fs/pstore", 84, {f_type=0x6165676c, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/sys/fs/pstore", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
statfs64("/sys/fs/cgroup/systemd", 84, {f_type=0x27e0eb, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096, f_flags=4142}) = 0
stat64("/sys/fs/cgroup/systemd", {st_mode=S_IFDIR|0755, st_size=0, ...}) = 0
statfs64("/data", 84, {f_type="EXT2_SUPER_MAGIC", f_bsize=4096, f_blocks=128981614, f_bfree=93342103, f_bavail=86784459, f_files=32768000, f_ffree=32451931, f_fsid={-1906668704, -244025993}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/data", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
munmap(0xb638b000, 512000)              = 0
statfs64("/", 84, {f_type="EXT2_SUPER_MAGIC", f_bsize=4096, f_blocks=3063340, f_bfree=708785, f_bavail=547416, f_files=786432, f_ffree=540306, f_fsid={-371423568, -29257012}, f_namelen=255, f_frsize=4096, f_flags=4128}) = 0
stat64("/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/mtab", O_RDONLY|O_CLOEXEC)   = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=780, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "/dev/sda1 / ext4 rw,errors=remou"..., 4096) = 780
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0xb5c07000
mprotect(0xb5c07000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb6407424, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb6407ba8, {entry_number:6, base_addr:0xb6407b40, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb6407ba8) = 13914
select(0, NULL, NULL, NULL, {0, 50000}) = 0 (Timeout)
sched_yield()                           = 0
mmap2(NULL, 2101248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb5a06000
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x2} ---
time(NULL)                              = 1425498940
open("/etc/localtime", O_RDONLY|O_CLOEXEC) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6a50000
read(4, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10\0\0\0\0"..., 4096) = 2309
_llseek(4, -28, [2281], SEEK_CUR)       = 0
read(4, "\nCET-1CEST,M3.5.0,M10.5.0/3\n", 4096) = 28
close(4)                                = 0
munmap(0xb6a50000, 4096)                = 0
write(3, "03/04/2015 20:55:40 ANS0361I DIA"..., 71) = 71
rt_sigaction(SIGABRT, {SIG_DFL, [], SA_RESTORER|SA_STACK|SA_RESTART|SA_INTERRUPT|SA_NODEFER|SA_RESETHAND|SA_SIGINFO|SA_NOCLDSTOP|SA_NOCLDWAIT|0x3fffff8, 0xb770c100}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [ABRT], NULL, 8) = 0
tgkill(13911, 13911, SIGABRT)           = 0
--- SIGABRT {si_signo=SIGABRT, si_code=SI_TKILL, si_pid=13911, si_uid=0} ---
+++ killed by SIGABRT (core dumped) +++
Aborted (core dumped)
```

---

### Post by Frank_Knoben on 2015-03-25
Please see the following redhat bug: [https://bugzilla.redhat.com/show_bug.cgi?id=1030142](https://bugzilla.redhat.com/show_bug.cgi?id=1030142)
Basically, it's a bug in the libcrypt.so.1, if you install a libcrypt.so.1 version, which does not have
this bug and set the LD_LIBRARY_PATH, so that dsmc links against this version, it should work.

---

