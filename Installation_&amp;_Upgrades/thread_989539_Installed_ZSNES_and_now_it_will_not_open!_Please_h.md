---
title: "Installed ZSNES and now it will not open! Please help!"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by Killswitch1981 on 2008-11-21
OK. I Sudo apt-get install zsnes. Thought i had it and got really excited about the game. Then I got this message:

> samantha@samantha-laptop:~$ sudo zsnes
ZSNES v1.51, (c) 1997-2007, ZSNES Team
Be sure to check [http://www.zsnes.com/](http://www.zsnes.com/) for the latest version.

ZSNES is written by the ZSNES Team (See AUTHORS.TXT)
ZSNES comes with ABSOLUTELY NO WARRANTY.  This is free software,
and you are welcome to redistribute it under certain conditions;
please read 'LICENSE.TXT' thoroughly before doing so.

Use ZSNES -? for command line definitions.

Starting Mouse detection.
ManyMouse: 3 mice detected.
Using ManyMouse for:
Mouse 0: AlpsPS/2 ALPS GlidePoint
Mouse 1: PS/2 Mouse
*** buffer overflow detected ***: zsnes terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x48)[0xb7d0b558]
/lib/tls/i686/cmov/libc.so.6[0xb7d09680]
zsnes[0x8056c1b]
======= Memory map: ========
08048000-08303000 r-xp 00000000 08:07 2158216    /usr/bin/zsnes
08303000-08304000 r--p 002ba000 08:07 2158216    /usr/bin/zsnes
08304000-08343000 rw-p 002bb000 08:07 2158216    /usr/bin/zsnes
08343000-088f7000 rw-p 08343000 00:00 0 
08ee7000-08f31000 rw-p 08ee7000 00:00 0          [heap]
b6bd1000-b7700000 rw-p b6bd1000 00:00 0 
b7700000-b7703000 r-xp 00000000 08:07 1957930    /lib/libcap.so.1.10
b7703000-b7704000 rw-p 00002000 08:07 1957930    /lib/libcap.so.1.10
b7704000-b7752000 r-xp 00000000 08:07 2156859    /usr/lib/libpulse.so.0.4.1
b7752000-b7753000 r--p 0004d000 08:07 2156859    /usr/lib/libpulse.so.0.4.1
b7753000-b7754000 rw-p 0004e000 08:07 2156859    /usr/lib/libpulse.so.0.4.1
b7754000-b7760000 r-xp 00000000 08:07 2156857    /usr/lib/libpulse-simple.so.0.0.1
b7760000-b7761000 r--p 0000b000 08:07 2156857    /usr/lib/libpulse-simple.so.0.0.1
b7761000-b7762000 rw-p 0000c000 08:07 2156857    /usr/lib/libpulse-simple.so.0.0.1
b7762000-b7784000 r-xp 00000000 08:07 2156171    /usr/lib/libaudiofile.so.0.0.2
b7784000-b7787000 rw-p 00021000 08:07 2156171    /usr/lib/libaudiofile.so.0.0.2
b7799000-b779a000 rw-p b7799000 00:00 0 
b779a000-b77c2000 r-xp 00000000 08:07 1958000    /lib/libpcre.so.3.12.1
b77c2000-b77c3000 r--p 00027000 08:07 1958000    /lib/libpcre.so.3.12.1
b77c3000-b77c4000 rw-p 00028000 08:07 1958000    /lib/libpcre.so.3.12.1
b77c4000-b7879000 r-xp 00000000 08:07 2157049    /usr/lib/libglib-2.0.so.0.1800.2
b7879000-b787a000 r--p 000b4000 08:07 2157049    /usr/lib/libglib-2.0.so.0.1800.2
b787a000-b787b000 rw-p 000b5000 08:07 2157049    /usr/lib/libglib-2.0.so.0.1800.2
b787b000-b787f000 r-xp 00000000 08:07 2157066    /usr/lib/libgthread-2.0.so.0.1800.2
b787f000-b7880000 r--p 00003000 08:07 2157066    /usr/lib/libgthread-2.0.so.0.1800.2
b7880000-b7881000 rw-p 00004000 08:07 2157066    /usr/lib/libgthread-2.0.so.0.1800.2
b7884000-b788d000 r-xp 00000000 08:07 2156328    /usr/lib/libesd.so.0.2.39
b788d000-b788e000 r--p 00008000 08:07 2156328    /usr/lib/libesd.so.0.2.39
b788e000-b788f000 rw-p 00009000 08:07 2156328    /usr/lib/libesd.so.0.2.39
b788f000-b7892000 r-xp 00000000 08:07 2179438    /usr/lib/ao/plugins-2/libalsa09.so
b7892000-b7894000 rw-p 00002000 08:07 2179438    /usr/lib/ao/plugins-2/libalsa09.so
b7894000-b78a9000 r-xp 00000000 08:07 2156046    /usr/lib/libICE.so.6.3.0
b78a9000-b78aa000 rw-p 00014000 08:07 2156046    /usr/lib/libICE.so.6.3.0
b78aa000-b78ac000 rw-p b78aa000 00:00 0 
b78ac000-b78f9000 r-xp 00000000 08:07 2156128    /usr/lib/libXt.so.6.0.0
b78f9000-b78fd000 rw-p 0004c000 08:07 2156128    /usr/lib/libXt.so.6.0.0
b78fd000-b7913000 r-xp 00000000 08:07 2157325    /usr/lib/libaudio.so.2.4
b7913000-b7914000 r--p 00015000 08:07 2157325    /usr/lib/libaudio.so.2.4
b7914000-b7915000 rw-p 00016000 08:07 2157325    /usr/lib/libaudio.so.2.4
b7915000-b7917000 r-xp 00000000 08:07 2179443    /usr/lib/ao/plugins-2/libpulse.so
b7917000-b7919000 rw-p 00001000 08:07 2179443    /usr/lib/ao/plugins-2/libpulse.so
b7919000-b791c000 r-xp 00000000 08:07 2157055    /usr/lib/libgmodule-2.0.so.0.1800.2
b791c000-b791d000 r--p 00002000 08:07 2157055    /usr/lib/libgmodule-2.0.so.0.1800.2
b791d000-b791e000 rw-p 00003000 08:07 2157055    /usr/lib/libgmodule-2.0.so.0.1800.2
b791e000-b7923000 r-xp 00000000 08:07 2157323    /usr/lib/libartsc.so.0.0.0
b7923000-b7924000 r--p 00004000 08:07 2157323    /usr/lib/libartsc.so.0.0.0
b7924000-b7925000 rw-p 00005000 08:07 2157323    /usr/lib/libartsc.so.0.0.0
b7925000-b7926000 r-xp 00000000 08:07 2179439    /usr/lib/ao/plugins-2/libarts.so
b7926000-b7928000 rw-p 00000000 08:07 2179439    /usr/lib/ao/plugins-2/libarts.so
b7928000-b7932000 r-xp 00000000 08:07 1975462    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7932000-b7933000 r--p 00009000 08:07 1975462    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7933000-b7934000 rw-p 0000a000 08:07 1975462    /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7934000-b793d000 r-xp 00000000 08:07 1975466    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b793d000-b793e000 r--p 00008000 08:07 1975466    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b793e000-b793f000 rw-p 00009000 08:07 1975466    /lib/tls/i686/cmov/libnss_nis-2.8.90.so
b793f000-b7954000 r-xp 00000000 08:07 1975456    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7954000-b7955000 r--p 00014000 08:07 1975456    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7955000-b7956000 rw-p 00015000 08:07 1975456    /lib/tls/i686/cmov/libnsl-2.8.90.so
b7956000-b7958000 rw-p b7956000 00:00 0 
b7958000-b795f000 r-xp 00000000 08:07 1975458    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b795f000-b7960000 r--p 00006000 08:07 1975458    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7960000-b7961000 rw-p 00007000 08:07 1975458    /lib/tls/i686/cmov/libnss_compat-2.8.90.so
b7961000-b7963000 rw-p b7961000 00:00 0 
b7963000-b7967000 r-xp 00000000 08:07 2156098    /usr/lib/libXdmcp.so.6.0.0
b7967000-b7968000 rw-p 00003000 08:07 2156098    /usr/lib/libXdmcp.so.6.0.0
b7968000-b796a000 r-xp 00000000 08:07 2156087    /usr/lib/libXau.so.6.0.0
b796a000-b796b000 rw-p 00001000 08:07 2156087    /usr/lib/libXau.so.6.0.0
b796b000-b796c000 rw-p b796b000 00:00 0 
b796c000-b7983000 r-xp 00000000 08:07 2157031    /usr/lib/libxcb.so.1.0.0
b7983000-b7984000 r--p 00016000 08:07 2157031    /usr/lib/libxcb.so.1.0.0
b7984000-b7985000 rw-p 00017000 08:07 2157031    /usr/lib/libxcb.so.1.0.0
b7985000-b7986000 r-xp 00000000 08:07 2157029    /usr/lib/libxcb-xlib.so.0.0.0
b7986000-b7987000 r--p 00000000 08:07 2157029    /usr/lib/libxcb-xlib.so.0.0.0
b7987000-b7988000 rw-p 00001000 08:07 2157029    /usr/lib/libxcb-xlib.so.0.0.0
b7988000-b798f000 r-xp 00000000 08:07 1975475    /lib/tls/i686/cmov/librt-2.8.90.so
b798f000-b7990000 r--p 00007000 08:07 1975475    /lib/tls/i686/cmov/librt-2.8.90.so
b7990000-b7991000 rw-p 00008000 08:07 1975475    /lib/tls/i686/cmov/librt-2.8.90.so
b7991000-b7998000 r-xp 00000000 08:07 2156298    /usr/lib/libdrm.so.2.3.1
b7998000-b7999000 r--p 00006000 08:07 2156298    /usr/lib/libdrm.so.2.3.1
b7999000-b799a000 rw-p 00007000 08:07 2156298    /usr/lib/libdrm.so.2.3.1
b799a000-b799e000 r-xp 00000000 08:07 2156104    /usr/lib/libXfixes.so.3.1.0
b799e000-b799f000 rw-p 00003000 08:07 2156104    /usr/lib/libXfixes.so.3.1.0
b799f000-b79a0000 rw-p b799f000 00:00 0 
b79a0000-b79a2000 r-xp 00000000 08:07 2156096    /usr/lib/libXdamage.so.1.1.0
b79a2000-b79a3000 rw-p 00001000 08:07 2156096    /usr/lib/libXdamage.so.1.1.0
b79a3000-b79a7000 r-xp 00000000 08:07 2156138    /usr/lib/libXxf86vm.so.1.0.0
b79a7000-b79a8000 r--p 00003000 08:07 2156138    /usr/lib/libXxf86vm.so.1.0.0
b79a8000-b79a9000 rw-p 00004000 08:07 2156138    /usr/lib/libXxf86vm.so.1.0.0
b79a9000-b79b6000 r-xp 00000000 08:07 2156102    /usr/lib/libXext.so.6.4.0
b79b6000-b79b8000 rw-p 0000c000 08:07 2156102    /usr/lib/libXext.so.6.4.0
b79b8000-b7aa3000 r-xp 00000000 08:07 2156081    /usr/lib/libX11.so.6.2.0
b7aa3000-b7aa4000 r--p 000ea000 08:07 2156081    /usr/lib/libX11.so.6.2.0
b7aa4000-b7aa6000 rw-p 000eb000 08:07 2156081    /usr/lib/libX11.so.6.2.0
b7aa6000-b7aa7000 rw-p b7aa6000 00:00 0 
b7aa7000-b7aba000 r-xp 00000000 08:07 2156284    /usr/lib/libdirect-1.0.so.0.1.0
b7aba000-b7abb000 r--p 00012000 08:07 2156284    /usr/lib/libdirect-1.0.so.0.1.0
b7abb000-b7abc000 rw-p 00013000 08:07 2156284    /usr/lib/libdirect-1.0.so.0.1.0
b7abc000-b7ac3000 r-xp 00000000 08:07 2156362    /usr/lib/libfusion-1.0.so.0.1.0
b7ac3000-b7ac4000 r--p 00006000 08:07 2156362    /usr/lib/libfusion-1.0.so.0.1.0
b7ac4000-b7ac5000 rw-p 00007000 08:07 2156362    /usr/lib/libfusion-1.0.so.0.1.0
b7ac5000-b7ac6000 rw-p b7ac5000 00:00 0 
b7ac6000-b7b2a000 r-xp 00000000 08:07 2156286    /usr/lib/libdirectfb-1.0.so.0.1.0
b7b2a000-b7b2b000 r--p 00063000 08:07 2156286    /usr/lib/libdirectfb-1.0.so.0.1.0
b7b2b000-b7b2c000 rw-p 00064000 08:07 2156286    /usr/lib/libdirectfb-1.0.so.0.1.0
b7b2c000-b7b2e000 r-xp 00000000 08:07 1975451    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b2e000-b7b2f000 r--p 00001000 08:07 1975451    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b2f000-b7b30000 rw-p 00002000 08:07 1975451    /lib/tls/i686/cmov/libdl-2.8.90.so
b7b30000-b7bf3000 r-xp 00000000 08:07 2156161    /usr/lib/lAborted

