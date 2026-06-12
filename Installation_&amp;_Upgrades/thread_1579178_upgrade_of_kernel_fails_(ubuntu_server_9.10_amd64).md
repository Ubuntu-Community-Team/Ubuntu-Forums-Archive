---
title: "upgrade of kernel fails (ubuntu server 9.10 amd64)"
date: 2010-09-21
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-09-21
The following is a subset of error messages I'm getting when trying to do "apt-get upgrade" or "apt-get dist-upgrade" on a machine running ubuntu server 9.10 amd64:

```
Preparing to replace linux-image-2.6.31-22-server 2.6.31-22.60 (using .../linux-image-2.6.31-22-server_2.6.31-22.65_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.31-22-server ...
Running postrm hook script /usr/sbin/update-grub.
Generating grub.cfg ...
find: unknown predicate `-f'
Found linux image: /boot/vmlinuz-2.6.31-22-server
find: unknown predicate `-f'
User postrm hook script [/usr/sbin/update-grub] exited with value 1
```

I checked the man page for "find" and there really is no option '-f' for that command.  I am unable to get the upgraded kernel installed.  Anyone know what is going on here?

The full log file (output from script programs, so it has CRLF pairs) is downloadable here:
[http://phil.ipal.org/ufo/20100921/20100921-121047-005727-apt-get-dist-upgrade.log](http://phil.ipal.org/ufo/20100921/20100921-121047-005727-apt-get-dist-upgrade.log)

---

### Post by Skaperen on 2010-09-22
Is there another way to install a kernel since the package doesn't work?  I think the kernel itself is OK, but the rebuild scripts ... specifically the grub part ... seem to be broken.  Any docs on doing this manually?

---

### Post by Skaperen on 2010-09-22
It looks like the kernel is installed, but won't run.  Is there a command to make it run?

```
meitner/root/x0 /root 1# uname -a
Linux meitner 2.6.31-14-server #48-Ubuntu SMP Fri Oct 16 15:07:34 UTC 2009 x86_64 GNU/Linux
meitner/root/x0 /root 2# dpkg -l | fgrep linux
ii  libselinux1                       2.0.85-2ubuntu2                   SELinux shared libraries
ii  libv4l-0                          0.6.0-1                           Collection of video4linux support libraries
ii  linux-firmware                    1.26                              Firmware for Linux kernel drivers
ii  linux-headers-2.6.31-22           2.6.31-22.65                      Header files related to Linux kernel version
ii  linux-headers-2.6.31-22-server    2.6.31-22.65                      Linux kernel headers for version 2.6.31 on x
ii  linux-headers-server              2.6.31.22.35                      Linux kernel headers on Server Equipment.
ii  linux-image-2.6.31-14-server      2.6.31-14.48                      Linux kernel image for version 2.6.31 on x86
rc  linux-image-2.6.31-22-server      2.6.31-22.65                      Linux kernel image for version 2.6.31 on x86
ii  linux-libc-dev                    2.6.31-22.65                      Linux Kernel Headers for development
ii  util-linux                        2.16-1ubuntu5                     Miscellaneous system utilities
meitner/root/x0 /root 3# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
meitner/root/x0 /root 4# 
```

---

