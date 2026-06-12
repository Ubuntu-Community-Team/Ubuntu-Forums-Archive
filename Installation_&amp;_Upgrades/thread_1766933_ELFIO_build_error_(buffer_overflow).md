---
title: "ELFIO build error (buffer overflow)"
date: 2011-05-25
forum: Installation &amp; Upgrades
---

### Post by rajatkhanduja on 2011-05-25
While building ELFIO (both ELFIO-1.0.2 and ELFIO-1.0.3) I face buffer overflow. Due to which, the building obviously fails.

These are the outputs

```

./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
configure: creating ./config.status
config.status: creating Makefile
config.status: creating ELFIO/Makefile
config.status: creating Examples/Makefile
config.status: creating Examples/ELFDump/Makefile
config.status: creating Examples/RelocationTable/Makefile
config.status: creating Examples/Writer/Makefile
config.status: creating Examples/WriteObj/Makefile
config.status: creating Examples/WriteObj2/Makefile
config.status: creating Examples/tutorial/Makefile
config.status: creating doc/Makefile
config.status: executing depfiles commands


```

```

$ make
Making all in ELFIO
make[1]: Entering directory `/home/rajat/Documents/Summer_Project/tars/ELFIO-1.0.3/ELFIO'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIDynamic.o -MD -MP -MF ".deps/ELFIDynamic.Tpo" -c -o ELFIDynamic.o ELFIDynamic.cpp; \
	then mv -f ".deps/ELFIDynamic.Tpo" ".deps/ELFIDynamic.Po"; else rm -f ".deps/ELFIDynamic.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIImpl.o -MD -MP -MF ".deps/ELFIImpl.Tpo" -c -o ELFIImpl.o ELFIImpl.cpp; \
	then mv -f ".deps/ELFIImpl.Tpo" ".deps/ELFIImpl.Po"; else rm -f ".deps/ELFIImpl.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFINote.o -MD -MP -MF ".deps/ELFINote.Tpo" -c -o ELFINote.o ELFINote.cpp; \
	then mv -f ".deps/ELFINote.Tpo" ".deps/ELFINote.Po"; else rm -f ".deps/ELFINote.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIO.o -MD -MP -MF ".deps/ELFIO.Tpo" -c -o ELFIO.o ELFIO.cpp; \
	then mv -f ".deps/ELFIO.Tpo" ".deps/ELFIO.Po"; else rm -f ".deps/ELFIO.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIOUtils.o -MD -MP -MF ".deps/ELFIOUtils.Tpo" -c -o ELFIOUtils.o ELFIOUtils.cpp; \
	then mv -f ".deps/ELFIOUtils.Tpo" ".deps/ELFIOUtils.Po"; else rm -f ".deps/ELFIOUtils.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIRelocation.o -MD -MP -MF ".deps/ELFIRelocation.Tpo" -c -o ELFIRelocation.o ELFIRelocation.cpp; \
	then mv -f ".deps/ELFIRelocation.Tpo" ".deps/ELFIRelocation.Po"; else rm -f ".deps/ELFIRelocation.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFISection.o -MD -MP -MF ".deps/ELFISection.Tpo" -c -o ELFISection.o ELFISection.cpp; \
	then mv -f ".deps/ELFISection.Tpo" ".deps/ELFISection.Po"; else rm -f ".deps/ELFISection.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFISegment.o -MD -MP -MF ".deps/ELFISegment.Tpo" -c -o ELFISegment.o ELFISegment.cpp; \
	then mv -f ".deps/ELFISegment.Tpo" ".deps/ELFISegment.Po"; else rm -f ".deps/ELFISegment.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFIStrings.o -MD -MP -MF ".deps/ELFIStrings.Tpo" -c -o ELFIStrings.o ELFIStrings.cpp; \
	then mv -f ".deps/ELFIStrings.Tpo" ".deps/ELFIStrings.Po"; else rm -f ".deps/ELFIStrings.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFISymbols.o -MD -MP -MF ".deps/ELFISymbols.Tpo" -c -o ELFISymbols.o ELFISymbols.cpp; \
	then mv -f ".deps/ELFISymbols.Tpo" ".deps/ELFISymbols.Po"; else rm -f ".deps/ELFISymbols.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFODynamic.o -MD -MP -MF ".deps/ELFODynamic.Tpo" -c -o ELFODynamic.o ELFODynamic.cpp; \
	then mv -f ".deps/ELFODynamic.Tpo" ".deps/ELFODynamic.Po"; else rm -f ".deps/ELFODynamic.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFOImpl.o -MD -MP -MF ".deps/ELFOImpl.Tpo" -c -o ELFOImpl.o ELFOImpl.cpp; \
	then mv -f ".deps/ELFOImpl.Tpo" ".deps/ELFOImpl.Po"; else rm -f ".deps/ELFOImpl.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFONote.o -MD -MP -MF ".deps/ELFONote.Tpo" -c -o ELFONote.o ELFONote.cpp; \
	then mv -f ".deps/ELFONote.Tpo" ".deps/ELFONote.Po"; else rm -f ".deps/ELFONote.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFORelocation.o -MD -MP -MF ".deps/ELFORelocation.Tpo" -c -o ELFORelocation.o ELFORelocation.cpp; \
	then mv -f ".deps/ELFORelocation.Tpo" ".deps/ELFORelocation.Po"; else rm -f ".deps/ELFORelocation.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFOSection.o -MD -MP -MF ".deps/ELFOSection.Tpo" -c -o ELFOSection.o ELFOSection.cpp; \
	then mv -f ".deps/ELFOSection.Tpo" ".deps/ELFOSection.Po"; else rm -f ".deps/ELFOSection.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFOSegment.o -MD -MP -MF ".deps/ELFOSegment.Tpo" -c -o ELFOSegment.o ELFOSegment.cpp; \
	then mv -f ".deps/ELFOSegment.Tpo" ".deps/ELFOSegment.Po"; else rm -f ".deps/ELFOSegment.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFOString.o -MD -MP -MF ".deps/ELFOString.Tpo" -c -o ELFOString.o ELFOString.cpp; \
	then mv -f ".deps/ELFOString.Tpo" ".deps/ELFOString.Po"; else rm -f ".deps/ELFOString.Tpo"; exit 1; fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"ELFIO\" -DVERSION=\"1.0.3\"  -I. -I.     -g -O2 -MT ELFOSymbols.o -MD -MP -MF ".deps/ELFOSymbols.Tpo" -c -o ELFOSymbols.o ELFOSymbols.cpp; \
	then mv -f ".deps/ELFOSymbols.Tpo" ".deps/ELFOSymbols.Po"; else rm -f ".deps/ELFOSymbols.Tpo"; exit 1; fi
