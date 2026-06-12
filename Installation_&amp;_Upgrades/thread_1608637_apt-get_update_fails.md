---
title: "apt-get update fails"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by Der Dafmeister on 2010-10-29
Yesterday, I installed ubuntu 10.10 server edition and today I tried to install some software. First I did:
```
sudo apt-get update
```it's really slow and get  the following errors:

```
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Err http://nl.archive.ubuntu.com maverick Release.gpg
  Connection failed
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-                                             en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-                                             en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-                                             en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-                                             en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en                                             _US
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en
  Connection failed
Ign http://security.ubuntu.com maverick-security Release
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US
  Connection failed
Ign http://security.ubuntu.com maverick-security/main Sources
Ign http://security.ubuntu.com maverick-security/restricted Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/universe Sources/DiffIndex
Ign http://security.ubuntu.com maverick-security/multiverse Sources/DiffIndex
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
  Connection failed
Ign http://security.ubuntu.com maverick-security/main i386 Packages
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US
  Connection failed
Ign http://security.ubuntu.com maverick-security/restricted i386 Packages/DiffIn                                             dex
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
  Connection failed
Ign http://security.ubuntu.com maverick-security/universe i386 Packages
Ign http://security.ubuntu.com maverick-security/multiverse i386 Packages/DiffIn                                             dex
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US
  Connection failed
Err http://security.ubuntu.com maverick-security/main Sources
  Connection failed [IP: 91.189.92.166 80]
Get:2 http://security.ubuntu.com maverick-security/restricted Sources [14B]
Get:3 http://security.ubuntu.com maverick-security/universe Sources [2,599B]
Get:4 http://security.ubuntu.com maverick-security/multiverse Sources [14B]
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
  Connection failed
Err http://security.ubuntu.com maverick-security/main i386 Packages
  Connection failed [IP: 91.189.92.166 80]
Get:5 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B                                             ]
Err http://nl.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
  Connection failed
Err http://security.ubuntu.com maverick-security/universe i386 Packages
  Connection failed [IP: 91.189.92.167 80]
Get:6 http://security.ubuntu.com maverick-security/multiverse i386 Packages [14B                                             ]
Err http://nl.archive.ubuntu.com maverick-updates Release.gpg
  Connection failed
Err http://nl.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
  Connection failed
99% [Waiting for headers]
```My source.list
```

# 
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://nl.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://nl.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://nl.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick universe
deb http://nl.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://nl.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://nl.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://nl.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu maverick partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb http://extras.ubuntu.com/ubuntu maverick main
# deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse


```

Please, can somebody help me?

---

### Post by Der Dafmeister on 2010-10-30
Here is my output when i typed: 
sudo strace apt-get update


