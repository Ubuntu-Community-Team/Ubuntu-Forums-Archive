---
title: "MS Project on wine"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by stuppaz on 2007-07-02
Hi,
I need to install Ms Project through wine.
I did it, but when I run "wine WINPROJ.EXE", the program comes up but I catch the following error and the WINPROJ immage disappears.

fixme:imm:ImmGetOpenStatus (0x162af0): semi-stub
wine: Unhandled page fault on read access to 0x00000062 at address 0x303f1516 (thread 0047), starting debugger...
Unhandled exception: page fault on read access to 0x00000062 in 32-bit code (0x303f1516).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:303f1516 ESP:0033f154 EBP:0033f16c EFLAGS:00210202(   - 00      - -RI1)
 EAX:00000001 EBX:00000000 ECX:00000000 EDX:7eba5b84
 ESI:00000000 EDI:00000000
Stack dump:
0x0033f154:  00000000 0033f678 00000000 00000000
0x0033f164:  00000000 00000001 0033f194 303f051d
0x0033f174:  000b0028 00000200 00000000 00190001
0x0033f184:  308c6179 300462b7 00000282 00000000
0x0033f194:  0033f66c 300448dc 0033f674 0033f678
0x0033f1a4:  0033f67c 0033f680 0033f668 000b0028
Backtrace:
=>1 0x303f1516 in winproj (+0x3f1516) (0x0033f16c)
  2 0x303f051d in winproj (+0x3f051d) (0x0033f194)
  3 0x300448dc in winproj (+0x448dc) (0x0033f66c)
  4 0x7eb662ea WINPROC_wrapper+0x1a() in user32 (0x0033f69c)
  5 0x7eb66a1e in user32 (+0xa6a1e) (0x0033f6dc)
  6 0x7eb6bad3 CallWindowProcW+0x53() in user32 (0x0033f71c)
  7 0x7eb333a8 in user32 (+0x733a8) (0x0033f78c)
  8 0x7eb37140 SendMessageTimeoutW+0x1a0() in user32 (0x0033f7fc)
  9 0x7eb371b0 SendMessageW+0x50() in user32 (0x0033f83c)
  10 0x7d583a23 in imm32 (+0x3a23) (0x0033f86c)
  11 0x7d583d41 ImmSetOpenStatus+0x71() in imm32 (0x0033f89c)
  12 0x303f1391 in winproj (+0x3f1391) (0x0033f8d8)
  13 0x3003cd35 in winproj (+0x3cd35) (0x0033f92c)
  14 0x3003567a in winproj (+0x3567a) (0x0033fe7c)
  15 0x300010c9 in winproj (+0x10c9) (0x0033ff08)
  16 0x7b87221e in kernel32 (+0x5221e) (0x0033ffe8)
  17 0xb7eab897 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x303f1516: cmpw        $0,0x62(%esi)
Modules:
Module  Address                 Debug info      Name (82 modules)
PE      2d500000-2d612000       Deferred        prjres9
PE      2d830000-2d876000       Deferred        atlconv
PE      30000000-30623000       Export          winproj
PE      308c0000-30e1c000       Deferred        mso9
ELF     7b800000-7b926000       Export          kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d2f1000-7d335000       Deferred        riched20<elf>
  \-PE  7d300000-7d335000       \               riched20
ELF     7d335000-7d349000       Deferred        lz32<elf>
  \-PE  7d340000-7d349000       \               lz32
ELF     7d349000-7d362000       Deferred        version<elf>
  \-PE  7d350000-7d362000       \               version
ELF     7d362000-7d383000       Deferred        cabinet<elf>
  \-PE  7d370000-7d383000       \               cabinet
ELF     7d383000-7d3cb000       Deferred        wininet<elf>
  \-PE  7d390000-7d3cb000       \               wininet
ELF     7d3cb000-7d401000       Deferred        urlmon<elf>
  \-PE  7d3d0000-7d401000       \               urlmon
ELF     7d401000-7d488000       Deferred        msi<elf>
  \-PE  7d410000-7d488000       \               msi
ELF     7d52d000-7d55f000       Deferred        uxtheme<elf>
  \-PE  7d530000-7d55f000       \               uxtheme
ELF     7d561000-7d566000       Deferred        libxfixes.so.3
ELF     7d566000-7d56f000       Deferred        libxcursor.so.1
ELF     7d56f000-7d58c000       Export          imm32<elf>
  \-PE  7d580000-7d58c000       \               imm32
