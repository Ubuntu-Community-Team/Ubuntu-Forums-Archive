---
title: "problems in installing linphone-3.3.0"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by mkarthik90 on 2010-06-14
Hi,
i downloaded linphone 3.30 using mozila and tried installing. while  giving
the command ./configure it was successful and next giving the command  make
gives me a error message make file is not found. but [makefile.am]("http://makefile.am/") and
[makefile.in]("http://makefile.in/") is already  available in the current working directory.


 i have given the link of the pastebin for **./configure** command and **make**
command..


*./configure :*

[http://pastebin.com/CvF4FDpw](http://pastebin.com/CvF4FDpw)


*make command :*


[http://pastebin.com/X8fVuBkT](http://pastebin.com/X8fVuBkT)



Can anyone suggest me what shall be done to solve the problem ?

---

### Post by davidmohammed on 2010-06-14
its in the standard repository - just open synaptic manager and search for it.

---

### Post by wayover13 on 2010-06-25
I'd like to hijack this thread, if I may.

My issue does concern Linphone, so I won't take this thread in an utterly different direction. No. Linphone has been installed via the repository on this ubuntu (alternate) installation, which has now been upgraded to Lucid. Problem is, it won't start for me.

When I issue the command linphone-3 from the CLI, a lot of text scrolls by, the tail end of which looks like this:

003a7000-003a8000 rw-p 00016000 08:01 1875074    /usr/lib/libglade-2.0.so.0.0.7
003a8000-0041f000 r-xp 00000000 08:01 1868373    /usr/lib/libcairo.so.2.10800.10
0041f000-00421000 r--p 00076000 08:01 1868373    /usr/lib/libcairo.so.2.10800.10
00421000-00422000 rw-p 00078000 08:01 1868373    /usr/lib/libcairo.so.2.10800.10
00422000-00462000 r-xp 00000000 08:01 1868194    /usr/lib/libpango-1.0.so.0.2800.0
00462000-00463000 ---p 00040000 08:01 1868194    /usr/lib/libpango-1.0.so.0.2800.0
00463000-00464000 r--p 00040000 08:01 1868194    /usr/lib/libpango-1.0.so.0.2800.0
00464000-00465000 rw-p 00041000 08:01 1868194    /usr/lib/libpango-1.0.so.0.2800.0
00465000-004d6000 r-xp 00000000 08:01 1872982    /usr/lib/libfreetype.so.6.3.22
004d6000-004da000 r--p 00070000 08:01 1872982    /usr/lib/libfreetype.so.6.3.22
004da000-004db000 rw-p 00074000 08:01 1872982    /usr/lib/libfreetype.so.6.3.22
004db000-00509000 r-xp 00000000 08:01 1869106    /usr/lib/libfontconfig.so.1.4.4
00509000-0050a000 r--p 0002d000 08:01 1869106    /usr/lib/libfontconfig.so.1.4.4
0050a000-0050b000 rw-p 0002e000 08:01 1869106    /usr/lib/libfontconfig.so.1.4.4
0050b000-00548000 r-xp 00000000 08:01 1867832    /usr/lib/libgobject-2.0.so.0.2400.1
00548000-00549000 r--p 0003c000 08:01 1867832    /usr/lib/libgobject-2.0.so.0.2400.1
00549000-0054a000 rw-p 0003d000 08:01 1867832    /usr/lib/libgobject-2.0.so.0.2400.1
0054a000-0055b000 r-xp 00000000 08:01 1867940    /usr/lib/libosip2.so.4.2.0
0055b000-0055c000 r--p 00010000 08:01 1867940    /usr/lib/libosip2.so.4.2.0
0055c000-0055d000 rw-p 00011000 08:01 1867940    /usr/lib/libosip2.so.4.2.0
0055d000-0055f000 r-xp 00000000 08:01 1869539    /usr/lib/libXinerama.so.1.0.0
0055f000-00560000 r--p 00001000 08:01 1869539    /usr/lib/libXinerama.so.1.0.0
00560000-00561000 rw-p 00002000 08:01 1869539    /usr/lib/libXinerama.so.1.0.0
00563000-0057e000 r-xp 00000000 08:01 2392083    /lib/ld-2.11.1.so
0057e000-0057f000 r--p 0001a000 08:01 2392083    /lib/ld-2.11.1.so
0057f000-00580000 rw-p 0001b000 08:01 2392083    /lib/ld-2.11.1.so
00580000-00648000 r-xp 00000000 08:01 2392074    /lib/libglib-2.0.so.0.2400.1
00648000-00649000 r--p 000c7000 08:01 2392074    /lib/libglib-2.0.so.0.2400.1
00649000-0064a000 rw-p 000c8000 08:01 2392074    /lib/libglib-2.0.so.0.2400.1
0064b000-00663000 r-xp 00000000 08:01 1869864    /usr/lib/libortp.so.8.0.0
00663000-00664000 r--p 00018000 08:01 1869864    /usr/lib/libortp.so.8.0.0
00664000-00665000 rw-p 00019000 08:01 1869864    /usr/lib/libortp.so.8.0.0
00665000-00728000 r-xp 00000000 08:01 1868488    /usr/lib/libasound.so.2.0.0
00728000-0072c000 r--p 000c2000 08:01 1868488    /usr/lib/libasound.so.2.0.0
0072c000-0072d000 rw-p 000c6000 08:01 1868488    /usr/lib/libasound.so.2.0.0
0072d000-00748000 r-xp 00000000 08:01 2670722    /usr/lib/sse2/libspeex.so.1.5.0
00748000-00749000 r--p 0001a000 08:01 2670722    /usr/lib/sse2/libspeex.so.1.5.0
00749000-0074a000 rw-p 0001b000 08:01 2670722    /usr/lib/sse2/libspeex.so.1.5.0
0074a000-00767000 r-xp 00000000 08:01 2392415    /lib/libgcc_s.so.1
00767000-00768000 r--p 0001c000 08:01 2392415    /lib/libgcc_s.so.1
00768000-00769000 rw-p 0001d000 08:01 2392415    /lib/libgcc_s.so.1
00769000-00777000 r-xp 00000000 08:01 1868080    /usr/lib/libXext.so.6.4.0
00777000-00778000 r--p 0000d000 08:01 1868080    /usr/lib/libXext.so.6.4.0
00778000-00779000 rw-p 0000e000 08:01 1868080    /usr/lib/libXext.so.6.4.0
00779000-0077b000 r-xp 00000000 08:01 1868625    /usr/lib/libXcomposite.so.1.0.0
0077b000-0077c000 r--p 00001000 08:01 1868625    /usr/lib/libXcomposite.so.1.0.0
0077c000-0077d000 rw-p 00002000 08:01 1868625    /usr/lib/libXcomposite.so.1.0.0
0077e000-00793000 r-xp 00000000 08:01 32811      /lib/tls/i686/cmov/libpthread-2.11.1.so
00793000-00794000 r--p 00014000 08:01 32811      /lib/tls/i686/cmov/libpthread-2.11.1.soAborted

The screen then flashes as if the application is actually opening, but then I'm dumped back at the CLI. No segfaults or error messages appear there beyond the last line of what you see above. So, no program interface or clear indication of failure--other than the fact that the program's interface doesn't finally appear.

Anyone else having a problem with linphone under lucid? I should mention that, on this alternate installation, I do not have gnome installed. Rather, I've sort of built up a customized system. It has X installed, of course, but I'm using dwm as my WM.

Tips and/or other reports of failure will be appreciated.

Thanks,
James

---

### Post by wayover13 on 2010-06-25
Resolved.

Very, very odd. I've resolved this, and the "fix" is really a weird one. To backtrack a bit first, I ran the command linphone-3 in a terminal that does scrolling. So I was actually able to look further up in the output than the snippet I just posted and to see that some "stack smashing" had occurred and that the output I was seeing was the tail end of a memory dump or something. Anyway, that gave me some new search possibilities, using which I came across [https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/582268](https://bugs.launchpad.net/ubuntu/+source/linphone/+bug/582268) . Oddly enough, the final post in that thread (on the day when I looked at it, anyway) said "I am finding that after I have successfully launched linphone using the command line, it works perfectly when launched from GNOME," so I tried that. That is, I launched the command line version of linphone (linphonec), exited that, then tried opening the graphical version (linphone-3). And, just as the poster in the bug thread reported, the graphical version started fine after I'd done that.

Go figure. Well, it's working now, so I'm satisfied.

James

---

### Post by zelych on 2010-08-26
[mkarthik90]("http://newyork.ubuntuforums.org/member.php?u=1089737"),
try sudo apt-get install libspeexdsp-dev, then rerun ./configure && make
libspeexdsp-dev contains speex_echo.h and speex_preprocess.h which linphone needs

---

