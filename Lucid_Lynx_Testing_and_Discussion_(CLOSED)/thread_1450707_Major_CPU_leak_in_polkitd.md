---
title: "Major CPU leak in polkitd"
date: 2010-04-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DevilInPgh on 2010-04-09
I just upgraded to the Lucid beta last night from Karmic and noticed a huge jump in CPU usage for polkitd.  The CPU usage for this process is consistently between 30% and 40%.  Does anyone have a fix for this?

EDIT: Posting the strace output.  This is just a sample of an unending loop:

```
read(10, "[Mounting, checking, etc. of int"..., 2141) = 385
close(10)                               = 0
gettimeofday({1270828291, 705205}, NULL) = 0
gettimeofday({1270828291, 705266}, NULL) = 0
gettimeofday({1270828291, 705489}, NULL) = 0
gettimeofday({1270828291, 705542}, NULL) = 0
gettimeofday({1270828291, 705708}, NULL) = 0
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
read(9, "[Mounting, checking, etc. of int"..., 4096) = 385
read(9, "", 4096)                       = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 109) = 109
open("/etc/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 110) = 110
open("/var/lib/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 106) = 106
open("/etc/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 111) = 111
open("/var/lib/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 107) = 107
open("/etc/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/var/lib/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 108) = 108
open("/etc/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 116) = 116
open("/var/lib/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/etc/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 113) = 113
open("/var/lib/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 3 entries */, 32768)   = 96
getdents64(9, /* 0 entries */, 32768)   = 0
lstat64("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
gettimeofday({1270828291, 710966}, NULL) = 0
gettimeofday({1270828291, 711034}, NULL) = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 10
read(10, "[Mounting, checking, etc. of int"..., 2141) = 385
close(10)                               = 0
gettimeofday({1270828291, 714117}, NULL) = 0
gettimeofday({1270828291, 714187}, NULL) = 0
gettimeofday({1270828291, 714411}, NULL) = 0
gettimeofday({1270828291, 714460}, NULL) = 0
gettimeofday({1270828291, 714615}, NULL) = 0
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
read(9, "[Mounting, checking, etc. of int"..., 4096) = 385
read(9, "", 4096)                       = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 109) = 109
open("/etc/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 110) = 110
open("/var/lib/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 106) = 106
open("/etc/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 111) = 111
open("/var/lib/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 107) = 107
open("/etc/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/var/lib/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 108) = 108
open("/etc/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 116) = 116
open("/var/lib/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/etc/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 113) = 113
open("/var/lib/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 3 entries */, 32768)   = 96
getdents64(9, /* 0 entries */, 32768)   = 0
lstat64("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
gettimeofday({1270828291, 756962}, NULL) = 0
gettimeofday({1270828291, 757061}, NULL) = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 10
read(10, "[Mounting, checking, etc. of int"..., 2141) = 385
close(10)                               = 0
gettimeofday({1270828291, 757372}, NULL) = 0
gettimeofday({1270828291, 757430}, NULL) = 0
gettimeofday({1270828291, 757654}, NULL) = 0
gettimeofday({1270828291, 757705}, NULL) = 0
gettimeofday({1270828291, 757887}, NULL) = 0
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
read(9, "[Mounting, checking, etc. of int"..., 4096) = 385
read(9, "", 4096)                       = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 109) = 109
open("/etc/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 110) = 110
open("/var/lib/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 106) = 106
open("/etc/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 111) = 111
open("/var/lib/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 107) = 107
open("/etc/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/var/lib/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 108) = 108
open("/etc/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 116) = 116
open("/var/lib/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/etc/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 113) = 113
open("/var/lib/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 3 entries */, 32768)   = 96
getdents64(9, /* 0 entries */, 32768)   = 0
lstat64("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
gettimeofday({1270828291, 771164}, NULL) = 0
gettimeofday({1270828291, 771241}, NULL) = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 10
read(10, "[Mounting, checking, etc. of int"..., 2141) = 385
close(10)                               = 0
gettimeofday({1270828291, 771510}, NULL) = 0
gettimeofday({1270828291, 771570}, NULL) = 0
gettimeofday({1270828291, 771785}, NULL) = 0
gettimeofday({1270828291, 771836}, NULL) = 0
gettimeofday({1270828291, 771999}, NULL) = 0
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
read(9, "[Mounting, checking, etc. of int"..., 4096) = 385
read(9, "", 4096)                       = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 109) = 109
open("/etc/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 110) = 110
open("/var/lib/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 106) = 106
open("/etc/polkit-1/localauthority/20-org.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 111) = 111
open("/var/lib/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 107) = 107
open("/etc/polkit-1/localauthority/30-site.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/var/lib/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 108) = 108
open("/etc/polkit-1/localauthority/50-local.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 116) = 116
open("/var/lib/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 112) = 112
open("/etc/polkit-1/localauthority/90-mandatory.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 2 entries */, 32768)   = 48
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
write(1, "** (process:1278): DEBUG: Droppi"..., 113) = 113
open("/var/lib/polkit-1/localauthority/10-vendor.d", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = 9
getdents64(9, /* 3 entries */, 32768)   = 96
getdents64(9, /* 0 entries */, 32768)   = 0
lstat64("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
gettimeofday({1270828291, 811314}, NULL) = 0
gettimeofday({1270828291, 811414}, NULL) = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 10
read(10, "[Mounting, checking, etc. of int"..., 2141) = 385
close(10)                               = 0
gettimeofday({1270828291, 811726}, NULL) = 0
gettimeofday({1270828291, 811782}, NULL) = 0
gettimeofday({1270828291, 812001}, NULL) = 0
gettimeofday({1270828291, 812052}, NULL) = 0
gettimeofday({1270828291, 812261}, NULL) = 0
getdents64(9, /* 0 entries */, 32768)   = 0
close(9)                                = 0
open("/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla", O_RDONLY|O_LARGEFILE) = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=385, ...}) = 0
read(9, "[Mounting, checking, etc. of int"..., 4096) = 385
```

