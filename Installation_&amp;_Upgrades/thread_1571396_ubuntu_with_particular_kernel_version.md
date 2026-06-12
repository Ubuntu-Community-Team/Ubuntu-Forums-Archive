---
title: "ubuntu with particular kernel version"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by willgr on 2010-09-09
Hello,

I would like to download a version of Ubuntu that has a kernel version of 2.6.31-12 or previous.

I have googled it and found a way to determine kernel version after installation, but I would like to find out this information before I download Ubuntu, so that I don't install the wrong version.

Can anyone point me to where I can find this info?

Thanks.

---

### Post by Herman on 2010-09-09
:D Well I happen to be one of those people who like to install each new Ubuntu release fresh in its own partition and keep older installations of Ubuntu lying around rather than upgrading, or deleting and re-installing.
I just took a look around for you in my old Karmic and Jaunty installations and it looks like probably Karmic will be the one to try,
```
herman@amd-quad-lynx:~$ ls -l /media/KARMIC/boot/vmlinuz*
-rw-r--r-- 1 root root 3942624 2010-01-28 14:47 /media/KARMIC/boot/vmlinuz-2.6.31-19-generic
-rw-r--r-- 1 root root 3947008 2010-03-12 16:45 /media/KARMIC/boot/vmlinuz-2.6.31-20-generic
-rw-r--r-- 1 root root 3949024 2010-03-24 19:23 /media/KARMIC/boot/vmlinuz-2.6.31-21-generic
herman@amd-quad-lynx:~$ ls -l /media/JAUNTY/boot/vmlinuz*
-rw-r--r-- 1 root root 3522336 2009-04-17 13:34 /media/JAUNTY/boot/vmlinuz-2.6.28-11-generic
-rw-r--r-- 1 root root 3513024 2009-11-11 21:18 /media/JAUNTY/boot/vmlinuz-2.6.28-16-generic
-rw-r--r-- 1 root root 3513280 2009-12-02 09:03 /media/JAUNTY/boot/vmlinuz-2.6.28-17-generic

``` As you can see though, I no longer have the exact kernel you're looking for.
Maybe somebody running Karmic who still has that kernel can confirm?

UPDATE: I rebooted into Karmic for you and took a look around in Synaptic Package Manager, but mine currently only shows as far back as 2.6.31.14 now.

---

### Post by willgr on 2010-09-09
Well, that's very helpful info thanks. I don't need an exact version, just that one or a previous one. Perhaps Jaunty is best to ensure a pre-dated version.

I have a C++ script that I currently compile into a CGI on Win 32 (Vista) but my webhost runs linux.

They run 2.6.31-12, so to ensure the CGI works I need to compile it on a linux that pre-dates that linux (or so I have googled).

Any advice on this appreciated (I normally develop on Windows you see).

---

