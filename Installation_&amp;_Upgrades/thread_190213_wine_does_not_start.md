---
title: "wine does not start"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by fornix on 2006-06-06
Hi, Dont know if anyone else have this problem. I installed wine. Tried installing it through synaptic as well as apt-get. Next, when i type in winecfg, i get the following output
```

fornix@home:~$ winecfg
wine: creating configuration directory '/home/fornix/.wine'...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Xlib:  extension "GLX" missing on display ":0.0".
wine: Unhandled page fault on read access to 0x00000000 at address 0x7f4ee4ff (t
hread 0009), starting debugger...
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
Warning: Language 'en_IN' was not recognized, defaulting to 'en_US'.
WineDbg starting on pid 0x8
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information fo
r image C:\windows\rundll32.exe
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x7
f4ee4ff).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:1007 GS:0033
 EIP:7f4ee4ff ESP:7fb8fc0c EBP:7fb8fc48 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7c110758 ECX:b7f8f320 EDX:7c013ce8
 ESI:7c013ce8 EDI:7c013ce8
Stack dump:
0x7fb8fc0c:  7c013ce8 7f5238e0 7c013ce8 7f4ecd56
0x7fb8fc1c:  7c013ce8 7c013ce8 7f617760 7c110770
0x7fb8fc2c:  7f54c3f3 7c013ce8 7c110774 00000001
0x7fb8fc3c:  7f6bc60c 7f6c3a34 00000000 7fb8fc68
0x7fb8fc4c:  7f682ee8 7c013ce8 7f6bc60c 7fb8fc68
0x7fb8fc5c:  7f6bc60c 7f6bc60c 00000001 7fb8fdb8
0200: sel=1007 base=7fe4a000 limit=00001fff 32-bit rw-
Backtrace:
=>1 0x7f4ee4ff in libgl.so.1 (+0x304ff) (0x7f4ee4ff)
  2 0x7f682ee8 X11DRV_GDI_Finalize+0x28 in winex11 (0x7f682ee8)
  3 0x7f69af1a DllMain+0x41 in winex11 (0x7f69af1a)
  4 0x7f6ab442 in winex11 (+0x5b442) (0x7f6ab442)
  5 0x7ff9c0e5 call_dll_entry_point+0x15 in ntdll (0x7ff9c0e5)
  6 0x7ff9cea7 in ntdll (+0x1cea7) (0x7ff9cea7)
  7 0x7ff9d16f in ntdll (+0x1d16f) (0x7ff9d16f)
  8 0x7fc59c1c ExitProcess+0x1b in kernel32 (0x7fc59c1c)
  9 0x7fbade2f in rundll32 (+0xde2f) (0x7fbade2f)
  10 0x7fc5b311 in kernel32 (+0x4b311) (0x7fc5b311)
  11 0xb7fbaddb wine_switch_to_stack+0x17 in libwine.so.1 (0xb7fbaddb)
0x7f4ee4ff: movl        0x0(%eax),%eax
Modules:
Module  Address                 Debug info      Name (89 modules)
ELF     0x7bf00000-7bf03000     Deferred        <wine-loader>
ELF     0x7e2f7000-7e310000     Deferred        advpack<elf>
  \-PE  0x7e300000-7e310000     \               advpack
ELF     0x7e458000-7e4b3000     Deferred        shlwapi<elf>
  \-PE  0x7e470000-7e4b3000     \               shlwapi
ELF     0x7e4b3000-7e57f000     Deferred        shell32<elf>
  \-PE  0x7e4d0000-7e57f000     \               shell32
ELF     0x7e57f000-7e5b0000     Deferred        uxtheme<elf>
  \-PE  0x7e590000-7e5b0000     \               uxtheme
ELF     0x7e5b0000-7e670000     Deferred        comctl32<elf>
  \-PE  0x7e5c0000-7e670000     \               comctl32
ELF     0x7e670000-7e6c2000     Deferred        dsound<elf>
  \-PE  0x7e680000-7e6c2000     \               dsound
ELF     0x7e6c2000-7e720000     Deferred        quartz<elf>
  \-PE  0x7e6e0000-7e720000     \               quartz
ELF     0x7e836000-7e84e000     Deferred        msacm<elf>
  \-PE  0x7e840000-7e84e000     \               msacm
ELF     0x7e84e000-7e892000     Deferred        wineoss<elf>
  \-PE  0x7e860000-7e892000     \               wineoss
ELF     0x7e8bc000-7e8e2000     Deferred        msvfw32<elf>
  \-PE  0x7e8c0000-7e8e2000     \               msvfw32
ELF     0x7e8e2000-7e978000     Deferred        oleaut32<elf>
  \-PE  0x7e900000-7e978000     \               oleaut32
ELF     0x7e978000-7ea09000     Deferred        ole32<elf>
  \-PE  0x7e990000-7ea09000     \               ole32
ELF     0x7ea09000-7ea91000     Deferred        winmm<elf>
  \-PE  0x7ea10000-7ea91000     \               winmm
ELF     0x7ea95000-7eaa9000     Deferred        avicap32<elf>
  \-PE  0x7eaa0000-7eaa9000     \               avicap32
ELF     0x7eaa9000-7ead0000     Deferred        devenum<elf>
  \-PE  0x7eac0000-7ead0000     \               devenum
ELF     0x7ebe1000-7ebf6000     Deferred        midimap<elf>
  \-PE  0x7ebf0000-7ebf6000     \               midimap
ELF     0x7ebf6000-7ec1c000     Deferred        msacm32<elf>
  \-PE  0x7ec00000-7ec1c000     \               msacm32
ELF     0x7ec1c000-7ec3b000     Deferred        iphlpapi<elf>
  \-PE  0x7ec20000-7ec3b000     \               iphlpapi
ELF     0x7ec3b000-7ec84000     Deferred        rpcrt4<elf>
  \-PE  0x7ec50000-7ec84000     \               rpcrt4
ELF     0x7ec84000-7ec98000     Deferred        lz32<elf>
  \-PE  0x7ec90000-7ec98000     \               lz32
ELF     0x7ec98000-7ecb1000     Deferred        version<elf>
  \-PE  0x7eca0000-7ecb1000     \               version
ELF     0x7ecb1000-7ed06000     Deferred        setupapi<elf>
  \-PE  0x7ecc0000-7ed06000     \               setupapi
ELF     0x7ed60000-7ed64000     Deferred        libxfixes.so.3
ELF     0x7ed64000-7ed6d000     Deferred        libxcursor.so.1
ELF     0x7ed6d000-7f4be000     Deferred        libglcore.so.1
ELF     0x7f4be000-7f536000     Export          libgl.so.1
ELF     0x7f536000-7f61c000     Deferred        libx11.so.6
ELF     0x7f61c000-7f629000     Deferred        libxext.so.6
ELF     0x7f629000-7f641000     Deferred        libice.so.6
ELF     0x7f641000-7f6c4000     Export          winex11<elf>
  \-PE  0x7f650000-7f6c4000     \               winex11
ELF     0x7f6c4000-7f6e3000     Deferred        libexpat.so.1
ELF     0x7f6e3000-7f711000     Deferred        libfontconfig.so.1
ELF     0x7f711000-7f725000     Deferred        libz.so.1
ELF     0x7f725000-7f78e000     Deferred        libfreetype.so.6
ELF     0x7f78e000-7f7ce000     Deferred        advapi32<elf>
  \-PE  0x7f7a0000-7f7ce000     \               advapi32
ELF     0x7f8a3000-7f954000     Deferred        gdi32<elf>
  \-PE  0x7f8c0000-7f954000     \               gdi32
ELF     0x7f954000-7fa80000     Deferred        user32<elf>
  \-PE  0x7f970000-7fa80000     \               user32
ELF     0x7fb93000-7fb9b000     Deferred        libxrender.so.1
PE      0x7fb9b000-7fbb0000     Export          rundll32
PE      0x7fba0000-7fbb0000     Export          rundll32
ELF     0x7fbb1000-7fbbb000     Deferred        libgcc_s.so.1
ELF     0x7fbee000-7fcf0000     Export          kernel32<elf>
  \-PE  0x7fc10000-7fcf0000     \               kernel32
ELF     0x7fe00000-7fe03000     Deferred        libxrandr.so.2
ELF     0x7fe03000-7fe08000     Deferred        libxxf86vm.so.1
ELF     0x7fe08000-7fe12000     Deferred        libnss_files.so.2
ELF     0x7fe12000-7fe1b000     Deferred        libnss_nis.so.2
ELF     0x7fe1b000-7fe30000     Deferred        libnsl.so.1
ELF     0x7fe30000-7fe39000     Deferred        libnss_compat.so.2
ELF     0x7fe3d000-7fe42000     Deferred        libxxf86dga.so.1
ELF     0x7fe42000-7fe4a000     Deferred        libsm.so.6
ELF     0x7fe4c000-7fe4e000     Deferred        libnvidia-tls.so.1
ELF     0x7fe4e000-7fe70000     Deferred        libm.so.6
ELF     0x7fe70000-7ff66000     Deferred        libwine_unicode.so.1
ELF     0x7ff66000-7ffe0000     Export          ntdll<elf>
  \-PE  0x7ff80000-7ffe0000     \               ntdll
ELF     0xb7e50000-b7e53000     Deferred        libxau.so.6
ELF     0xb7e60000-b7e63000     Deferred        libdl.so.2
ELF     0xb7e63000-b7f92000     Deferred        libc.so.6
ELF     0xb7f92000-b7fa4000     Deferred        libpthread.so.0
ELF     0xb7fb6000-b7fd0000     Export          libwine.so.1
ELF     0xb7fd3000-b7fe9000     Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) C:\windows\rundll32.exe
        00000009    0 <==

```
I have used wine on Dapper Drake Beta though without problems. Any help will be appreciated. Thanks

---

### Post by flip314 on 2006-06-06
Which repositories did you use?  I added the winehq repositories (from the FAQ on winehq.com), did an apt-get, and it ran just fine.

---

### Post by fornix on 2006-06-06
Not the problem of repositories i think. Because i have it installed fine. Still if you say so, i'll try reinstalling it.

---

### Post by fornix on 2006-06-06
The problem has been solved. It was nvidia driver problem. Thanks for the help.=D>

---

