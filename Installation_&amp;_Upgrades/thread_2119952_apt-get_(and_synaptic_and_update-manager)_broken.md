---
title: "apt-get (and synaptic and update-manager) broken"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by garfieldpbj on 2013-02-25
Hi

I have a problem, I can't update anything. I noticed this because update-manager told me it  was broken. 

If I do a normal sudo apt-get update, it do all the checks and retrieves the needed, but in the end when it says "reading package list X %", where the X is changing, it dies at 96 % with no error (I am not completely sure whether it is excactly "reading package list" it says, this is the expected translation of the Danish text I see).

How to fix this? 

I have tried all "standard" cleaning, found when googling..

---

### Post by matt_symes on 2013-02-25
Hi

Try

```
sudo rm -vf /var/lib/apt/lists/*
```
```

sudo apt-get update
```

Kind regards

---

### Post by garfieldpbj on 2013-02-25
> **matt_symes said:**
> Hi

Try

```
sudo rm -vf /var/lib/apt/lists/*
```
```

sudo apt-get update
```

Kind regards

Thank you for the suggestion; I tried that before also, and the problem is not solved. (I do remove files with the first command.)

---

### Post by matt_symes on 2013-02-25
Hi

That's rather odd. With no error message as well. Lets see if we can see where it's failiing

From the terminal

Move to home directory
```
cd
```

get an strace
```
sudo strace -o apt apt-get update
```

get the last 200 lines.
```
tail -n 200 apt > upload
```

Copy the contents of the file upload into your next post. That may give some indication of what is happening.

Kind regards

---

### Post by schragge on 2013-02-25
If you have some data in */var/lib/apt/lists/partial*, try to remove them too
```

sudo rm -vf /var/lib/apt/lists/partial/*
sudo apt-get update

```

If this doesn't help, please post the output of
```

sudo tail /var/log/apt/term.log|tr \\r \\n

```

---

### Post by garfieldpbj on 2013-02-25
> **matt_symes said:**
> Hi

That's rather odd. With no error message as well. Lets see if we can see where it's failiing

From the terminal

Move to home directory
```
cd
```get an strace
```
sudo strace -o apt apt-get update
```get the last 200 lines.
```
tail -n 200 apt > upload
```Copy the contents of the file upload into your next post. That may give some indication of what is happening.

Kind regards

Hi again 