Now why on earth does it say aborted at the end? I'm very knew to Linux and any input would be greatly appreciated. What am I doing wrong??

---

### Post by taurus on 2008-11-21
Is there any reason you want to run that game as root?  What happens if you just run the game from a terminal by itself?

```
zsnes
```

---

### Post by Killswitch1981 on 2008-11-22
> **taurus said:**
> Is there any reason you want to run that game as root?  What happens if you just run the game from a terminal by itself?

```
zsnes
```
Yes I have tried running it without root and it says the same thing. I have removed it and installed it a couple of times and also get the same thing.

---

### Post by anders_c_ on 2008-11-22
I have the same problem...
Intrepid 32 bit

---

### Post by adibudeen on 2008-11-26
I just tried it and have the same problem.  I'm also using Intrepid 32bit.

---

### Post by shadov on 2008-11-27
Same problem here! Fresh install of 32 bit 8.10. Has anyone filed a bug report?

---

### Post by DirtDawg on 2008-11-27
I've said it before and I'll say it again. Give [Snes9x-gtk]("http://www.happypenguin.org/show?snes9x-gtk") a try. You will like. Debs and binaries [available here]("http://www.snes9x.com/phpbb2/viewtopic.php?p=22874").

---

### Post by shadov on 2008-11-27
It is possible to install an older version of zsnes, which works.

> **eltoozero said:**
> Sweet, yes in fact installing the Gutsy package for zsnes works.

Package download here: [http://packages.ubuntu.com/gutsy/i386/zsnes/download]("http://packages.ubuntu.com/gutsy/i386/zsnes/download")

You should freeze the package version using Synaptic so you're not stuck with software update killing your newly working zsnes.

System->Administration->Synaptic->
Select the packages you don't want to update
From packages menu -> select "Lock Version"
~or~
aptitude hold pkgname

Instructions stolen from: [http://ubuntuforums.org/showthread.php?p=1324502]("http://ubuntuforums.org/showthread.php?p=1324502")

:)

---

### Post by CTRLurself on 2008-11-27
personally I never had luck with Linux-based emulators, so I downloaded 

--Nester (NES emulator)
--PJ64 (N-64 emulator)
--Gens32 Surreal (Sega Genesis emulator)

and I can't remember what I used to use for SNES, but most of the emulators out for Windows work perfectly under WINE, This will probably simplify your search significantly.

The only one I've found so far that doesn't work is VBA (Video Boy Advanced), but there are other GBA emulators (made for windows) that work perfectly.

---

