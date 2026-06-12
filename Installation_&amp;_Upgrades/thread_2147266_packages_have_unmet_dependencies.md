---
title: "packages have unmet dependencies"
date: 2013-05-21
forum: Installation &amp; Upgrades
---

### Post by giacall99 on 2013-05-21
Hi to all dear experts.
I'm new at this forum... so.. sorry for my english... i know is a little bit poor...

I need some idea..
I've a virtual installation of Ubuntu server 12.04.2 LTS on a VMWARE server..

```

root@jodomail:/# cat /etc/issue
Ubuntu 12.04.2 LTS \n \l

```

This server work as a server mail (postfix + dovecot + horde + postfixadmin) in a test environment... And works fine

Yesterday.. I rty to install samba server through apt-get

```

root@jodomail:/# apt-get install samba

```

and i receive the following error:

```

root@jodomail:/# apt-get install samba
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.41.49) but 3.2.0.43.51 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.43.51 is to be installed
 samba : Depends: samba-common (= 2:3.6.3-2ubuntu2.6) but it is not going to be installed
         Depends: libwbclient0 (= 2:3.6.3-2ubuntu2.6) but it is not going to be installed
         Depends: libtalloc2 (>= 2.0.4~git20101213) but it is not going to be installed
         Depends: libtdb1 (>= 1.2.7+git20101214) but it is not going to be installed
         Depends: update-inetd but it is not going to be installed
         Depends: samba-common-bin but it is not going to be installed
         Recommends: tdb-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

I've got free space under /boot

```

root@jodomail:/# df -h
Filesystem                    Size  Used Avail Use% Mounted on
/dev/mapper/jodomailsrv-root  242G  7.7G  222G   4% /
udev                          2.4G  4.0K  2.4G   1% /dev
tmpfs                         959M  276K  959M   1% /run
none                          5.0M     0  5.0M   0% /run/lock
none                          2.4G     0  2.4G   0% /run/shm
/dev/sda1                     228M   49M  168M  23% /boot

```

and the current kernel in use is 

```

root@jodomail:/# uname -a
Linux jodomail 3.2.0-43-generic-pae #68-Ubuntu SMP Wed May 15 03:55:10 UTC 2013 i686 i686 i386 GNU/Linux

```

also the output of dpkg --list | grep linux-image is

```

root@jodomail:/# dpkg --list | grep linux-image
rc  linux-image-3.2.0-23-generic-pae   3.2.0-23.36                                         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae   3.2.0-32.51                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae   3.2.0-33.52                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae   3.2.0-34.53                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae   3.2.0-35.55                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-36-generic-pae   3.2.0-36.57                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae   3.2.0-37.58                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic-pae   3.2.0-38.61                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic-pae   3.2.0-39.62                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-40-generic-pae   3.2.0-40.64                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae   3.2.0-43.68                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae            3.2.0.43.51                                         Generic Linux kernel image


```

there is someone that could help me to solve this issue??

Thank's in advance

---

### Post by dino99 on 2013-05-21
you does not more than the 2 latest good working kernels installed (purge the others). Each kernel has : 2 headers + 1 or 2 image (some have image-extras)
these "unmet" dependencies are often due to some version conflicts: for example, when non genuine archive(s) is/are added (like ppa(s)). So you you have some in use, purge them and re-update to finally try again the upgrading/installation.

---

### Post by giacall99 on 2013-05-21
> **dino99 said:**
> you does not more than the 2 latest good working kernels installed (purge the others). Each kernel has : 2 headers + 1 or 2 image (some have image-extras)
these "unmet" dependencies are often due to some version conflicts: for example, when non genuine archive(s) is/are added (like ppa(s)). So you you have some in use, purge them and re-update to finally try again the upgrading/installation.

Hi Dino.. Thank for replay..

I try to purge the first old kernel linux-image-3.2.0-23-generic-pae but i receive the same error:

```


root@jodomail:/# apt-get purge linux-image-3.2.0-23-generic-pae
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.41.49) but 3.2.0.43.51 is to be installed
                     Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.43.51 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@jodomail:/#


```

I'm making some mistake??

---

### Post by giacall99 on 2013-05-22
OK... i purge all the old kernel installed whit 


```
dpkg --purge linux-image-3.2.0-33-generic-pae
```



 Now the situation is:

uname -r
```

Linux jodomail 3.2.0-43-generic-pae #68-Ubuntu SMP Wed May 15 03:55:10 UTC 2013 i686 i686 i386 GNU/Linux
```


dpkg --list | grep linux-image
```

ii  linux-image-3.2.0-40-generic-pae   3.2.0-40.64                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-43-generic-pae   3.2.0-43.68                                         Linux kernel image for version 3.2.0 on 32 bit x86 SMP

```

If i try to upgrade by apt with

apt-get upgrade i receive

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.41.49) but it is not installed
                     Depends: linux-headers-generic-pae (= 3.2.0.41.49) but 3.2.0.43.51 is installed
E: Unmet dependencies. Try using -f.

```

But.. i don't have the 3.2.0.41 installed...

---

### Post by giacall99 on 2013-05-22
I try to download the 3.2.0.41..

But installing it i receive

```
root@jodomail:/home/calloni# dpkg --install  linux-server_3.2.0.41.49_i386.deb
(Reading database ... 142163 files and directories currently installed.)
Preparing to replace linux-server 3.2.0.41.49 (using linux-server_3.2.0.41.49_i386.deb) ...
Unpacking replacement linux-server ...
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-server
root@jodomail:/home/calloni#
```

---

### Post by giacall99 on 2013-05-23
Nobody else have some idea and/or suggestion??

---