The output: [INDENT]```

stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-da%5fDK.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
close(6)                                = 0
write(1, "\rIndl\303\246ser pakkelisterne... 95%\r", 32) = 32
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
read(6, "Package: nvidia-173\nDescription-"..., 32768) = 4028
read(6, "", 28740)                      = 0
write(1, "\rIndl\303\246ser pakkelisterne... 95%\r", 32) = 32
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
close(7)                                = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=4028, ...}) = 0
close(6)                                = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da%5fDK.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
close(6)                                = 0
write(1, "\rIndl\303\246ser pakkelisterne... 95%\r", 32) = 32
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
read(6, "Package: aiccu\nDescription-md5: "..., 32768) = 32768
write(1, "\rIndl\303\246ser pakkelisterne... 95%\r", 32) = 32
stat64("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
open("/var/lib/apt/lists/dk.archive.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
close(7)                                = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=217793, ...}) = 0
read(6, "o it.\n\nPackage: jabberd2\nDescrip"..., 32200) = 32200
read(6, "lobus Toolkit is an open source "..., 32622) = 32622
read(6, " meta-package, which will ensure"..., 32160) = 32160
read(6, " use the MySQL Native Driver.\n ."..., 32309) = 32309
read(6, "nt, resolution, and notification"..., 31993) = 31993
gettimeofday({1361798595, 114470}, NULL) = 0
read(6, "k activity and signal strength;\n"..., 32203) = 23741
read(6, "", 8462)                       = 0
close(6)                                = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
open("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
close(6)                                = 0
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
open("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
read(6, "Package: acroread\nPriority: extr"..., 32768) = 21765
read(6, "", 11003)                      = 0
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
open("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
close(7)                                = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=21765, ...}) = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_InRelease", 0xbfe38930) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release", {st_mode=S_IFREG|0644, st_size=7078, ...}) = 0
open("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_Release", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
dup(7)                                  = 8
fcntl64(8, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat64(8, {st_mode=S_IFREG|0644, st_size=7078, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb58e7000
_llseek(8, 0, [0], SEEK_CUR)            = 0
read(8, "Origin: Canonical\nLabel: Partner"..., 4096) = 4096
read(8, "87cc6f649bec5312a3e5a93f79d6c76f"..., 4096) = 2982
read(8, "", 4096)                       = 0
close(8)                                = 0
munmap(0xb58e7000, 4096)                = 0
close(7)                                = 0
close(6)                                = 0
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da%5fDK.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_i18n_Translation-en", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
open("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
close(6)                                = 0
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
open("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
read(6, "Package: unity-lens-sshsearch\nPr"..., 32768) = 32768
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
open("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
close(7)                                = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=35407, ...}) = 0
read(6, "-apport, python-gobject-2, gir1."..., 32493) = 2639
read(6, "", 29854)                      = 0
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_InRelease", 0xbfe38930) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release", {st_mode=S_IFREG|0644, st_size=11875, ...}) = 0
open("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
dup(7)                                  = 8
fcntl64(8, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat64(8, {st_mode=S_IFREG|0644, st_size=11875, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb58e7000
_llseek(8, 0, [0], SEEK_CUR)            = 0
read(8, "Origin: LP-PPA-app-review-board\n"..., 4096) = 4096
read(8, "     8776 main/binary-armel/Pack"..., 4096) = 4096
read(8, "b8bf98f78bf5f4be0a523869ac55c1f9"..., 4096) = 3683
read(8, "", 4096)                       = 0
close(8)                                = 0
munmap(0xb58e7000, 4096)                = 0
close(7)                                = 0
close(6)                                = 0
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da%5fDK.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-da%5fDK", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en.gz", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en", 0xbfe392b0) = -1 ENOENT (No such file or directory)
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
open("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
close(6)                                = 0
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
open("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 6
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
read(6, "Package: firefox-mozilla-build\nV"..., 32768) = 2788
read(6, "", 29980)                      = 0
write(1, "\rIndl\303\246ser pakkelisterne... 96%\r", 32) = 32
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
open("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_main_binary-i386_Packages", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
fstat64(7, {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
close(7)                                = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
fstat64(6, {st_mode=S_IFREG|0644, st_size=2788, ...}) = 0
stat64("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_InRelease", {st_mode=S_IFREG|0644, st_size=1891, ...}) = 0
open("/var/lib/apt/lists/downloads.sourceforge.net_project_ubuntuzilla_mozilla_apt_dists_all_InRelease", O_RDONLY|O_LARGEFILE) = 7
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
dup(7)                                  = 8
fcntl64(8, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat64(8, {st_mode=S_IFREG|0644, st_size=1891, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb58e7000
_llseek(8, 0, [0], SEEK_CUR)            = 0
read(8, "-----BEGIN PGP SIGNED MESSAGE---"..., 4096) = 1891
_llseek(5, 26214399, [26214399], SEEK_SET) = 0
write(5, "\0", 1)                       = 1
mremap(0xb58e8000, 25165824, 26214400, MREMAP_MAYMOVE) = 0xb3fe7000
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
```[/INDENT]

---

### Post by schragge on 2013-02-25
> var/lib/apt/lists/downloads.sourceforge.net
Wait, what's in your */etc/apt/sources.list*? *sourceforge.net* usually doesn't host deb repositories
```

grep ^[^#] /etc/apt/sources.list /etc/apt/sources.list.d/*

```

[highlight]Update.[/highlight]
Oh I see. [Ubuntuzilla does](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation). Still, it looks weird to me. Try to remove ubuntuzilla from your sources.list

---

### Post by garfieldpbj on 2013-02-25
> **schragge said:**
> If you have some data in */var/lib/apt/lists/partial*, try to remove them too
```

sudo rm -vf /var/lib/apt/lists/partial/*
sudo apt-get update

```