---

### Post by DevilInPgh on 2010-04-09
Bttt

---

### Post by DevilInPgh on 2010-04-09
bttt again.  Come on, this is a really serious problem with the OS.

---

### Post by chrisccoulson on 2010-04-09
Please be patient. Perhaps nobody knows of a solution? (and you seem to be the only person with this problem)

---

### Post by DevilInPgh on 2010-04-09
Nope, not isolated to me.  Seems to be quite an old problem:
[https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/426556](https://bugs.launchpad.net/ubuntu/+source/policykit/+bug/426556)

---

### Post by kansasnoob on 2010-04-09
I'm getting basically the same thing on my VIA C7 CPU + VIA P4/M800 Graphics box, but not on my Intel Atom 230 + Intel 82945G/GZ Graphics box. So please provide some hardware info.

To gather info:

```
cat /proc/cpuinfo
cat /proc/loadavg
cat /proc/meminfo
free
lspci | grep VGA
```

Sadly I've not found a solution for my VIA box other than running Jaunty, Karmic's X crashes on it :(

---

### Post by cariboo on 2010-04-09
Please don't bump your thread more than once every 24 hours.

---

### Post by DevilInPgh on 2010-04-09
Sorry, was just concerned about a major bug getting bumped off the front page and being lost to the developers.  And it is a major bug.

---

### Post by splicerr on 2010-04-09
> **DevilInPgh said:**
> Sorry, was just concerned about a major bug getting bumped off the front page and being lost to the developers.  And it is a major bug.

There are at least a hundred people with 'major bugs' here.  Should they all bump their thread every hour? Your behavior is unacceptable. You won't see many developers here anyway and the proper way to make sure your bug is not getting lost to the developers is to file a bug report at launchpad.

---

### Post by clhsharky on 2010-04-09
HI DevilInPgh

Report a bug if you want the Devs to see your problem.


Sharky

Stating your concern here is not filing a bug.

---

### Post by DevilInPgh on 2010-04-09
> **clhsharky said:**
> HI DevilInPgh

Report a bug if you want the Devs to see your problem.


Sharky

Stating your concern here is not filing a bug.

K, thx.

---

### Post by kansasnoob on 2010-04-09
And still no output from my request in post #6?

If you intend to only complain how do you expect to improve either Ubuntu or your experience with Ubuntu?

We are not mind readers! Sometimes additional info is essential!

---

### Post by DevilInPgh on 2010-04-10
> **kansasnoob said:**
> And still no output from my request in post #6?

If you intend to only complain how do you expect to improve either Ubuntu or your experience with Ubuntu?

We are not mind readers! Sometimes additional info is essential!

Sorry that I have a busy life on Fridays and tried out a few things myself before going out (like installing other policykit packages that should have been installed).

Anyways, the readouts are at these pastebin links:
cpuinfo: [http://pastebin.ubuntu.com/411935/](http://pastebin.ubuntu.com/411935/)
meminfo: [http://pastebin.ubuntu.com/411937/](http://pastebin.ubuntu.com/411937/) (note: I had just killed polkitd to release the memory it was hogging, but it has respawned and will eventually take up that memory again)
loadavg: ```
2.37 2.49 2.43 5/245 7052
```

free: [http://pastebin.ubuntu.com/411938/](http://pastebin.ubuntu.com/411938/)
lspci | grep VGA: ```
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
```

I hope this helps.

---

### Post by DevilInPgh on 2010-04-11
bttt (it's been more than 24 hours, OK?!)

---

### Post by haylocki on 2010-04-15
Hi,

I also had this problem with my laptop after upgrading to Lucid.

I think your problem is caused by one (or more) of the files in your home directory, that wasn't upgraded properly when you upgraded your system.

Which file it is I do not know.

One thing you could try to prove this, is to create a new user, then reboot your system. Then log in as the new user. Hopefully if the problem is caused by a file in your original users home directory it should no longer be present.

HTH, Ian

---

### Post by DevilInPgh on 2010-04-17
Thanks.  That's what I was asking for.  And you are correct, setting up a second account solves the problem.  Now to go through each and every one of these to find the problem maker.

EDIT:  Well, whichever of the hidden directories in the Home directory it was, it's fixed now.  Thx for the solution.

---

