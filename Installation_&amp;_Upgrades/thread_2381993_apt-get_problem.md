---
title: "apt-get problem"
date: 2018-01-07
forum: Installation &amp; Upgrades
---

### Post by clearski on 2018-01-07
Hi, everyone.

I've a problem with one of my machines running 14.04.5 Server. Suddenly, after I updated the local repository and tried to upgrade the packages, here's what I got:

```
$** sudo apt-get upgrade -s**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```

```
$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  anacron
The following packages will be REMOVED:
  accountsservice apparmor console-setup cron dbus dmsetup eject
  friendly-recovery grub-common grub-gfxpayload-lists grub-pc grub-pc-bin
  grub2-common initramfs-tools initramfs-tools-bin kbd
  language-selector-common libdevmapper1.02.1 libpam-systemd libparted0debian1
  linux-image-3.13.0-95-generic linux-image-extra-3.13.0-95-generic mountall
  parted plymouth plymouth-theme-ubuntu-text policykit-1 systemd-services
  ubuntu-minimal ubuntu-standard upstart ureadahead
The following NEW packages will be installed:
  anacron
0 upgraded, 1 newly installed, 32 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 26.2 kB of archives.
After this operation, 226 MB disk space will be freed.
Do you want to continue? [Y/n] 
```

Canceled and tried to install anacron myself:

```
$ **sudo apt-get install anacron**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apparmor : Depends: initramfs-tools but it is not going to be installed or
                     linux-initramfs-tool
 console-setup : Depends: initramfs-tools (>= 0.85eubuntu12) but it is not going to be installed
 dmsetup : Depends: initramfs-tools but it is not going to be installed
 kbd : Depends: initramfs-tools but it is not going to be installed
 linux-image-3.13.0-95-generic : Depends: initramfs-tools (>= 0.36ubuntu6) but it is not going to be installed
 plymouth : Depends: initramfs-tools but it is not going to be installed
 ubuntu-minimal : Depends: initramfs-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Since the machine it's a server, reinstalling everything right now is not my first choice, as I need time to reconfigure all services and migrate data, so I am looking for a way to fix this.

Any ideas?

---

### Post by Xian on 2018-01-07
Couple of commands you may want to run to see how it plays out:

$ sudo apt-get dist-upgrade -s

What does this yield for output?


Then :

$ sudo apt-mark hold [COLOR=#000000][FONT=&amp]anacron
$ [/FONT][/COLOR]sudo apt-get upgrade -s

If not satisfactory just revert with:
$ sudo apt-mark unhold [COLOR=#000000]anacron[/COLOR]

---

### Post by clearski on 2018-01-08
Thank you and I am sorry for the late answer. Here's the result of running the suggested commands:

```
$ sudo apt-get dist-upgrade -s
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```

```
$ sudo apt-mark hold anacron
anacron set on hold.
```

```
$ sudo apt-get upgrade -s
Reading package lists... Done
Building dependency tree      
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
E: Unmet dependencies. Try using -f.
```

```
$ sudo apt-mark unhold anacron
anacron was already not hold.
```

It seems that anacron was not on hold because for some reason (of which I am unaware) it is not installed:

```
$ sudo find / -type f -iname "*anacron*" 2>/dev/null
/usr/share/augeas/lenses/dist/anacron.aug
/usr/share/augeas/lenses/dist/tests/test_anacron.aug
/usr/share/doc/cron/README.anacron
```

So we're back here:

```
$ sudo apt-get install anacron
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
apparmor : Depends: initramfs-tools but it is not going to be installed or
linux-initramfs-tool
console-setup : Depends: initramfs-tools (>= 0.85eubuntu12) but it is not going to be installed
dmsetup : Depends: initramfs-tools but it is not going to be installed
kbd : Depends: initramfs-tools but it is not going to be installed
linux-image-3.13.0-95-generic : Depends: initramfs-tools (>= 0.36ubuntu6) but it is not going to be installed
plymouth : Depends: initramfs-tools but it is not going to be installed
ubuntu-minimal : Depends: initramfs-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by ian-weisser on 2018-01-08
You need to figure out why  initramfs-tool won't install.

Please show us the complete output from:
```
sudo apt-get install initramfs-tools
```

If you read all the error messages line-by-line, you will see that all the others are simply a cascade of 'failed-to-install' because of initramfs-tools.

---

### Post by clearski on 2018-01-08
Yes. And initramfs-tools and initramfs-tools-bin won't install, too.

```
$ sudo apt-get install initramfs-tools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 initramfs-tools : Depends: initramfs-tools-bin (>= 0.103ubuntu4.10) but it is not going to be installed
                   Depends: initramfs-tools-bin (< 0.103ubuntu4.10.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


$ sudo apt-get install initramfs-tools-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 apparmor : Depends: initramfs-tools but it is not going to be installed or
                     linux-initramfs-tool
 console-setup : Depends: initramfs-tools (>= 0.85eubuntu12) but it is not going to be installed
 dmsetup : Depends: initramfs-tools but it is not going to be installed
 kbd : Depends: initramfs-tools but it is not going to be installed
 linux-image-3.13.0-95-generic : Depends: initramfs-tools (>= 0.36ubuntu6) but it is not going to be installed
 plymouth : Depends: initramfs-tools but it is not going to be installed
 ubuntu-minimal : Depends: initramfs-tools but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

It's really weird since I didn't mess with these, always apt-get updated && upgraded.

---

### Post by Bashing-om on 2018-01-08
clearski; Hello -

Maybe best to do a bit of sleuthing :
show us:
```

