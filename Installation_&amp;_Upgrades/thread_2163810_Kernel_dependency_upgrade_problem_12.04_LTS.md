---
title: "Kernel dependency upgrade problem 12.04 LTS"
date: 2013-07-19
forum: Installation &amp; Upgrades
---

### Post by mbze430 on 2013-07-19
I can't seem to get my apt-get to upgrade to new kernels

[SIZE=3]**apt-get upgrade**[/SIZE]
> The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.41.49) but 3.2.0.49.59 is installed
                     Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.49.59 is installed
 linux-headers-generic : Depends: linux-headers-3.2.0-41-generic but it is not installed
E: Unmet dependencies. Try using -f.


[SIZE=3]**apt-get -f install**[/SIZE]

> Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.41.49); however:
  Version of linux-image-generic-pae on system is 3.2.0.49.59.
 linux-generic-pae depends on linux-headers-generic-pae (= 3.2.0.41.49); however:
  Version of linux-headers-generic-pae on system is 3.2.0.49.59.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.2.0-41-generic; however:
  Package linux-headers-3.2.0-41-generic is not installed.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-generic-pae
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

[SIZE=3]**df -h**[/SIZE]
> 
Filesystem                   Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu1204-root   12G  2.6G  8.0G  25% /
udev                         180M  4.0K  180M   1% /dev
tmpfs                         75M  252K   75M   1% /run
none                         5.0M     0  5.0M   0% /run/lock
none                         187M     0  187M   0% /run/shm
/dev/sda1                    228M   71M  145M  33% /boot

[SIZE=3]**dpkg -l | grep linux-image-**[/SIZE]


> 
ii linux-image-3.2.0-40-generic-pae 3.2.0-40.64 Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii linux-image-3.2.0-41-generic-pae 3.2.0-41.66 Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii linux-image-3.2.0-49-generic-pae 3.2.0-49.75 Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii linux-image-generic-pae 3.2.0.49.59 Generic Linux kernel image

[SIZE=3]**dpkg -l |grep linux-headers-**[/SIZE]
> 
johnny@ubuntu1204:~$ dpkg -l |grep linux-headers-
                                               ii  linux-headers-3.2.0-29                         3.2.0-29.46                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-29-generic-pae             3.2.0-29.46                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-36                         3.2.0-36.57                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-36-generic-pae             3.2.0-36.57                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-37                         3.2.0-37.58                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-37-generic-pae             3.2.0-37.58                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-38                         3.2.0-38.61                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-38-generic-pae             3.2.0-38.61                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-39                         3.2.0-39.62                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-39-generic-pae             3.2.0-39.62                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-40                         3.2.0-40.64                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-40-generic-pae             3.2.0-40.64                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-41                         3.2.0-41.66                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-41-generic-pae             3.2.0-41.66                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-44                         3.2.0-44.69                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic-pae             3.2.0-44.69 Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49                         3.2.0-49.75                                  Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-49-generic                 3.2.0-49.75                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
ii  linux-headers-3.2.0-49-generic-pae             3.2.0-49.75                                  Linux kernel headers for version 3.2.0 on 32 bit x86 SMP
iU  linux-headers-generic                          3.2.0.41.49                                  Generic Linux kernel headers
ii  linux-headers-generic-pae                      3.2.0.49.59                                  Generic Linux kernel headers


---

### Post by newbie-user on 2013-07-19
To upgrade to newer kernels:
```

apt-get dist-upgrade

```

---