If this doesn't help, please post the output of
```

sudo tail /var/log/apt/term.log|tr \\r \\n

```

Hi..

Still not working.. output:

[INDENT]
2013-02-22 13:06:54 (1,74 MB/s) - 'jdk-7u15-linux-i586.tar.gz' gemt [97486991/97486991]



Download done.

Removing outdated cached downloads...

fjernede 'jdk-7u13-linux-i586.tar.gz'

Oracle JDK 7 installed

Oracle JRE 7 browser plugin installed

Sætter openssl (1.0.1-4ubuntu5.6) op...

Behandler udløsere for menu ...

Log ended: 2013-02-22  13:07:05 [/INDENT]

---

### Post by garfieldpbj on 2013-02-25
> **schragge said:**
> Wait, what's in your */etc/apt/sources.list*? *sourceforge.net* usually doesn't host deb repositories
```

grep ^[^#] /etc/apt/sources.list /etc/apt/sources.list.d/*

```

I am not sure what's in my source list - a lot have been added from time to time..:[INDENT]```

/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) natty-updates main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) natty-security main restricted
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise main restricted
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates main restricted
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise universe
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates universe
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise multiverse
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-updates multiverse
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security main restricted
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security main restricted
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security universe
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security universe
/etc/apt/sources.list:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security multiverse
/etc/apt/sources.list:deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) precise-security multiverse
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
/etc/apt/sources.list:deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) precise main
/etc/apt/sources.list:deb [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt) all main # slået fra under opgradering til oneiric
/etc/apt/sources.list:deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # slået fra under opgradering til oneiric
/etc/apt/sources.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
/etc/apt/sources.list:deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
/etc/apt/sources.list:deb [http://www.duinsoft.nl/pkg](http://www.duinsoft.nl/pkg) debs all #java
/etc/apt/sources.list.d/chromium-daily-ppa-natty.list:deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/chromium-daily-ppa-natty.list:deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/chromium-daily-ppa-natty.list.save:deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/chromium-daily-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/dlecan-openjdk-natty.list.save:deb-src [http://ppa.launchpad.net/dlecan/openjdk/ubuntu](http://ppa.launchpad.net/dlecan/openjdk/ubuntu) natty main
/etc/apt/sources.list.d/glasen-intel-driver-precise.list:deb [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) precise main
/etc/apt/sources.list.d/glasen-intel-driver-precise.list:deb-src [http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu) precise main
/etc/apt/sources.list.d/google-chrome.list:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/google-chrome.list.save:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/home_dtufys.sources.list:deb [http://download.opensuse.org/repositories/home:/dtufys/xUbuntu_12.04](http://download.opensuse.org/repositories/home:/dtufys/xUbuntu_12.04) /
/etc/apt/sources.list.d/home_dtufys.sources.list.save:deb [http://download.opensuse.org/repositories/home:/dtufys/xUbuntu_12.04](http://download.opensuse.org/repositories/home:/dtufys/xUbuntu_12.04) /
/etc/apt/sources.list.d/mendeleydesktop.list:deb [http://download.mendeley.com/apt/](http://download.mendeley.com/apt/) stable main
/etc/apt/sources.list.d/mendeleydesktop.list.save:deb [http://download.mendeley.com/apt/](http://download.mendeley.com/apt/) stable main
/etc/apt/sources.list.d/opera.list:deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
/etc/apt/sources.list.d/opera.list.save:deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
/etc/apt/sources.list.d/shutter-ppa-precise.list:deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
/etc/apt/sources.list.d/shutter-ppa-precise.list:deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
/etc/apt/sources.list.d/shutter-ppa-precise.list.save:deb [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
/etc/apt/sources.list.d/shutter-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/shutter/ppa/ubuntu](http://ppa.launchpad.net/shutter/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tiheum-equinox-natty.list:deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/tiheum-equinox-natty.list:deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/tiheum-equinox-natty.list.save:deb [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/tiheum-equinox-natty.list.save:deb-src [http://ppa.launchpad.net/tiheum/equinox/ubuntu](http://ppa.launchpad.net/tiheum/equinox/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list:deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list:deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list.save:deb [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/ubuntu-mozilla-daily-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/webupd8team-java-precise.list.save:deb-src [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-natty.list:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/xorg-edgers-ppa-natty.list:deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/xorg-edgers-ppa-natty.list.save:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/xorg-edgers-ppa-natty.list.save:deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) oneiric main # slået fra under opgradering til oneiric
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list:deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:deb [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/xorg-edgers-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) precise main
```
[/INDENT]

---

### Post by schragge on 2013-02-25
Try to remove (or comment out) the ubuntuzilla line from your /etc/apt/sources.list
```

sudo sed -i '/sourceforge/s/^/#/' /etc/apt/sources.list

```

---

### Post by matt_symes on 2013-02-25
Hi

it going bang when parsing the list from this site: downloads.sourceforge.net

You have repos for maverick, natty, oneric and precise. Do you really need these below ?

```

deb http://downloads.sourceforge.net/pro...la/mozilla/apt all main 
deb http://dk.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/dlecan/openjdk/ubuntu natty main
deb http://dl.google.com/linux/chrome/deb/ stable main # slået fra under opgradering til oneiric
deb http://dl.google.com/linux/chrome/deb/ stable main # slået fra under opgradering til oneiric
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
``` Remove them and try updating again.

What does this mean ?

> slået fra under opgradering til oneiricIt may be worth increasing you APTCache limit as well.

Kind regards

---

### Post by garfieldpbj on 2013-02-25
> **schragge said:**
> Try to remove (or comment out) the ubuntuzilla line from your /etc/apt/sources.list
```

sudo sed -i '/sourceforge/s/^/#/' /etc/apt/sources.list

```

That solved the problem! 

Thank you.. 

Just strange that there was no error message..

---

### Post by garfieldpbj on 2013-02-25
> **matt_symes said:**
> Hi

it going bang when parsing the list from this site: downloads.sourceforge.net

You have repos for maverick, natty, oneric and precise. Do you really need these below ?

```

deb http://downloads.sourceforge.net/pro...la/mozilla/apt all main 
deb http://dk.archive.ubuntu.com/ubuntu/ natty-updates main restricted
deb http://security.ubuntu.com/ubuntu natty-security main restricted
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/dlecan/openjdk/ubuntu natty main
deb http://dl.google.com/linux/chrome/deb/ stable main # slået fra under opgradering til oneiric
deb http://dl.google.com/linux/chrome/deb/ stable main # slået fra under opgradering til oneiric
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases) slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/tiheum/equinox/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/ubuntu-mozi...ily/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu oneiric main # slået fra under opgradering til oneiric
``` Remove them and try updating again.

What does this mean ?

It may be worth increasing you APTCache limit as well.

Kind regards

Hi

"slået fra under opgradering til oneiric" = "disabled during upgrade to oneiric"

I do probably not need all the repositories, but as explained, I think they are automatically "duplicated" during upgrade? 

How do I increase the APTcache? And is it stille necessary?

/Peter

---

### Post by matt_symes on 2013-02-25
Hi

If you have a lot of sources and hence packages you can run out of memory and apt will fail.

Personally i would remove those old sources from my files.

If you keep adding sources though at some point you will need to increase the Cache level.

You can do that by running this command. Copy and paste into the terminal.

```
echo 'APT::Cache-Limit "40000000";' | sudo tee -a /etc/apt/apt.conf
```

Kind regards

---

### Post by garfieldpbj on 2013-02-26
> **matt_symes said:**
> Hi

If you have a lot of sources and hence packages you can run out of memory and apt will fail.

Personally i would remove those old sources from my files.

If you keep adding sources though at some point you will need to increase the Cache level.

You can do that by running this command. Copy and paste into the terminal.

```
echo 'APT::Cache-Limit "40000000";' | sudo tee -a /etc/apt/apt.conf
```

Kind regards

Thank you.. 

I will try to remove something which I am sure not is needed :-)

---

