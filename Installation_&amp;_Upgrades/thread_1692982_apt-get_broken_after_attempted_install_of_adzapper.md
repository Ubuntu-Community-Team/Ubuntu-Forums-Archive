---
title: "apt-get broken after attempted install of adzapper"
date: 2011-02-22
forum: Installation &amp; Upgrades
---

### Post by ThomasJAndrews on 2011-02-22
Have a hyper-V installation of Ubuntu 10.10 which I am working with. Till my attempted installation of adzapper using apt-get, apt-get update and apt-get install worked well with completion times being very short, usually under 10 seconds for small packages. My internet connection is high speed ASL. I am connecting through a local proxy server. Everything else concerning connectivity on my assembly prototype seems to be functioning excellently, that includes wget and browser use. When I now do a apt-get update, it gets stuck on waiting for headers. I did an strace apt-get update, the text of which you can view below:

execve("/usr/bin/apt-get", ["apt-get", "update"], [/* 27 vars */]) = 0
brk(0)                                  = 0x8c21000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb76e2000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=52774, ...}) = 0
mmap2(NULL, 52774, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb76d5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libapt-pkg.so.4.10", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\0\2\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1026824, ...}) = 0
mmap2(NULL, 1030844, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75d9000
mmap2(0xb76d2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xf8) = 0xb76d2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libutil.so.1", O_RDONLY)     = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9748, ...}) = 0
mmap2(NULL, 12424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75d5000
mmap2(0xb75d7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb75d7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libstdc++.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340B\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=930044, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75d4000
mmap2(NULL, 959532, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74e9000
mmap2(0xb75c8000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xde) = 0xb75c8000
mmap2(0xb75cd000, 25644, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb75cd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libm.so.6", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\2604\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149392, ...}) = 0
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74c3000
mmap2(0xb74e7000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb74e7000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libgcc_s.so.1", O_RDONLY)    = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\37\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=108040, ...}) = 0
mmap2(NULL, 111148, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74a7000
mmap2(0xb74c1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19) = 0xb74c1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libc.so.6", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@n\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1421892, ...}) = 0
mmap2(NULL, 1427880, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb734a000
mmap2(0xb74a1000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157) = 0xb74a1000
mmap2(0xb74a4000, 10664, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb74a4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libdl.so.2", O_RDONLY)       = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9736, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7346000
mmap2(0xb7348000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7348000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/libz.so.1", O_RDONLY)        = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\27\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=79476, ...}) = 0
mmap2(NULL, 82192, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7331000
mmap2(0xb7344000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0xb7344000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7330000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb732f000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb732f6d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7344000, 4096, PROT_READ)   = 0
mprotect(0xb7348000, 4096, PROT_READ)   = 0
mprotect(0xb74a1000, 8192, PROT_READ)   = 0
mprotect(0xb74c1000, 4096, PROT_READ)   = 0
mprotect(0xb74e7000, 4096, PROT_READ)   = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb732e000
mprotect(0xb75c8000, 16384, PROT_READ)  = 0
mprotect(0xb75d7000, 4096, PROT_READ)   = 0
mprotect(0xb76d2000, 8192, PROT_READ)   = 0
mprotect(0x806a000, 4096, PROT_READ)    = 0
mprotect(0xb7701000, 4096, PROT_READ)   = 0
munmap(0xb76d5000, 52774)               = 0
brk(0)                                  = 0x8c21000
brk(0x8c42000)                          = 0x8c42000
open("/dev/null", O_WRONLY|O_CREAT|O_TRUNC|O_LARGEFILE, 0666) = 3
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=2985392, ...}) = 0
mmap2(NULL, 2097152, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb712e000
close(4)                                = 0
stat64("/var/lib/apt/.", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/etc/apt/apt.conf.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/usr/lib/gconv/gconv-modules.cache", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=26048, ...}) = 0
mmap2(NULL, 26048, PROT_READ, MAP_SHARED, 4, 0) = 0xb76db000
close(4)                                = 0
open("/etc/apt/apt.conf.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 4
fcntl64(4, F_GETFD)                     = 0x1 (flags FD_CLOEXEC)
getdents(4, /* 15 entries */, 32768)    = 372
stat64("/etc/apt/apt.conf.d/05aptitude", {st_mode=S_IFREG|0644, st_size=157, ...}) = 0
stat64("/etc/apt/apt.conf.d/20dbus", {st_mode=S_IFREG|0644, st_size=243, ...}) = 0
stat64("/etc/apt/apt.conf.d/01autoremove", {st_mode=S_IFREG|0644, st_size=395, ...}) = 0
stat64("/etc/apt/apt.conf.d/70debconf", {st_mode=S_IFREG|0644, st_size=255, ...}) = 0
stat64("/etc/apt/apt.conf.d/15update-stamp", {st_mode=S_IFREG|0644, st_size=108, ...}) = 0
stat64("/etc/apt/apt.conf.d/20archive", {st_mode=S_IFREG|0644, st_size=85, ...}) = 0
stat64("/etc/apt/apt.conf.d/30autoproxy", {st_mode=S_IFREG|0755, st_size=87, ...}) = 0
stat64("/etc/apt/apt.conf.d/99update-notifier", {st_mode=S_IFREG|0644, st_size=231, ...}) = 0
stat64("/etc/apt/apt.conf.d/20auto-upgrades", {st_mode=S_IFREG|0644, st_size=80, ...}) = 0
stat64("/etc/apt/apt.conf.d/00trustcdrom", {st_mode=S_IFREG|0644, st_size=40, ...}) = 0
stat64("/etc/apt/apt.conf.d/50unattended-upgrades", {st_mode=S_IFREG|0644, st_size=1169, ...}) = 0
stat64("/etc/apt/apt.conf.d/10periodic", {st_mode=S_IFREG|0644, st_size=129, ...}) = 0
stat64("/etc/apt/apt.conf.d/00CDMountPoint", {st_mode=S_IFREG|0644, st_size=81, ...}) = 0
getdents(4, /* 0 entries */, 32768)     = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/00CDMountPoint", O_RDONLY|O_LARGEFILE) = 4
read(4, "Acquire::cdrom {\n  mount \"/media"..., 8191) = 81
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/00trustcdrom", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Authentication::TrustCDROM "..., 8191) = 40
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/01autoremove", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT\n{\n  NeverAutoRemove\n  {\n\t\"^f"..., 8191) = 395
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/05aptitude", O_RDONLY|O_LARGEFILE) = 4
read(4, "aptitude::Keep-Unused-Pattern \"^"..., 8191) = 157
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/10periodic", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 129
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/15update-stamp", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Update::Post-Invoke-Success"..., 8191) = 108
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20archive", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Archives::MaxAge \"30\";\nAPT:"..., 8191) = 85
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20auto-upgrades", O_RDONLY|O_LARGEFILE) = 4
read(4, "APT::Periodic::Update-Package-Li"..., 8191) = 80
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/20dbus", O_RDONLY|O_LARGEFILE) = 4
read(4, "// Notify all clients to reload "..., 8191) = 243
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/30autoproxy", O_RDONLY|O_LARGEFILE) = 4
read(4, "Acquire::http::ProxyAutoDetect \""..., 8191) = 87
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/50unattended-upgrades", O_RDONLY|O_LARGEFILE) = 4
read(4, "// Automatically upgrade package"..., 8191) = 1169
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY|O_LARGEFILE) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 255
read(4, "", 8191)                       = 0
close(4)                                = 0
open("/etc/apt/apt.conf.d/99update-notifier", O_RDONLY|O_LARGEFILE) = 4
read(4, "DPkg::Post-Invoke {\"if [ -d /var"..., 8191) = 231
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/etc/apt/apt.conf", {st_mode=S_IFREG|0644, st_size=151, ...}) = 0
open("/etc/apt/apt.conf", O_RDONLY|O_LARGEFILE) = 4
read(4, "Acquire::http::proxy \"http://10."..., 8191) = 151
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=1519310, ...}) = 0
stat64("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=206768, ...}) = 0
stat64("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=12, ...}) = 0
getuid32()                              = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfa277c8) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGWINCH, {0x804ea90, [WINCH], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
ioctl(1, TIOCGWINSZ, 0xbfa27838)        = -1 ENOTTY (Inappropriate ioctl for device)
stat64("/etc/apt/sources.list", {st_mode=S_IFREG|0644, st_size=3604, ...}) = 0
open("/etc/apt/sources.list", O_RDONLY|O_LARGEFILE) = 4
read(4, "# \n# deb cdrom:[Ubuntu-Server 10"..., 8191) = 3604
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/etc/apt/sources.list.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/sources.list.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 4
getdents(4, /* 2 entries */, 32768)     = 32
getdents(4, /* 0 entries */, 32768)     = 0
close(4)                                = 0
gettimeofday({1298380310, 584566}, NULL) = 0
gettimeofday({1298380310, 584670}, NULL) = 0
stat64("/var/lib/apt/lists/partial/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/var/cache/apt/archives/partial/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/lib/apt/lists/lock", O_RDWR|O_CREAT|O_NOFOLLOW, 0640) = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
unlink("/var/lib/apt/lists/partial/de.archive.ubuntu.com_ubuntu_dists_maverick_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_Release.gpg", 0xbfa26edc) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([5, 6])                            = 0
pipe([7, 8])                            = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(8, F_SETFD, FD_CLOEXEC)         = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb732f738) = 4431
fcntl64(5, F_GETFL)                     = 0 (flags O_RDONLY)
fcntl64(5, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
fcntl64(8, F_GETFL)                     = 0x1 (flags O_WRONLY)
fcntl64(8, F_SETFL, O_WRONLY|O_NONBLOCK) = 0
close(6)                                = 0
close(7)                                = 0
select(6, [5], NULL, NULL, NULL)        = 1 (in [5])
read(5, "100 Capabilities\nVersion: 1.2\nPi"..., 64000) = 64
close(5)                                = 0
close(8)                                = 0
kill(4431, SIGINT)                      = 0
waitpid(4431, [{WIFSIGNALED(s) && WTERMSIG(s) == SIGINT}], 0) = 4431
--- SIGCHLD (Child exited) @ 0 (0) ---
open("/var/lib/apt/lists/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 5
getdents(5, /* 35 entries */, 32768)    = 2744
getdents(5, /* 0 entries */, 32768)     = 0
close(5)                                = 0
stat64("/bin/bzip2", {st_mode=S_IFREG|0755, st_size=26064, ...}) = 0
stat64("/usr/bin/lzma", {st_mode=S_IFREG|0755, st_size=100104, ...}) = 0
unlink("/var/lib/apt/lists/partial/de.archive.ubuntu.com_ubuntu_dists_maverick-updates_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick-updates_Release.gpg", 0xbfa26edc) = -1 ENOENT (No such file or directory)
unlink("/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_maverick-security_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_Release.gpg", 0xbfa26edc) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([5, 6])                            = 0
pipe([7, 8])                            = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(8, F_SETFD, FD_CLOEXEC)         = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb732f738) = 4432
fcntl64(5, F_GETFL)                     = 0 (flags O_RDONLY)
fcntl64(5, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
fcntl64(8, F_GETFL)                     = 0x1 (flags O_WRONLY)
fcntl64(8, F_SETFL, O_WRONLY|O_NONBLOCK) = 0
close(6)                                = 0
close(7)                                = 0
select(6, [5], NULL, NULL, NULL)        = 1 (in [5])
read(5, "100 Capabilities\nVersion: 1.2\nPi"..., 64000) = 64
stat64("", 0xbfa26e6c)                  = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_i18n_Translation-de", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_i18n_Translation-de", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_i18n_Translation-de", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_i18n_Translation-de", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([6, 7])                            = 0
pipe([9, 10])                           = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb732f738) = 4433
fcntl64(6, F_GETFL)                     = 0 (flags O_RDONLY)
fcntl64(6, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
fcntl64(10, F_GETFL)                    = 0x1 (flags O_WRONLY)
fcntl64(10, F_SETFL, O_WRONLY|O_NONBLOCK) = 0
close(7)                                = 0
close(9)                                = 0
select(7, [6], NULL, NULL, NULL)        = 1 (in [6])
read(6, "100 Capabilities\nVersion: 1.2\nPi"..., 64000) = 64
stat64("", 0xbfa26e6c)                  = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-de", {st_mode=S_IFREG|0644, st_size=1742260, ...}) = 0
open("/etc/localtime", O_RDONLY)        = 7
fstat64(7, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=2309, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb76da000
read(7, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\10\0\0\0\10\0\0\0\0"..., 4096) = 2309
_llseek(7, -28, [2281], SEEK_CUR)       = 0
read(7, "\nCET-1CEST,M3.5.0,M10.5.0/3\n", 4096) = 28
close(7)                                = 0
munmap(0xb76da000, 4096)                = 0
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_i18n_Translation-de", {st_mode=S_IFREG|0644, st_size=244438, ...}) = 0
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_restricted_i18n_Translation-de", {st_mode=S_IFREG|0644, st_size=9937, ...}) = 0
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_restricted_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_universe_i18n_Translation-de", {st_mode=S_IFREG|0644, st_size=6592582, ...}) = 0
stat64("/var/lib/apt/lists/de.archive.ubuntu.com_ubuntu_dists_maverick_universe_i18n_Translation-en", 0xbfa26e4c) = -1 ENOENT (No such file or directory)
stat64("", 0xbfa26e6c)                  = -1 ENOENT (No such file or directory)
gettimeofday({1298380310, 681117}, NULL) = 0
gettimeofday({1298380310, 681165}, NULL) = 0
select(11, [5 6], [8 10], NULL, {0, 500000}) = 2 (out [8 10], left {0, 499997})
write(10, "601 Configuration\nConfig-Item: A"..., 7275) = 7275
write(8, "601 Configuration\nConfig-Item: A"..., 7010) = 7010
gettimeofday({1298380310, 682692}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380311, 183723}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380311, 684841}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [6], left {0, 324267})
read(6, "102 Status\nURI: http://de.archiv"..., 64000) = 118
gettimeofday({1298380311, 861265}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [6], left {0, 499673})
read(6, "102 Status\nURI: http://de.archiv"..., 64000) = 134
gettimeofday({1298380311, 861807}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [6], left {0, 498753})
read(6, "102 Status\nURI: http://de.archiv"..., 64000) = 111
gettimeofday({1298380311, 863251}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [5], left {0, 495801})
read(5, "102 Status\nURI: http://security."..., 64000) = 125
gettimeofday({1298380311, 867684}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [5], left {0, 499746})
read(5, "102 Status\nURI: http://security."..., 64000) = 141
gettimeofday({1298380311, 868132}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 1 (in [5], left {0, 499561})
read(5, "102 Status\nURI: http://security."..., 64000) = 118
gettimeofday({1298380311, 868771}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380312, 370632}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380312, 871777}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380313, 372886}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380313, 873984}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}) = 0 (Timeout)
gettimeofday({1298380314, 375200}, NULL) = 0
select(7, [5 6], [], NULL, {0, 500000}^C <unfinished ...>


Any ideas what's going on here? I'm not a kernel junkie, so I don't have experience in this. Any help is desirable.

---

### Post by anglican on 2011-02-22
> **ThomasJAndrews said:**
> Have a hyper-V installation of Ubuntu 10.10 which I am working with. Till my attempted installation of adzapper using apt-get, apt-get update and apt-get install worked well with completion times being very short, usually under 10 seconds for small packages. My internet connection is high speed ASL. I am connecting through a local proxy server. Everything else concerning connectivity on my assembly prototype seems to be functioning excellently, that includes wget and browser use. When I now do a apt-get update, it gets stuck on waiting for headers. I did an strace apt-get update, the text of which you can view below:
... snip
Any ideas what's going on here? I'm not a kernel junkie, so I don't have experience in this. Any help is desirable.What exactly did you do to try and install adzapper? I'm thinking specifically about the "Install Python" instruction - which could do some damage. Check your /etc/apt/sources.list file and /etc/apt/sources.list.d directory for recent changes that are causing apt-get to stall.

H

---

### Post by ThomasJAndrews on 2011-02-22
Checked both /etc/apt/sources.list file and /etc/apt/sources.list.d directory immediately after the incident. There was no change in either. Even did an apt-config dump to see what possibly could have changed somewhere, but to no visible avail. I suspect it was the packages adzapper and squid-deb-proxy that caused the calamity by digging into related posts. Removal and purging of either deb packages did nothing to change anything. Well, all said, I've decided to roll back the whole effort and just leave out the conflicting packages that just won't work. Time is something most of us don't have. Thanks for your assistence.

---

