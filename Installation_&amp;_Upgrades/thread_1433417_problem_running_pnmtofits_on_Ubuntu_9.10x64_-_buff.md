---
title: "problem running pnmtofits on Ubuntu 9.10x64 - buffer overflow"
date: 2010-03-19
forum: Installation &amp; Upgrades
---

### Post by wikisky on 2010-03-19
I have a problem running pnmtofits on Ubuntu 9.10x64.
It works fine on Ubuntu 8x64, but I can't make it work on 9. 
I just installed fresh both 8 and 9 on virtualBox to confirm that there's a problem in 9. 
Any suggestions how to fix it? 

Thank you.



>$ pnmtofits t.pnm >t.fits

*** buffer overflow detected ***: pnmtofits terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x37)[0x7f4aae764647]
/lib/libc.so.6[0x7f4aae7635f0]
/lib/libc.so.6[0x7f4aae762a59]
/lib/libc.so.6(_IO_default_xsputn+0x98)[0x7f4aae6e1448]
/lib/libc.so.6(_IO_vfprintf+0x5a5)[0x7f4aae6b2345]
/lib/libc.so.6(__vsprintf_chk+0x99)[0x7f4aae762af9]
/lib/libc.so.6(__sprintf_chk+0x7f)[0x7f4aae762a3f]
pnmtofits[0x400dcc]
/lib/libc.so.6(__libc_start_main+0xfd)[0x7f4aae68babd]
pnmtofits[0x400989]
======= Memory map: ========
00400000-00402000 r-xp 00000000 08:05 1533193                            /usr/bin/pnmtofits
00601000-00602000 r--p 00001000 08:05 1533193                            /usr/bin/pnmtofits
00602000-00603000 rw-p 00002000 08:05 1533193                            /usr/bin/pnmtofits
00c60000-00c81000 rw-p 00000000 00:00 0                                  [heap]
7f4aadf85000-7f4aadf9b000 r-xp 00000000 08:05 5382159                    /lib/libgcc_s.so.1
7f4aadf9b000-7f4aae19a000 ---p 00016000 08:05 5382159                    /lib/libgcc_s.so.1
7f4aae19a000-7f4aae19b000 r--p 00015000 08:05 5382159                    /lib/libgcc_s.so.1
7f4aae19b000-7f4aae19c000 rw-p 00016000 08:05 5382159                    /lib/libgcc_s.so.1
7f4aae19c000-7f4aae66d000 rw-p 00000000 00:00 0 
7f4aae66d000-7f4aae7d3000 r-xp 00000000 08:05 5382422                    /lib/libc-2.10.1.so
7f4aae7d3000-7f4aae9d2000 ---p 00166000 08:05 5382422                    /lib/libc-2.10.1.so
7f4aae9d2000-7f4aae9d6000 r--p 00165000 08:05 5382422                    /lib/libc-2.10.1.so
7f4aae9d6000-7f4aae9d7000 rw-p 00169000 08:05 5382422                    /lib/libc-2.10.1.so
7f4aae9d7000-7f4aae9dc000 rw-p 00000000 00:00 0 
7f4aae9dc000-7f4aae9fa000 r-xp 00000000 08:05 1532151                    /usr/lib/libnetpbm.so.10.0
7f4aae9fa000-7f4aaebf9000 ---p 0001e000 08:05 1532151                    /usr/lib/libnetpbm.so.10.0
7f4aaebf9000-7f4aaebfa000 r--p 0001d000 08:05 1532151                    /usr/lib/libnetpbm.so.10.0
7f4aaebfa000-7f4aaebfe000 rw-p 0001e000 08:05 1532151                    /usr/lib/libnetpbm.so.10.0
7f4aaebfe000-7f4aaec1d000 r-xp 00000000 08:05 5382203                    /lib/ld-2.10.1.so
7f4aaedfd000-7f4aaedff000 rw-p 00000000 00:00 0 
7f4aaee18000-7f4aaee1c000 rw-p 00000000 00:00 0 
7f4aaee1c000-7f4aaee1d000 r--p 0001e000 08:05 5382203                    /lib/ld-2.10.1.so
7f4aaee1d000-7f4aaee1e000 rw-p 0001f000 08:05 5382203                    /lib/ld-2.10.1.so
7fff758e3000-7fff758f8000 rw-p 00000000 00:00 0                          [stack]
7fff759cf000-7fff759d0000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
Aborted

---

