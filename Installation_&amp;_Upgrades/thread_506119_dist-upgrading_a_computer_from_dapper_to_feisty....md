---
title: "dist-upgrading a computer from dapper to feisty...mdadm help"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by master5o1 on 2007-07-21
help i don't know what to do here:

```
Ubuntu Configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring mdadm &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474;
 &#9474; If your system has its root filesystem on an MD array (RAID), it needs
 &#9474; to be started early during the boot sequence. If your root filesystem is  &#9618;
 &#9474; on a logical volume (LVM), which is on MD, all constituent arrays need    &#9618;
 &#9474; to be started.                                                            &#9618;
 &#9474;                                                                           &#9618;
 &#9474; If you know exactly which arrays are needed to bring up the root          &#9618;
 &#9474; filesystem, and you want to postpone starting all other arrays to a       &#9618;
 &#9474; later point in the boot sequence, enter the arrays to start here.         &#9618;
 &#9474; Alternatively, enter 'all' to simply start all available arrays.          &#9618;
 &#9474;                                                                           &#9618;
 &#9474; If you do not need or want to start any arrays for the root filesystem,   &#9618;
 &#9474; leave the answer blank (or enter 'none'). This may be the case if you     &#9618;
 &#9474; are using kernel autostart or do not need any arrays to boot.             &#9618;
 &#9474;                                                                           &#9618;
 &#9474;
 &#9474;                                  <Ok>

```

There is only one hard drive on this Acer Aspire 5020 laptop, and it is 100gb -- split into 2 parts -- one for the existing windows, the other for Ubuntu :)

I had only installed ubuntu on the previously D:\ drive on windows -- the empty partition. I don't know whether I should put "all" or "none".

---

### Post by master5o1 on 2007-07-21
I just decided to do "none" and then let it start them automatically... so does tha tmake it that if there ARE infact arrays, they will get started, and if there ARE NO arrays, they will not? I hope so :|

---

### Post by master5o1 on 2007-07-21
argh! Now its stopped the dist-upgrade process and says:

> Errors were encountered while processing:
 /var/cache/apt/archives/ia32-libs_1.5ubuntu9_amd64.deb
 /var/cache/apt/archives/libc6-i386_2.5-0ubuntu14_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


So running "sudo dpkg -C" :

> The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 lsb-release          Linux Standard Base version reporting utility
 lib32gcc1            GCC support library (32 bit Version)
 lib32z1              compression library - 32 bit runtime
 tzdata               Time Zone and Daylight Saving Time Data
 python-support       automated rebuilding support for python modules
 gcc-4.1-base         The GNU Compiler Collection (base package)
 lib32stdc++6         The GNU Standard C++ Library v3 (32 bit Version)
 belocs-locales-bin   tools for compiling locale data files


:S

---

### Post by Flamekebab on 2007-07-24
Did you try running
```
sudo dpkg --configure
```
as it suggested?

---

### Post by Steve1961 on 2007-07-24
Try running:

sudo apt-get -f install
sudo dpkg --configure -a

Don't worry about mdadm - you only need it if you have raid arrays.  By the way, and I know this is probably too late, but the 'safest' way of upgrading is to first upgrade to edgy and then to feisty.

---

