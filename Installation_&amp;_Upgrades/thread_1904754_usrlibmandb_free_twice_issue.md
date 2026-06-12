---
title: "/usr/lib/mandb free twice issue"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by mykes on 2012-01-05
When doing sudo apt-get upgrade, I've been getting a "free twice" error running /usr/bin/mandb the past few times.  

In this case, I did sudo apt-get dist-upgrade and it's installing just binutils.

```

Preparing to replace binutils 2.21.53.20110810-0ubuntu5 (using .../binutils_2.21.53.20110810-0ubuntu5.1_amd64.deb) ...
Unpacking replacement binutils ...
Processing triggers for man-db ...
*** glibc detected *** /usr/bin/mandb: double free or corruption (fasttop): 0x00007f0ba739e150 ***
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78a96)[0x7f0ba4b6ca96]
/lib/x86_64-linux-gnu/libc.so.6(cfree+0x6c)[0x7f0ba4b70d7c]
/usr/bin/mandb(+0x7dff)[0x7f0ba58f6dff]
/usr/bin/mandb(+0x60bc)[0x7f0ba58f50bc]
/usr/bin/mandb(+0x645e)[0x7f0ba58f545e]
/usr/bin/mandb(+0x6e8e)[0x7f0ba58f5e8e]
/usr/bin/mandb(+0xc4ac)[0x7f0ba58fb4ac]
/usr/bin/mandb(+0xc93b)[0x7f0ba58fb93b]
/usr/bin/mandb(main+0x1bd)[0x7f0ba58f441d]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed)[0x7f0ba4b1530d]
/usr/bin/mandb(+0x57ad)[0x7f0ba58f47ad]
======= Memory map: ========
7f0b9c000000-7f0b9c021000 rw-p 00000000 00:00 0 
7f0b9c021000-7f0ba0000000 ---p 00000000 00:00 0 
7f0ba3910000-7f0ba3925000 r-xp 00000000 08:15 12849575                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f0ba3925000-7f0ba3b24000 ---p 00015000 08:15 12849575                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f0ba3b24000-7f0ba3b25000 r--p 00014000 08:15 12849575                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f0ba3b25000-7f0ba3b26000 rw-p 00015000 08:15 12849575                   /lib/x86_64-linux-gnu/libgcc_s.so.1
7f0ba3b26000-7f0ba3b32000 r-xp 00000000 08:15 12849586                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f0ba3b32000-7f0ba3d31000 ---p 0000c000 08:15 12849586                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f0ba3d31000-7f0ba3d32000 r--p 0000b000 08:15 12849586                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f0ba3d32000-7f0ba3d33000 rw-p 0000c000 08:15 12849586                   /lib/x86_64-linux-gnu/libnss_files-2.13.so
7f0ba3d33000-7f0ba3d3d000 r-xp 00000000 08:15 12849592                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f0ba3d3d000-7f0ba3f3d000 ---p 0000a000 08:15 12849592                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f0ba3f3d000-7f0ba3f3e000 r--p 0000a000 08:15 12849592                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f0ba3f3e000-7f0ba3f3f000 rw-p 0000b000 08:15 12849592                   /lib/x86_64-linux-gnu/libnss_nis-2.13.so
7f0ba3f3f000-7f0ba3f56000 r-xp 00000000 08:15 12849203                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f0ba3f56000-7f0ba4155000 ---p 00017000 08:15 12849203                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f0ba4155000-7f0ba4156000 r--p 00016000 08:15 12849203                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f0ba4156000-7f0ba4157000 rw-p 00017000 08:15 12849203                   /lib/x86_64-linux-gnu/libnsl-2.13.so
7f0ba4157000-7f0ba4159000 rw-p 00000000 00:00 0 
7f0ba4159000-7f0ba4161000 r-xp 00000000 08:15 12849199                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f0ba4161000-7f0ba4360000 ---p 00008000 08:15 12849199                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f0ba4360000-7f0ba4361000 r--p 00007000 08:15 12849199                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f0ba4361000-7f0ba4362000 rw-p 00008000 08:15 12849199                   /lib/x86_64-linux-gnu/libnss_compat-2.13.so
7f0ba4362000-7f0ba48dc000 r--p 00000000 08:15 11803433                   /usr/lib/locale/locale-archive
7f0ba48dc000-7f0ba48f3000 r-xp 00000000 08:15 12848880                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f0ba48f3000-7f0ba4af2000 ---p 00017000 08:15 12848880                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f0ba4af2000-7f0ba4af3000 r--p 00016000 08:15 12848880                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f0ba4af3000-7f0ba4af4000 rw-p 00017000 08:15 12848880                   /lib/x86_64-linux-gnu/libz.so.1.2.3.4
7f0ba4af4000-7f0ba4c89000 r-xp 00000000 08:15 12849583                   /lib/x86_64-linux-gnu/libc-2.13.so
7f0ba4c89000-7f0ba4e88000 ---p 00195000 08:15 12849583                   /lib/x86_64-linux-gnu/libc-2.13.so
7f0ba4e88000-7f0ba4e8c000 r--p 00194000 08:15 12849583                   /lib/x86_64-linux-gnu/libc-2.13.so
7f0ba4e8c000-7f0ba4e8d000 rw-p 00198000 08:15 12849583                   /lib/x86_64-linux-gnu/libc-2.13.so
7f0ba4e8d000-7f0ba4e93000 rw-p 00000000 00:00 0 
7f0ba4e93000-7f0ba4e9f000 r-xp 00000000 08:15 11798910                   /usr/lib/x86_64-linux-gnu/libpipeline.so.1.2.0
7f0ba4e9f000-7f0ba509e000 ---p 0000c000 08:15 11798910                   /usr/lib/x86_64-linux-gnu/libpipeline.so.1.2.0
7f0ba509e000-7f0ba509f000 r--p 0000b000 08:15 11798910                   /usr/lib/x86_64-linux-gnu/libpipeline.so.1.2.0
7f0ba509f000-7f0ba50a0000 rw-p 0000c000 08:15 11798910                   /usr/lib/x86_64-linux-gnu/libpipeline.so.1.2.0
7f0ba50a0000-7f0ba50a5000 r-xp 00000000 08:15 11796500                   /usr/lib/x86_64-linux-gnu/libgdbm.so.3.0.0
7f0ba50a5000-7f0ba52a4000 ---p 00005000 08:15 11796500                   /usr/lib/x86_64-linux-gnu/libgdbm.so.3.0.0
7f0ba52a4000-7f0ba52a5000 r--p 00004000 08:15 11796500                   /usr/lib/x86_64-linux-gnu/libgdbm.so.3.0.0
7f0ba52a5000-7f0ba52a6000 rw-p 00005000 08:15 11796500                   /usr/lib/x86_64-linux-gnu/libgdbm.so.3.0.0
7f0ba52a6000-7f0ba52c3000 r-xp 00000000 08:15 11797620                   /usr/lib/man-db/libman-2.6.0.2.so
7f0ba52c3000-7f0ba54c3000 ---p 0001d000 08:15 11797620                   /usr/lib/man-db/libman-2.6.0.2.so
7f0ba54c3000-7f0ba54c4000 r--p 0001d000 08:15 11797620                   /usr/lib/man-db/libman-2.6.0.2.so
7f0ba54c4000-7f0ba54c5000 rw-p 0001e000 08:15 11797620                   /usr/lib/man-db/libman-2.6.0.2.so
7f0ba54c5000-7f0ba54c6000 rw-p 00000000 00:00 0 
7f0ba54c6000-7f0ba54cb000 r-xp 00000000 08:15 11797643                   /usr/lib/man-db/libmandb-2.6.0.2.so
7f0ba54cb000-7f0ba56ca000 ---p 00005000 08:15 11797643                   /usr/lib/man-db/libmandb-2.6.0.2.so
7f0ba56ca000-7f0ba56cb000 r--p 00004000 08:15 11797643                   /usr/lib/man-db/libmandb-2.6.0.2.so
7f0ba56cb000-7f0ba56cc000 rw-p 00005000 08:15 11797643                   /usr/lib/man-db/libmandb-2.6.0.2.so
7f0ba56cc000-7f0ba56ed000 r-xp 00000000 08:15 12849590                   /lib/x86_64-linux-gnu/ld-2.13.so
7f0ba58c3000-7f0ba58c8000 rw-p 00000000 00:00 0 
7f0ba58ea000-7f0ba58ec000 rw-p 00000000 00:00 0 
7f0ba58ec000-7f0ba58ed000 r--p 00020000 08:15 12849590                   /lib/x86_64-linux-gnu/ld-2.13.so
7f0ba58ed000-7f0ba58ef000 rw-p 00021000 08:15 12849590                   /lib/x86_64-linux-gnu/ld-2.13.so
7f0ba58ef000-7f0ba590d000 r-xp 00000000 08:15 11797280                   /usr/bin/mandb
7f0ba5b0d000-7f0ba5b0e000 r--p 0001e000 08:15 11797280                   /usr/bin/mandb
7f0ba5b0e000-7f0ba5b0f000 rw-p 0001f000 08:15 11797280                   /usr/bin/mandb
7f0ba5b0f000-7f0ba5b11000 rw-p 00000000 00:00 0 
7f0ba72bd000-7f0ba73bd000 rw-p 00000000 00:00 0                          [heap]
7fffb5d75000-7fffb5d96000 rw-p 00000000 00:00 0                          [stack]
7fffb5dff000-7fffb5e00000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted
Setting up binutils (2.21.53.20110810-0ubuntu5.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