apt policy initramfs-tools initramfs-tools-bin linux-initramfs-tool

```

where all versions that are installed should be the same as the target .

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by clearski on 2018-01-08
Absolutely. Here's the result:

```
$ sudo apt-cache policy initramfs-tools initramfs-tools-bin linux-initramfs-tool
initramfs-tools:
  Installed: 0.103ubuntu4.9
  Candidate: 0.103ubuntu4.10
  Version table:
     0.103ubuntu4.10 0
        500 http://mirrors.digitalocean.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 0.103ubuntu4.9 0
        100 /var/lib/dpkg/status
     0.103ubuntu4 0
        500 http://mirrors.digitalocean.com/ubuntu/ trusty/main amd64 Packages
initramfs-tools-bin:
  Installed: 0.103ubuntu4.9
  Candidate: 0.103ubuntu4.10
  Version table:
     0.103ubuntu4.10 0
        500 http://mirrors.digitalocean.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 0.103ubuntu4.9 0
        100 /var/lib/dpkg/status
     0.103ubuntu4 0
        500 http://mirrors.digitalocean.com/ubuntu/ trusty/main amd64 Packages
linux-initramfs-tool:
  Installed: (none)
  Candidate: (none)
  Version table:
```

---

### Post by Bashing-om on 2018-01-08
clearski; Well;

What should be:
> 
Package initramfs-tools
trusty-updates (utils): tools for generating an initramfs 
0.103ubuntu4.10: all

Package initramfs-tools-bin
trusty-updates (utils): binaries used by initramfs-tools 
0.103ubuntu4.10: amd64 arm64 armhf i386 powerpc ppc64el



so, what is holding them to the 0.103ubuntu4.9 version ?
If the system is fully updated, you should be up on:
> 
Package linux-image-3.13.0-100-generic
trusty-updates (kernel): Linux kernel image for version 3.13.0 on 32 bit x86 SMP 
3.13.0-100.147: amd64 arm64 armhf i386 ppc64el


So, let us walk down the linux-image path:
show us:
```

uname -r
dpkg -l | grep linux-

```

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by clearski on 2018-01-09
```
$ uname -r
3.13.0-95-generic

$ sudo dpkg -l | grep -i linux-

ii  linux-firmware                       1.127.24                                   all          Firmware for Linux kernel drivers
ii  linux-generic                        3.13.0.137.146                             amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-137             3.13.0-137.186                             all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-137-generic     3.13.0-137.186                             amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-95              3.13.0-95.142                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic      3.13.0-95.142                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                3.13.0.137.146                             amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-132-generic       3.13.0-132.181                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-137-generic       3.13.0-137.186                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-77-generic        3.13.0-77.121                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic        3.13.0-79.123                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic        3.13.0-85.129                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic        3.13.0-86.131                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-88-generic        3.13.0-88.135                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-95-generic        3.13.0-95.142                              amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-132-generic 3.13.0-132.181                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-137-generic 3.13.0-137.186                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-77-generic  3.13.0-77.121                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic  3.13.0-79.123                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-85-generic  3.13.0-85.129                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-86-generic  3.13.0-86.131                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-88-generic  3.13.0-88.135                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-95-generic  3.13.0-95.142                              amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                  3.13.0.137.146                             amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                 3.13.0-137.186                             amd64        Linux Kernel Headers for development

$ ls -l /boot
total 60536
-rw-r--r-- 1 root root  1166991 Dec  4 22:50 abi-3.13.0-137-generic
-rw-r--r-- 1 root root  1166336 Aug 12  2016 abi-3.13.0-95-generic
-rw-r--r-- 1 root root   166050 Dec  4 22:50 config-3.13.0-137-generic
-rw-r--r-- 1 root root   165966 Aug 12  2016 config-3.13.0-95-generic
drwxr-xr-x 5 root root     4096 Jan  4 18:13 grub
-rw-r--r-- 1 root root 20163067 Dec 15 21:49 initrd.img-3.13.0-137-generic
-rw-r--r-- 1 root root 20116848 Dec 15 21:48 initrd.img-3.13.0-95-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3400567 Dec  4 22:50 System.map-3.13.0-137-generic
-rw------- 1 root root  3394259 Aug 12  2016 System.map-3.13.0-95-generic
-rw------- 1 root root  5852400 Dec  4 22:50 vmlinuz-3.13.0-137-generic
-rw------- 1 root root  5835312 Aug 12  2016 vmlinuz-3.13.0-95-generic

```

For some reason it's running kernel 3.13.0-95.

---

### Post by Bashing-om on 2018-01-10
clearski; Humm ..

So this is a Virtual Machine install ?
> 
 [http://mirrors.digitalocean.com/ubuntu/](http://mirrors.digitalocean.com/ubuntu/)


I have no experience with VMs so this is above my skill set.

Have you considered opening a ticket with your provider ?

[INDENT][INDENT][INDENT][INDENT]above and beyond the call ?
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by clearski on 2018-01-11
Thank you, everyone, much appreciated.

Just wanted to make sure there isn't anything I could do myself, but now I will open a ticket with the VM provider.

---

