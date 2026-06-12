---
title: "multi-arch installation fails when version dismatch"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by chenze on 2022-09-07
It seems if we want to install multiple architectures of a package, the versions of that package must be exactly matched.

For example, in the latest Ubuntu 18.04, libsystemd0 of x86_64 has a different version than ARM64. So even though libsystemd0 is "Multi-Arch: same", the installation fails for the ARM64 as the 2nd arch.

(By the way, just a few weeks ago, the libsystemd0 of x86_64 and ARM64 has the exactly same version but recently "Primary apt source" gets an update, making the x86_64 has a greater version than ARM64)

x86_64
```
# aptitude show libsystemd0:amd64
Version: 237-3ubuntu10.54
State: installed
Multi-Arch: same
```

ARM64
```
# aptitude show libsystemd0:arm64
Version: 237-3ubuntu10.53
State: not installed
Multi-Arch: same
```

Error happens when trying to install ARM64:
```

# aptitude install libsystemd0:arm64
The following NEW packages will be installed:
  liblz4-1:arm64{a} liblzma5:arm64{a} libsystemd0:arm64{b} 
0 packages upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 303 kB of archives. After unpacking 1071 kB will be used.
The following packages have unmet dependencies:
 libsystemd0 : Breaks: libsystemd0:arm64 (!= 237-3ubuntu10.54) but 237-3ubuntu10.53 is to be installed
 libsystemd0:arm64 : Breaks: libsystemd0 (!= 237-3ubuntu10.53) but 237-3ubuntu10.54 is installed
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     libsystemd0:arm64 [Not Installed] 
```


It is hard to keep every packages in the same version for all the architectures, because in the current deployment of packages, Ubuntu(/etc/apt/sources.list) uses "Primary(archive.ubuntu.com)" for x86, and "Ports (ports.ubuntu.com)" for ARMHF/ARM64.

Do we have any solution to above problem? I tried to find a single package source with both x86_64 and ARM64 but couldn't find any.

---

