---
title: "dpkg: error processing (simple question, honest!)"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by rubic on 2005-11-12
Errors during 5.04 -> 5.10 upgrade.  Can I just download and apply the individual .debs that are missing?  If so, where are they located?  Thanks!

---
dpkg: error processing /var/cache/apt/archives/libc6-i686_2.3.5-1ubuntu12_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1_all.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libdb4.2_4.2.52-19ubuntu4_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/perl_5.8.7-5ubuntu1_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/libperl5.8_5.8.7-5ubuntu1_i386.deb (--unpack):
 cannot access archive: No such file or directory
dpkg: error processing /var/cache/apt/archives/perl-base_5.8.7-5ubuntu1_i386.deb (--unpack):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-i686_2.3.5-1ubuntu12_i386.deb
 /var/cache/apt/archives/perl-modules_5.8.7-5ubuntu1_all.deb
 /var/cache/apt/archives/libdb4.2_4.2.52-19ubuntu4_i386.deb
 /var/cache/apt/archives/perl_5.8.7-5ubuntu1_i386.deb
 /var/cache/apt/archives/libperl5.8_5.8.7-5ubuntu1_i386.deb
 /var/cache/apt/archives/perl-base_5.8.7-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by rubic on 2005-11-12
*<< Can I just download and apply the individual .debs that are missing? If so, where are they located? Thanks! >>*

Just to make it clear:  These .deb files are not located anywhere on my system, i.e. the following produces no output:

 sudo find / -name libc6-i686_2.3.5-1ubuntu12_i386.deb -print

---

### Post by Xian on 2005-11-12
Just download the pkgs from the [Ubuntu Package](http://packages.ubuntu.com/) addy and install locally.

---

### Post by rubic on 2005-11-12
Xian,

I go lookup the first .deb file at this page:

  [http://packages.ubuntu.com/breezy/base/libc6](http://packages.ubuntu.com/breezy/base/libc6)

But I'm unable to locate: libc6-i686_2.3.5-1ubuntu12_i386.deb.
Please advise.  I owe you a cup of coffee. Thanks.

---

### Post by Xian on 2005-11-12
[QUOTE=rubic]But I'm unable to locate: libc6-i686_2.3.5-1ubuntu12_i386.deb.
Please advise.  I owe you a cup of coffee. Thanks.[/QUOTE]

Here's the direct addy: [libc6-i686_2.3.5-1ubuntu12_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-i686_2.3.5-1ubuntu12_i386.deb)

---