ELF     7d58c000-7d592000       Deferred        libxrandr.so.2
ELF     7d592000-7d59a000       Deferred        libxrender.so.1
ELF     7d59a000-7d59d000       Deferred        libxinerama.so.1
ELF     7e19d000-7e3f3000       Deferred        i915_dri.so
ELF     7e3f3000-7e3fc000       Deferred        libdrm.so.2
ELF     7e3fc000-7e45c000       Deferred        libgl.so.1
ELF     7e45c000-7e461000       Deferred        libxdmcp.so.6
ELF     7e461000-7e464000       Deferred        libxau.so.6
ELF     7e464000-7e555000       Deferred        libx11.so.6
ELF     7e555000-7e563000       Deferred        libxext.so.6
ELF     7e563000-7e568000       Deferred        libxxf86vm.so.1
ELF     7e568000-7e580000       Deferred        libice.so.6
ELF     7e580000-7e589000       Deferred        libsm.so.6
ELF     7e589000-7e617000       Deferred        winex11<elf>
  \-PE  7e5a0000-7e617000       \               winex11
ELF     7e690000-7e6b0000       Deferred        libexpat.so.1
ELF     7e6b0000-7e6db000       Deferred        libfontconfig.so.1
ELF     7e6db000-7e6ef000       Deferred        libz.so.1
ELF     7e6ef000-7e75a000       Deferred        libfreetype.so.6
ELF     7e75a000-7e816000       Deferred        comctl32<elf>
  \-PE  7e760000-7e816000       \               comctl32
ELF     7e816000-7e86f000       Deferred        shlwapi<elf>
  \-PE  7e830000-7e86f000       \               shlwapi
ELF     7e86f000-7e964000       Deferred        shell32<elf>
  \-PE  7e880000-7e964000       \               shell32
ELF     7e964000-7e9ff000       Deferred        oleaut32<elf>
  \-PE  7e980000-7e9ff000       \               oleaut32
ELF     7e9ff000-7ea1e000       Deferred        mpr<elf>
  \-PE  7ea10000-7ea1e000       \               mpr
ELF     7ea1e000-7ea31000       Deferred        libresolv.so.2
ELF     7ea31000-7ea4f000       Deferred        iphlpapi<elf>
  \-PE  7ea40000-7ea4f000       \               iphlpapi
ELF     7ea4f000-7eaa4000       Deferred        rpcrt4<elf>
  \-PE  7ea60000-7eaa4000       \               rpcrt4
ELF     7eaa4000-7ebe0000       Export          user32<elf>
  \-PE  7eac0000-7ebe0000       \               user32
ELF     7ebe0000-7ec7a000       Deferred        ole32<elf>
  \-PE  7ebf0000-7ec7a000       \               ole32
ELF     7ec7a000-7ec86000       Deferred        libgcc_s.so.1
ELF     7ed7b000-7ee38000       Deferred        gdi32<elf>
  \-PE  7ed90000-7ee38000       \               gdi32
ELF     7ee38000-7ee7e000       Deferred        advapi32<elf>
  \-PE  7ee40000-7ee7e000       \               advapi32
ELF     7efac000-7efb7000       Deferred        libnss_files.so.2
ELF     7efb7000-7efce000       Deferred        libnsl.so.1
ELF     7efce000-7eff5000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d32000-b7d3b000       Deferred        libnss_compat.so.2
ELF     b7d3c000-b7d40000       Deferred        libdl.so.2
ELF     b7d40000-b7e81000       Deferred        libc.so.6
ELF     b7e82000-b7e99000       Deferred        libpthread.so.0
ELF     b7ea4000-b7fb5000       Export          libwine.so.1
ELF     b7fb7000-b7fd2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000001b (D) C:\Programmi\Microsoft Office\Office\WINPROJ.EXE
        00000047    0 <==
0000002a 
        00000037    0
        00000036    0
        00000035    0
        00000033    0
        00000025    0
        00000034    0
        0000002f    0
0000003b 
        00000043    0
        00000042    0
        00000041    0
        00000040    0
        0000003e    0
        0000003d    0
        0000003c    0
00000026 
        0000002e    0
        0000002d    0
        0000002c    0
        0000002b    0
        00000029    0
        00000028    0
        00000027    0
0000000d 
        00000015    0
        00000014    0
        00000013    0
        00000012    0
        00000010    0
        0000000f    0
        0000000e    0
0000000a 
        0000000c    0
        0000000b    0



I thing the problem could be linked to add correct natives dll using winecfg. 
For now I add olny riched20.dll. I don't know if the are others.

Help me please .... I need MS Project to work.

---

### Post by Mark Phelps on 2007-07-02
I have some Windows apps that I have to keep booting back into Windows to run, but my checking of the Wine Application DB ( at [http://www.winehq.org/](http://www.winehq.org/))  and the list at Frank's corner ( at [http://frankscorner.org/](http://frankscorner.org/)) didn't have them listed.  

Just looked at both of these and didn't see MS Project listed.

So, unless someone here has been able to get it to work, you're out of luck.

---

