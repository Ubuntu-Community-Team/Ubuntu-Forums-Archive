---
title: "Google Talk on Pidgin: &quot;Server requires TLS/SSL for login.&quot;"
date: 2008-01-21
forum: Installation &amp; Upgrades
---

### Post by nomenclature3000 on 2008-01-21
I upgraded to 7.10 yesterday and everything was working fine afterward except for my monitor and pidgin. After an hour or two of struggle I got my monitor problem straightened out but the pidgin problem remains.

When I try to connect to my google talk account in pidgin, I get "Server requires TLS/SSL for login. No TLS/SSL support found". I have found several posts about this error, but none of the information that I've found in them is useful. I have configured google talk correctly, and I don't have a router or firewall that is blocking google talk. I have tried reinstalling pidgin (I am using 1:2.2.1-1ubuntu4.1, btw) and, after reading a bug report, I also tried the following command:

```
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/firefox/ pidgin
```

I was greeted with the following impolite output:

```

*** glibc detected *** pidgin: double free or corruption (out): 0x0000000000ae44a0 ***
======= Backtrace: =========
/lib/libc.so.6[0x2b33c3892b0a]
/lib/libc.so.6(cfree+0x8c)[0x2b33c38966fc]
/usr/local/lib/libpurple.so.0(purple_ssl_close+0x45)[0x2b33c31bbf35]
/usr/local/lib/purple-2/libjabber.so.0(jabber_close+0x3b)[0x2b33ca56855b]
/usr/local/lib/libpurple.so.0(purple_connection_destroy+0xbd)[0x2b33c319163d]
/usr/local/lib/libpurple.so.0(purple_account_disconnect+0x41)[0x2b33c3182de1]
/usr/local/lib/libpurple.so.0[0x2b33c3191159]
/usr/lib/libglib-2.0.so.0[0x2b33c2ec170b]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2b33c2ec0fd3]
/usr/lib/libglib-2.0.so.0[0x2b33c2ec42dd]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2b33c2ec45ea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2b33c000b883]
pidgin(main+0x92f)[0x46fb3f]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2b33c383eb44]
pidgin[0x42ba79]
======= Memory map: ========
00400000-004b9000 r-xp 00000000 08:01 22595376                           /usr/local/bin/pidgin
006b8000-006be000 rw-p 000b8000 08:01 22595376                           /usr/local/bin/pidgin
006be000-00c80000 rw-p 006be000 00:00 0                                  [heap]
2b33bf52d000-2b33bf54a000 r-xp 00000000 08:01 15319351                   /lib/ld-2.6.1.so
2b33bf54a000-2b33bf54d000 rw-p 2b33bf54a000 00:00 0 
2b33bf54d000-2b33bf54e000 r--p 00000000 08:01 22479106                   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
2b33bf54e000-2b33bf555000 r--s 00000000 08:01 22430194                   /usr/lib/gconv/gconv-modules.cache
2b33bf555000-2b33bf556000 r--p 00000000 08:01 22479105                   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
2b33bf556000-2b33bf557000 r--p 00000000 08:01 22479104                   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
2b33bf557000-2b33bf558000 r--p 00000000 08:01 22479103                   /usr/lib/locale/en_US.utf8/LC_ADDRESS
2b33bf558000-2b33bf559000 r--p 00000000 08:01 22479961                   /usr/lib/locale/en_US.utf8/LC_NAME
2b33bf559000-2b33bf55a000 r--p 00000000 08:01 22479963                   /usr/lib/locale/en_US.utf8/LC_PAPER
2b33bf55a000-2b33bf55b000 r--p 00000000 08:01 22495242                   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2b33bf55b000-2b33bf55c000 r--p 00000000 08:01 22479102                   /usr/lib/locale/en_US.utf8/LC_MONETARY
2b33bf55c000-2b33bf63c000 r--p 00000000 08:01 22479048                   /usr/lib/locale/en_US.utf8/LC_COLLATE
2b33bf63c000-2b33bf63d000 r--p 00000000 08:01 22479101                   /usr/lib/locale/en_US.utf8/LC_TIME
2b33bf63d000-2b33bf63e000 r--p 00000000 08:01 22479863                   /usr/lib/locale/en_US.utf8/LC_NUMERIC
2b33bf63e000-2b33bf67d000 r--p 00000000 08:01 22479047                   /usr/lib/locale/en_US.utf8/LC_CTYPE
2b33bf749000-2b33bf74b000 rw-p 0001c000 08:01 15319351                   /lib/ld-2.6.1.so
2b33bf74b000-2b33bf753000 r-xp 00000000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2b33bf753000-2b33bf952000 ---p 00008000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2b33bf952000-2b33bf953000 rw-p 00007000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2b33bf953000-2b33bf96a000 r-xp 00000000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2b33bf96a000-2b33bfb6a000 ---p 00017000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2b33bfb6a000-2b33bfb6b000 rw-p 00017000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2b33bfb6b000-2b33bfb6f000 rw-p 2b33bfb6b000 00:00 0 
2b33bfb6f000-2b33bfcab000 r-xp 00000000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2b33bfcab000-2b33bfeaa000 ---p 0013c000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2b33bfeaa000-2b33bfeb4000 rw-p 0013b000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2b33bfeb4000-2b33bfeb5000 rw-p 2b33bfeb4000 00:00 0 
2b33bfeb5000-2b33c0286000 r-xp 00000000 08:01 22415748                   /usr/lib/libgtk-x11-2.0.so.0.1200.0
2b33c0286000-2b33c0485000 ---p 003d1000 08:01 22415748                   /usr/lib/libgtk-x11-2.0.so.0.1200.0
2b33c0485000-2b33c0491000 rw-p 003d0000 08:01 22415748                   /uAborted (core dumped)
adam@buttercup:~$ LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/firefox/ pidgin
*** glibc detected *** pidgin: free(): invalid pointer: 0x0000000000c52920 ***
======= Backtrace: =========
/lib/libc.so.6[0x2ac25c572b0a]
/lib/libc.so.6(cfree+0x8c)[0x2ac25c5766fc]
/usr/local/lib/libpurple.so.0(purple_ssl_close+0x45)[0x2ac25be9bf35]
/usr/local/lib/purple-2/libjabber.so.0(jabber_close+0x3b)[0x2ac26324855b]
/usr/local/lib/libpurple.so.0(purple_connection_destroy+0xbd)[0x2ac25be7163d]
/usr/local/lib/libpurple.so.0(purple_account_disconnect+0x41)[0x2ac25be62de1]
/usr/local/lib/libpurple.so.0[0x2ac25be71159]
/usr/lib/libglib-2.0.so.0[0x2ac25bba170b]
/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1c3)[0x2ac25bba0fd3]
/usr/lib/libglib-2.0.so.0[0x2ac25bba42dd]
/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1ca)[0x2ac25bba45ea]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xa3)[0x2ac258ceb883]
pidgin(main+0x92f)[0x46fb3f]
/lib/libc.so.6(__libc_start_main+0xf4)[0x2ac25c51eb44]
pidgin[0x42ba79]
======= Memory map: ========
00400000-004b9000 r-xp 00000000 08:01 22595376                           /usr/local/bin/pidgin
006b8000-006be000 rw-p 000b8000 08:01 22595376                           /usr/local/bin/pidgin
006be000-00c85000 rw-p 006be000 00:00 0                                  [heap]
2ac25820d000-2ac25822a000 r-xp 00000000 08:01 15319351                   /lib/ld-2.6.1.so
2ac25822a000-2ac25822d000 rw-p 2ac25822a000 00:00 0 
2ac25822d000-2ac25822e000 r--p 00000000 08:01 22479106                   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
2ac25822e000-2ac258235000 r--s 00000000 08:01 22430194                   /usr/lib/gconv/gconv-modules.cache
2ac258235000-2ac258236000 r--p 00000000 08:01 22479105                   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
2ac258236000-2ac258237000 r--p 00000000 08:01 22479104                   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
2ac258237000-2ac258238000 r--p 00000000 08:01 22479103                   /usr/lib/locale/en_US.utf8/LC_ADDRESS
2ac258238000-2ac258239000 r--p 00000000 08:01 22479961                   /usr/lib/locale/en_US.utf8/LC_NAME
2ac258239000-2ac25823a000 r--p 00000000 08:01 22479963                   /usr/lib/locale/en_US.utf8/LC_PAPER
2ac25823a000-2ac25823b000 r--p 00000000 08:01 22495242                   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
2ac25823b000-2ac25823c000 r--p 00000000 08:01 22479102                   /usr/lib/locale/en_US.utf8/LC_MONETARY
2ac25823c000-2ac25831c000 r--p 00000000 08:01 22479048                   /usr/lib/locale/en_US.utf8/LC_COLLATE
2ac25831c000-2ac25831d000 r--p 00000000 08:01 22479101                   /usr/lib/locale/en_US.utf8/LC_TIME
2ac25831d000-2ac25831e000 r--p 00000000 08:01 22479863                   /usr/lib/locale/en_US.utf8/LC_NUMERIC
2ac25831e000-2ac25835d000 r--p 00000000 08:01 22479047                   /usr/lib/locale/en_US.utf8/LC_CTYPE
2ac258429000-2ac25842b000 rw-p 0001c000 08:01 15319351                   /lib/ld-2.6.1.so
2ac25842b000-2ac258433000 r-xp 00000000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2ac258433000-2ac258632000 ---p 00008000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2ac258632000-2ac258633000 rw-p 00007000 08:01 22414504                   /usr/lib/libSM.so.6.0.0
2ac258633000-2ac25864a000 r-xp 00000000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2ac25864a000-2ac25884a000 ---p 00017000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2ac25884a000-2ac25884b000 rw-p 00017000 08:01 22414400                   /usr/lib/libICE.so.6.3.0
2ac25884b000-2ac25884f000 rw-p 2ac25884b000 00:00 0 
2ac25884f000-2ac25898b000 r-xp 00000000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2ac25898b000-2ac258b8a000 ---p 0013c000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2ac258b8a000-2ac258b94000 rw-p 0013b000 08:01 22415769                   /usr/lib/libxml2.so.2.6.30
2ac258b94000-2ac258b95000 rw-p 2ac258b94000 00:00 0 
2ac258b95000-2ac258f66000 r-xp 00000000 08:01 22415748                   /usr/lib/libgtk-x11-2.0.so.0.1200.0
2ac258f66000-2ac259165000 ---p 003d1000 08:01 22415748                   /usr/lib/libgtk-x11-2.0.so.0.1200.0
2ac259165000-Aborted (core dumped)

```

In case it matters, I am running the amd64 version of Ubuntu. Does anyone have any advice for me?

Thanks very much, and here is a gratuitous animated guitar player: :guitar:

Adam

---

### Post by jmmcd on 2008-01-22
Not sure about the backtrace you provided (try going back to your original $PATH), but I had the TLS/SSL problem, and this worked for me:

sudo apt-get install libgnutls-dev

(then restart, possibly even reinstall gaim/pidgin). Good luck.

(BTW how did I figure this out? I downloaded the latest pidgin source and ran ./configure on it -- it said 

[...]
SSL Library/Libraries......... : None. MSN, Novell Groupwise and Google Talk will not work without GnuTLS or NSS. OpenSSL is NOT usable!
[...]

So I ran:

$ apt-cache search gnutls

and found libgnutls-dev.)

---

### Post by nomenclature3000 on 2008-01-22
Thanks very much for your reply! I already had libgnutls installed but, just for the heck of it, I installed libgnutls-dev as well. I then restarted pidgin and got the same error. I then reinstalled pidgin and got the same error. I think that next I will try to build pidgin from the source. I will post my results here!

---