rm -f libELFIO.a
ar cru libELFIO.a ELFIDynamic.o ELFIImpl.o ELFINote.o ELFIO.o ELFIOUtils.o ELFIRelocation.o ELFISection.o ELFISegment.o ELFIStrings.o ELFISymbols.o ELFODynamic.o ELFOImpl.o ELFONote.o ELFORelocation.o ELFOSection.o ELFOSegment.o ELFOString.o ELFOSymbols.o 
*** buffer overflow detected ***: ar terminated
======= Backtrace: =========
/lib/libc.so.6(__fortify_fail+0x50)[0x40124980]
/lib/libc.so.6(+0xe487a)[0x4012387a]
/lib/libc.so.6(+0xe3fb8)[0x40122fb8]
/lib/libc.so.6(_IO_default_xsputn+0x9e)[0x400a9a2e]
/lib/libc.so.6(_IO_padn+0xd8)[0x4009d3b8]
/lib/libc.so.6(_IO_vfprintf+0x2b17)[0x4007ed27]
/lib/libc.so.6(__vsprintf_chk+0xad)[0x4012306d]
/lib/libc.so.6(__sprintf_chk+0x2d)[0x40122fad]
ar[0x8050355]
ar[0x804e6d3]
ar[0x8050cfe]
ar[0x8053a88]
ar[0x804b5cf]
ar[0x804c236]
/lib/libc.so.6(__libc_start_main+0xe7)[0x40055ce7]
ar[0x8049351]
======= Memory map: ========
08048000-080aa000 r-xp 00000000 08:07 214688     /usr/local/bin/ar
080aa000-080ab000 r--p 00061000 08:07 214688     /usr/local/bin/ar
080ab000-080ac000 rw-p 00062000 08:07 214688     /usr/local/bin/ar
09b4f000-09c3c000 rw-p 00000000 00:00 0          [heap]
40000000-4001c000 r-xp 00000000 08:07 496        /lib/ld-2.12.1.so
4001c000-4001d000 r--p 0001b000 08:07 496        /lib/ld-2.12.1.so
4001d000-4001e000 rw-p 0001c000 08:07 496        /lib/ld-2.12.1.so
4001e000-4001f000 r-xp 00000000 00:00 0          [vdso]
4001f000-40021000 rw-p 00000000 00:00 0 
40021000-40022000 r--p 0029c000 08:07 262293     /usr/lib/locale/locale-archive
40022000-40029000 r--s 00000000 08:07 159193     /usr/lib/gconv/gconv-modules.cache
40029000-40033000 rw-p 00000000 00:00 0 
4003f000-40196000 r-xp 00000000 08:07 821        /lib/libc-2.12.1.so
40196000-40197000 ---p 00157000 08:07 821        /lib/libc-2.12.1.so
40197000-40199000 r--p 00157000 08:07 821        /lib/libc-2.12.1.so
40199000-4019a000 rw-p 00159000 08:07 821        /lib/libc-2.12.1.so
4019a000-4019e000 rw-p 00000000 00:00 0 
4019e000-4039e000 r--p 00000000 08:07 262293     /usr/lib/locale/locale-archive
403bc000-403d6000 r-xp 00000000 08:07 885        /lib/libgcc_s.so.1
403d6000-403d7000 r--p 00019000 08:07 885        /lib/libgcc_s.so.1
403d7000-403d8000 rw-p 0001a000 08:07 885        /lib/libgcc_s.so.1
bfb47000-bfb68000 rw-p 00000000 00:00 0          [stack]
make[1]: *** [libELFIO.a] Aborted
make[1]: *** Deleting file `libELFIO.a'
make[1]: Leaving directory `/home/rajat/Documents/Summer_Project/tars/ELFIO-1.0.3/ELFIO'
make: *** [all-recursive] Error 1


```

---

### Post by rajatkhanduja on 2011-06-04
The problem was caused due to 'ranlib'. I removed the existing executable files for ranlib and re-installed binutils. That did the trick.

---

