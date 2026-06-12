---
title: "cowpatty error"
date: 2009-02-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubusira on 2009-02-17
ubuntu 9.04 on hp-lptp

i've made many efforts to "make" cowpatty work.
downloaded all lib that needs ,tried cowpatty 4.2 ,4.3 ,tried debian pkg..stil nothing!

when i make
./cowpatty -r /root/corin-01.cap -d /root/corinpmk -s "wifinet"
it gives me

cowpatty 4.3 - WPA-PSK dictionary attack. <jwright@hasborg.com>

Collected all necessary data to mount crack against WPA2/PSK passphrase.
Starting dictionary attack. Please be patient.
*** buffer overflow detected ***: ./cowpatty terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x4[0xb7e55da8]
/lib/tls/i686/cmov/libc.so.6[0xb7e53eb0]
/lib/tls/i686/cmov/libc.so.6(__fread_chk+0x143)[0xb7e547a3]
./cowpatty[0x804904f]
./cowpatty[0x804a349]
./cowpatty[0x804a8b1]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb7d6e775]
./cowpatty[0x8048cb1]
======= Memory map: ========
08048000-0804d000 r-xp 00000000 08:11
7176244 /root/cowpatty-4.3/cowpatty
0804d000-0804e000 r--p 00004000 08:11
7176244 /root/cowpatty-4.3/cowpatty
0804e000-0804f000 rw-p 00005000 08:11
7176244 /root/cowpatty-4.3/cowpatty
0971b000-0973c000 rw-p 0971b000 00:00 0
b7d3d000-b7d3e000 rw-p b7d3d000 00:00 0
b7d3e000-b7d52000 r-xp 00000000 08:11
5679603 /usr/lib/libz.so.1.2.3.3
b7d52000-b7d54000 rw-p 00013000 08:11
5679603 /usr/lib/libz.so.1.2.3.3
b7d54000-b7d56000 r-xp 00000000 08:11
6627381 /lib/tls/i686/cmov/libdl-2.9.so
b7d56000-b7d57000 r--p 00001000 08:11
6627381 /lib/tls/i686/cmov/libdl-2.9.so
b7d57000-b7d58000 rw-p 00002000 08:11
6627381 /lib/tls/i686/cmov/libdl-2.9.so
b7d58000-b7eb4000 r-xp 00000000 08:11
6627378 /lib/tls/i686/cmov/libc-2.9.so
b7eb4000-b7eb5000 ---p 0015c000 08:11
6627378 /lib/tls/i686/cmov/libc-2.9.so
b7eb5000-b7eb7000 r--p 0015c000 08:11
6627378 /lib/tls/i686/cmov/libc-2.9.so
b7eb7000-b7eb8000 rw-p 0015e000 08:11
6627378 /lib/tls/i686/cmov/libc-2.9.so
b7eb8000-b7ebc000 rw-p b7eb8000 00:00 0
b7ebc000-b7fee000 r-xp 00000000 08:11
5709970 /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7fee000-b7fef000 ---p 00132000 08:11
5709970 /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7fef000-b7ff7000 r--p 00132000 08:11
5709970 /usr/lib/i686/cmov/libcrypto.so.0.9.8
b7ff7000-b8004000 rw-p 0013a000 08:11
5709970 /usr/lib/i686/cmov/libcrypto.so.0.9.8
b8004000-b8008000 rw-p b8004000 00:00 0
b8008000-b8037000 r-xp 00000000 08:11
5678725 /usr/lib/libpcap.so.1.0.0
b8037000-b8038000 r--p 0002e000 08:11
5678725 /usr/lib/libpcap.so.1.0.0
b8038000-b8039000 rw-p 0002f000 08:11
5678725 /usr/lib/libpcap.so.1.0.0
b8041000-b804e000 r-xp 00000000 08:11 6611002 /lib/libgcc_s.so.1
b804e000-b804f000 r--p 0000c000 08:11 6611002 /lib/libgcc_s.so.1
b804f000-b8050000 rw-p 0000d000 08:11 6611002 /lib/libgcc_s.so.1
b8050000-b8054000 rw-p b8050000 00:00 0
b8054000-b8055000 r-xp b8054000 00:00 0 [vdso]
b8055000-b8071000 r-xp 00000000 08:11 6611086 /lib/ld-2.9.so
b8071000-b8072000 r--p 0001b000 08:11 6611086 /lib/ld-2.9.so
b8072000-b8073000 rw-p 0001c000 08:11 6611086 /lib/ld-2.9.so
bfe5d000-bfe72000 rw-p bffeb000 00:00 0 [stack]
Aborted (core dumped)




the same result with genpmk efforts.
anyone can help?   :(

---

