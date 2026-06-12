---
title: "dpkg interruption problem in Ubuntu 17.04  on DELL Precision 5520"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by joe-wangq on 2017-07-24
Hello everyone, today, I encountered a dpkg interruption problem when I update my Ubuntu 17.04 (default is unity) on the DELL Precision 5520.
 
In July, I installed a GNOME on the Ubuntu 17.04 unity, and  Anaconda 4.4.0. 

The dpkg interruption problem is as following table: 

```
wq@wangq:~$ sudo apt-get update
[sudo] password for wq: 
Sorry, try again.
[sudo] password for wq: 
Hit:1 [http://cn.archive.ubuntu.com/ubuntu](http://cn.archive.ubuntu.com/ubuntu) zesty InRelease
Hit:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) zesty InRelease                         
Get:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease [89.2 kB]
Fetched 89.2 kB in 1s (61.1 kB/s)                            
Reading package lists... Done
wq@wangq:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
wq@wangq:~$ sudo rm /var/lib/dpkg/updates/*
wq@wangq:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  guile-2.0-libs libgc1c2
Use 'sudo apt autoremove' to remove them.
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic linux-signed-generic
  linux-signed-image-generic
The following packages will be upgraded:
  apport apport-gtk evince evince-common libevdocument3-4 libevview3-3
  libexpat1 libexpat1-dev libmysqlclient-dev libmysqlclient20 linux-libc-dev
11 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0 B/4,059 kB of archives.
After this operation, 26.6 kB disk space will be freed.
Do you want to continue? [Y/n] 
dpkg: warning: files list file for package 'language-pack-gnome-en' missing; assuming package has no files currently installed
(Reading database ... 280210 files and directories currently installed.)
Preparing to unpack .../00-apport_2.20.4-0ubuntu4.5_all.deb ...
Traceback (most recent call last):
  File "/usr/bin/pyclean", line 32, in <module>
    from debpython.namespace import add_namespace_files
  File "/usr/share/python/debpython/namespace.py", line 28, in <module>
    from debpython.pydist import PUBLIC_DIR_RE
  File "/usr/share/python/debpython/pydist.py", line 27, in <module>
    from string import maketrans
ImportError: cannot import name 'maketrans'
dpkg: warning: subprocess old pre-removal script returned error exit status 1
dpkg: trying script from the new package instead ...
Traceback (most recent call last):
  File "/usr/bin/pyclean", line 32, in <module>
    from debpython.namespace import add_namespace_files
  File "/usr/share/python/debpython/namespace.py", line 28, in <module>
    from debpython.pydist import PUBLIC_DIR_RE
  File "/usr/share/python/debpython/pydist.py", line 27, in <module>
    from string import maketrans
ImportError: cannot import name 'maketrans'
dpkg: error processing archive /tmp/apt-dpkg-install-yCYRze/00-apport_2.20.4-0ubuntu4.5_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycompile", line 35, in <module>
    from debpython.version import SUPPORTED, debsorted, vrepr, \
  File "/usr/share/python/debpython/version.py", line 24, in <module>
    from ConfigParser import SafeConfigParser
ImportError: No module named 'ConfigParser'
*** Error in `/usr/bin/dpkg': munmap_chunk(): invalid pointer: 0x0000562f42f242b8 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x7908b)[0x7fa94a35c08b]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x1f8)[0x7fa94a369ed8]
/usr/bin/dpkg(+0x20cd0)[0x562f40b2fcd0]
/usr/bin/dpkg(+0x21119)[0x562f40b30119]
/usr/bin/dpkg(+0x283cd)[0x562f40b373cd]
/usr/bin/dpkg(+0x17737)[0x562f40b26737]
/usr/bin/dpkg(+0x17915)[0x562f40b26915]
/usr/bin/dpkg(+0x17b5d)[0x562f40b26b5d]
/usr/bin/dpkg(+0xaed7)[0x562f40b19ed7]
/usr/bin/dpkg(+0x20c0b)[0x562f40b2fc0b]
/usr/bin/dpkg(+0x20e01)[0x562f40b2fe01]
/usr/bin/dpkg(+0xa962)[0x562f40b19962]
/usr/bin/dpkg(+0x72fd)[0x562f40b162fd]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf1)[0x7fa94a3033f1]
/usr/bin/dpkg(+0x743a)[0x562f40b1643a]
======= Memory map: ========
562f40b0f000-562f40b54000 r-xp 00000000 103:02 14811402                  /usr/bin/dpkg
562f40d54000-562f40d57000 r--p 00045000 103:02 14811402                  /usr/bin/dpkg
562f40d57000-562f40d58000 rw-p 00048000 103:02 14811402                  /usr/bin/dpkg
562f40d58000-562f40f6c000 rw-p 00000000 00:00 0 
562f4295b000-562f45eb3000 rw-p 00000000 00:00 0                          [heap]
7fa948d66000-7fa948d7c000 r-xp 00000000 103:02 6296069                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa948d7c000-7fa948f7b000 ---p 00016000 103:02 6296069                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa948f7b000-7fa948f7c000 r--p 00015000 103:02 6296069                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa948f7c000-7fa948f7d000 rw-p 00016000 103:02 6296069                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa948f7d000-7fa948f88000 r-xp 00000000 103:02 6291549                   /lib/x86_64-linux-gnu/libnss_files-2.24.so
7fa948f88000-7fa949187000 ---p 0000b000 103:02 6291549                   /lib/x86_64-linux-gnu/libnss_files-2.24.so
7fa949187000-7fa949188000 r--p 0000a000 103:02 6291549                   /lib/x86_64-linux-gnu/libnss_files-2.24.so
7fa949188000-7fa949189000 rw-p 0000b000 103:02 6291549                   /lib/x86_64-linux-gnu/libnss_files-2.24.so
7fa949189000-7fa94918f000 rw-p 00000000 00:00 0 
7fa94918f000-7fa94919a000 r-xp 00000000 103:02 6291551                   /lib/x86_64-linux-gnu/libnss_nis-2.24.so
7fa94919a000-7fa949399000 ---p 0000b000 103:02 6291551                   /lib/x86_64-linux-gnu/libnss_nis-2.24.so
7fa949399000-7fa94939a000 r--p 0000a000 103:02 6291551                   /lib/x86_64-linux-gnu/libnss_nis-2.24.so
7fa94939a000-7fa94939b000 rw-p 0000b000 103:02 6291551                   /lib/x86_64-linux-gnu/libnss_nis-2.24.so
7fa94939b000-7fa9493b1000 r-xp 00000000 103:02 6291546                   /lib/x86_64-linux-gnu/libnsl-2.24.so
7fa9493b1000-7fa9495b0000 ---p 00016000 103:02 6291546                   /lib/x86_64-linux-gnu/libnsl-2.24.so
7fa9495b0000-7fa9495b1000 r--p 00015000 103:02 6291546                   /lib/x86_64-linux-gnu/libnsl-2.24.so
7fa9495b1000-7fa9495b2000 rw-p 00016000 103:02 6291546                   /lib/x86_64-linux-gnu/libnsl-2.24.so
7fa9495b2000-7fa9495b4000 rw-p 00000000 00:00 0 
7fa9495b4000-7fa9495bc000 r-xp 00000000 103:02 6291547                   /lib/x86_64-linux-gnu/libnss_compat-2.24.so
7fa9495bc000-7fa9497bb000 ---p 00008000 103:02 6291547                   /lib/x86_64-linux-gnu/libnss_compat-2.24.so
7fa9497bb000-7fa9497bc000 r--p 00007000 103:02 6291547                   /lib/x86_64-linux-gnu/libnss_compat-2.24.so
7fa9497bc000-7fa9497bd000 rw-p 00008000 103:02 6291547                   /lib/x86_64-linux-gnu/libnss_compat-2.24.so
7fa9497bd000-7fa949c4e000 r--p 00000000 103:02 14812737                  /usr/lib/locale/locale-archive
7fa949c4e000-7fa949c66000 r-xp 00000000 103:02 6295926                   /lib/x86_64-linux-gnu/libpthread-2.24.so
7fa949c66000-7fa949e66000 ---p 00018000 103:02 6295926                   /lib/x86_64-linux-gnu/libpthread-2.24.so
7fa949e66000-7fa949e67000 r--p 00018000 103:02 6295926                   /lib/x86_64-linux-gnu/libpthread-2.24.so
7fa949e67000-7fa949e68000 rw-p 00019000 103:02 6295926                   /lib/x86_64-linux-gnu/libpthread-2.24.so
7fa949e68000-7fa949e6c000 rw-p 00000000 00:00 0 
7fa949e6c000-7fa949e6f000 r-xp 00000000 103:02 6291542                   /lib/x86_64-linux-gnu/libdl-2.24.so
7fa949e6f000-7fa94a06e000 ---p 00003000 103:02 6291542                   /lib/x86_64-linux-gnu/libdl-2.24.so
7fa94a06e000-7fa94a06f000 r--p 00002000 103:02 6291542                   /lib/x86_64-linux-gnu/libdl-2.24.so
7fa94a06f000-7fa94a070000 rw-p 00003000 103:02 6291542                   /lib/x86_64-linux-gnu/libdl-2.24.so
7fa94a070000-7fa94a0e2000 r-xp 00000000 103:02 6296157                   /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fa94a0e2000-7fa94a2e1000 ---p 00072000 103:02 6296157                   /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fa94a2e1000-7fa94a2e2000 r--p 00071000 103:02 6296157                   /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fa94a2e2000-7fa94a2e3000 rw-p 00072000 103:02 6296157                   /lib/x86_64-linux-gnu/libpcre.so.3.13.3
7fa94a2e3000-7fa94a4a1000 r-xp 00000000 103:02 6291539                   /lib/x86_64-linux-gnu/libc-2.24.so
7fa94a4a1000-7fa94a6a0000 ---p 001be000 103:02 6291539                   /lib/x86_64-linux-gnu/libc-2.24.so
7fa94a6a0000-7fa94a6a4000 r--p 001bd000 103:02 6291539                   /lib/x86_64-linux-gnu/libc-2.24.so
7fa94a6a4000-7fa94a6a6000 rw-p 001c1000 103:02 6291539                   /lib/x86_64-linux-gnu/libc-2.24.so
7fa94a6a6000-7fa94a6aa000 rw-p 00000000 00:00 0 
7fa94a6aa000-7fa94a6cf000 r-xp 00000000 103:02 6296184                   /lib/x86_64-linux-gnu/libselinux.so.1
7fa94a6cf000-7fa94a8ce000 ---p 00025000 103:02 6296184                   /lib/x86_64-linux-gnu/libselinux.so.1
7fa94a8ce000-7fa94a8cf000 r--p 00024000 103:02 6296184                   /lib/x86_64-linux-gnu/libselinux.so.1
7fa94a8cf000-7fa94a8d0000 rw-p 00025000 103:02 6296184                   /lib/x86_64-linux-gnu/libselinux.so.1
7fa94a8d0000-7fa94a8d2000 rw-p 00000000 00:00 0 
7fa94a8d2000-7fa94a8f8000 r-xp 00000000 103:02 6291471                   /lib/x86_64-linux-gnu/ld-2.24.so
7fa94aad4000-7fa94aad6000 rw-p 00000000 00:00 0 
7fa94aaf3000-7fa94aaf7000 rw-p 00000000 00:00 0 
7fa94aaf7000-7fa94aaf8000 r--p 00025000 103:02 6291471                   /lib/x86_64-linux-gnu/ld-2.24.so
7fa94aaf8000-7fa94aaf9000 rw-p 00026000 103:02 6291471                   /lib/x86_64-linux-gnu/ld-2.24.so
7fa94aaf9000-7fa94aafa000 rw-p 00000000 00:00 0 
7ffc8b7f4000-7ffc8b815000 rw-p 00000000 00:00 0                          [stack]
7ffc8b84e000-7ffc8b850000 r--p 00000000 00:00 0                          [vvar]
7ffc8b850000-7ffc8b852000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

Anyone has encountered this problem?  Thanks!

---