Has somebody a suggestion?
```

lose(4)                                = 0
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
open("/etc/apt/apt.conf.d/70debconf", O_RDONLY|O_LARGEFILE) = 4
read(4, "// Pre-configure all packages wi"..., 8191) = 182
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/etc/apt/apt.conf", 0xbfaeb70c) = -1 ENOENT (No such file or directory)
stat64("/var/lib/dpkg/status", {st_mode=S_IFREG|0644, st_size=323679, ...}) = 0
stat64("/usr/bin/dpkg", {st_mode=S_IFREG|0755, st_size=206768, ...}) = 0
stat64("/etc/debian_version", {st_mode=S_IFREG|0644, st_size=12, ...}) = 0
getuid32()                              = 0
ioctl(1, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGWINCH, {0x804ea90, [WINCH], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
ioctl(1, TIOCGWINSZ, {ws_row=24, ws_col=80, ws_xpixel=0, ws_ypixel=0}) = 0
stat64("/etc/apt/sources.list", {st_mode=S_IFREG|0644, st_size=3459, ...}) = 0
open("/etc/apt/sources.list", O_RDONLY|O_LARGEFILE) = 4
read(4, "# \n# deb cdrom:[Ubuntu-Server 10"..., 8191) = 3459
read(4, "", 8191)                       = 0
close(4)                                = 0
stat64("/etc/apt/sources.list.d/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/apt/sources.list.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 4
getdents(4, /* 2 entries */, 32768)     = 32
getdents(4, /* 0 entries */, 32768)     = 0
close(4)                                = 0
gettimeofday({1288423961, 568938}, NULL) = 0
gettimeofday({1288423961, 569001}, NULL) = 0
stat64("/var/lib/apt/lists/partial/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat64("/var/cache/apt/archives/partial/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/var/lib/apt/lists/lock", O_RDWR|O_CREAT|O_NOFOLLOW, 0640) = 4
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETLK, {type=F_WRLCK, whence=SEEK_SET, start=0, len=0}) = 0
unlink("/var/lib/apt/lists/partial/nl.archive.ubuntu.com_ubuntu_dists_maverick_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_Release.gpg", 0xbfaeb04c) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([5, 6])                            = 0
pipe([7, 8])                            = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(8, F_SETFD, FD_CLOEXEC)         = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb74f3738) = 825
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
kill(825, SIGINT)                       = 0
waitpid(825, [{WIFSIGNALED(s) && WTERMSIG(s) == SIGINT}], 0) = 825
--- SIGCHLD (Child exited) @ 0 (0) ---
open("/var/lib/apt/lists/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 5
getdents(5, /* 16 entries */, 32768)    = 1256
getdents(5, /* 0 entries */, 32768)     = 0
close(5)                                = 0
stat64("/bin/bzip2", {st_mode=S_IFREG|0755, st_size=26064, ...}) = 0
stat64("/usr/bin/lzma", 0xbfaeae5c)     = -1 ENOENT (No such file or directory)
unlink("/var/lib/apt/lists/partial/nl.archive.ubuntu.com_ubuntu_dists_maverick-updates_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick-updates_Release.gpg", 0xbfaeb04c) = -1 ENOENT (No such file or directory)
unlink("/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_maverick-security_Release.gpg") = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_Release.gpg", 0xbfaeb04c) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([5, 6])                            = 0
pipe([7, 8])                            = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(8, F_SETFD, FD_CLOEXEC)         = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb74f3738) = 826
fcntl64(5, F_GETFL)                     = 0 (flags O_RDONLY)
fcntl64(5, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
fcntl64(8, F_GETFL)                     = 0x1 (flags O_WRONLY)
fcntl64(8, F_SETFL, O_WRONLY|O_NONBLOCK) = 0
close(6)                                = 0
close(7)                                = 0
select(6, [5], NULL, NULL, NULL)        = 1 (in [5])
read(5, "100 Capabilities\nVersion: 1.2\nPi"..., 64000) = 64
stat64("", 0xbfaeafdc)                  = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_main_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_multiverse_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_restricted_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_maverick-security_universe_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/apt/methods/http", {st_mode=S_IFREG|0755, st_size=55248, ...}) = 0
pipe([6, 7])                            = 0
pipe([9, 10])                           = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(10, F_SETFD, FD_CLOEXEC)        = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb74f3738) = 827
fcntl64(6, F_GETFL)                     = 0 (flags O_RDONLY)
fcntl64(6, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
fcntl64(10, F_GETFL)                    = 0x1 (flags O_WRONLY)
fcntl64(10, F_SETFL, O_WRONLY|O_NONBLOCK) = 0
close(7)                                = 0
close(9)                                = 0
select(7, [6], NULL, NULL, NULL)        = 1 (in [6])
read(6, "100 Capabilities\nVersion: 1.2\nPi"..., 64000) = 64
stat64("", 0xbfaeafdc)                  = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_main_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_multiverse_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_restricted_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_restricted_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_universe_i18n_Translation-en", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/nl.archive.ubuntu.com_ubuntu_dists_maverick_universe_i18n_Translation-en%5fUS", 0xbfaeafbc) = -1 ENOENT (No such file or directory)
stat64("", 0xbfaeafdc)                  = -1 ENOENT (No such file or directory)
gettimeofday({1288423961, 609423}, NULL) = 0
gettimeofday({1288423961, 609480}, NULL) = 0
select(11, [5 6], [8 10], NULL, {0, 500000}) = 2 (out [8 10], left {0, 499992})
write(10, "601 Configuration\nConfig-Item: A"..., 5622) = 5622
write(8, "601 Configuration\nConfig-Item: A"..., 5537) = 5537
gettimeofday({1288423961, 612638}, NULL) = 0
open("/usr/share/locale/locale.alias", O_RDONLY) = 7
fstat64(7, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb789d000
read(7, "# Locale name alias data base.\n#"..., 4096) = 2570
read(7, "", 4096)                       = 0
close(7)                                = 0
munmap(0xb789d000, 4096)                = 0
open("/usr/share/locale/en_US.UTF-8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US.utf8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en_US/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.UTF-8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en.utf8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.UTF-8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US.utf8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.UTF-8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en.utf8/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/apt.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_BLOCK, [WINCH], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb789d000
0% [Working])        = 14]", 14
select(7, [5 6], [], NULL, {0, 500000}) = 2 (in [5 6], left {0, 499995})
read(6, "102 Status\nURI: http://nl.archiv"..., 64000) = 125
read(5, "102 Status\nURI: http://security."..., 64000) = 130
select(7, [5 6], [], NULL, {0, 499995}) = 1 (in [5], left {0, 463287})
read(5, "102 Status\nURI: http://security."..., 64000) = 146
select(7, [5 6], [], NULL, {0, 463287}) = 1 (in [6], left {0, 462626})
read(6, "102 Status\nURI: http://nl.archiv"..., 64000) = 142
select(7, [5 6], [], NULL, {0, 462626}) = 1 (in [6], left {0, 437131})
read(6, "102 Status\nURI: http://nl.archiv"..., 64000) = 109
select(7, [5 6], [], NULL, {0, 437131}) = 1 (in [5], left {0, 434888})
read(5, "102 Status\nURI: http://security."..., 64000) = 116
select(7, [5 6], [], NULL, {0, 434888}^C <unfinished ...>
```

---

