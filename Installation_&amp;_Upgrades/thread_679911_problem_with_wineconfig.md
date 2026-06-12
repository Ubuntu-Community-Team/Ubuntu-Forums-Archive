---
title: "problem with wineconfig"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by babil on 2008-01-27
i'm using **GUTSY** 'n wine version "**wine-0.9.54**"

my wineconfig / wineprefixcreate crashes immediately with the following error message thus leaving me with no .wine directory in my $HOME.

this is the error message i'm getting:

> 
username@hostname:~$ wineprefixcreate
wine: Unhandled page fault on read access to 0x00000000 at address 0xb7d59583 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0xb7d59583).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:b7d59583 ESP:0033ed8c EBP:0033eda8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:b7e2eff4 ECX:00000000 EDX:00000000
 ESI:00000033 EDI:00000000
Stack dump:
0x0033ed8c:  b7d592c5 00000000 00000087 00000087
0x0033ed9c:  7eabd588 00000033 7eac43cc 0033ee38
0x0033edac:  7ea8354c 00000000 00000087 7c28cd50
0x0033edbc:  00000001 00000000 00000001 bfe1a138
0x0033edcc:  081572e7 08bd4538 7c28cd50 7c01ca90
0x0033eddc:  00000087 00000000 7c04fbc0 0033ef38
Backtrace:
=>1 0xb7d59583 strlen+0x33() in libc.so.6 (0x0033eda8)
  2 0x7ea8354c in winex11 (+0x4354c) (0x0033ee38)
  3 0x7ea86296 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033ef38)
  4 0x7ea98d64 in winex11 (+0x58d64) (0x0033f118)
  5 0x7eaa99b4 in winex11 (+0x699b4) (0x0033f138)
  6 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0033f158)
  7 0x7bc44b0a in ntdll (+0x34b0a) (0x0033f1e8)
  8 0x7bc44da4 in ntdll (+0x34da4) (0x0033f228)
  9 0x7bc47433 LdrLoadDll+0x67() in ntdll (0x0033f248)
  10 0x7b861f6a in kernel32 (+0x41f6a) (0x0033f4b8)
  11 0x7b862243 LoadLibraryExW+0x43() in kernel32 (0x0033f4d8)
  12 0x7b862322 LoadLibraryExA+0x43() in kernel32 (0x0033f4f8)
  13 0x7b862359 LoadLibraryA+0x2d() in kernel32 (0x0033f518)
  14 0x7ecc4439 in gdi32 (+0x24439) (0x0033f6a8)
  15 0x7ecbe164 CreateDCW+0x60() in gdi32 (0x0033f958)
  16 0x7ed6bc25 CreateIconFromResourceEx+0x6c1() in user32 (0x0033fa28)
  17 0x7ed6c1e4 in user32 (+0x2c1e4) (0x0033fa98)
  18 0x7ed6eb5a LoadImageW+0x45f() in user32 (0x0033fb38)
  19 0x7ed6f348 LoadImageA+0x1c0() in user32 (0x0033fc38)
  20 0x7ed6f4fa LoadCursorA+0x55() in user32 (0x0033fc68)
  21 0x7ed6368e in user32 (+0x2368e) (0x0033fc98)
  22 0x7ed636e1 in user32 (+0x236e1) (0x0033fcb8)
  23 0x7edd8a96 in user32 (+0x98a96) (0x0033fd68)
  24 0x7edecc74 in user32 (+0xacc74) (0x0033fd88)
  25 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  26 0x7bc44b0a in ntdll (+0x34b0a) (0x0033fe38)
  27 0x7bc44da4 in ntdll (+0x34da4) (0x0033fe78)
  28 0x7bc44e29 in ntdll (+0x34e29) (0x0033feb8)
  29 0x7bc4772f LdrInitializeThunk+0x27a() in ntdll (0x0033ff08)
  30 0x7b86e6a2 in kernel32 (+0x4e6a2) (0x0033ffe8)
  31 0xb7e701cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0xb7d59583 strlen+0x33 in libc.so.6: movl       0x0(%eax),%ecx
Modules:
Module  Address                 Debug info      Name (40 modules)
ELF     7b800000-7b925000       Export          kernel32<elf>
  \-PE  7b820000-7b925000       \               kernel32
ELF     7bc00000-7bca1000       Export          ntdll<elf>
  \-PE  7bc10000-7bca1000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d654000-7d65d000       Deferred        librt.so.1
ELF     7d65d000-7e866000       Deferred        fglrx_dri.so
ELF     7e866000-7e871000       Deferred        libgcc_s.so.1
ELF     7e871000-7e8ed000       Deferred        libgl.so.1
ELF     7e8ed000-7e8f2000       Deferred        libxdmcp.so.6
ELF     7e8f2000-7e8f5000       Deferred        libxau.so.6
ELF     7e8f5000-7e9e6000       Deferred        libx11.so.6
ELF     7e9e6000-7e9f4000       Deferred        libxext.so.6
ELF     7e9f4000-7e9f9000       Deferred        libxxf86vm.so.1
ELF     7e9f9000-7ea11000       Deferred        libice.so.6
ELF     7ea11000-7ea19000       Deferred        libsm.so.6
ELF     7ea36000-7eac5000       Export          winex11<elf>
  \-PE  7ea40000-7eac5000       \               winex11
ELF     7eb59000-7eb79000       Deferred        libexpat.so.1
ELF     7eb79000-7eba4000       Deferred        libfontconfig.so.1
ELF     7eba4000-7ebb9000       Deferred        libz.so.1
ELF     7ebb9000-7ec29000       Deferred        libfreetype.so.6
ELF     7ec46000-7ec90000       Deferred        advapi32<elf>
  \-PE  7ec50000-7ec90000       \               advapi32
ELF     7ec90000-7ed27000       Export          gdi32<elf>
  \-PE  7eca0000-7ed27000       \               gdi32
ELF     7ed27000-7ee5e000       Export          user32<elf>
  \-PE  7ed40000-7ee5e000       \               user32
ELF     7ee5e000-7ee72000       Deferred        rundll32<elf>
  \-PE  7ee60000-7ee72000       \               rundll32
ELF     7ef91000-7ef9c000       Deferred        libnss_files.so.2
ELF     7ef9c000-7efa6000       Deferred        libnss_nis.so.2
ELF     7efa6000-7efbe000       Deferred        libnsl.so.1
ELF     7efbe000-7efe3000       Deferred        libm.so.6
ELF     b7ce5000-b7ce9000       Deferred        libdl.so.2
ELF     b7ce9000-b7e33000       Export          libc.so.6
ELF     b7e34000-b7e4c000       Deferred        libpthread.so.0
ELF     b7e60000-b7e69000       Deferred        libnss_compat.so.2
ELF     b7e69000-b7f7d000       Export          libwine.so.1
ELF     b7f7f000-b7f9b000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000008 (D) c:\windows\system32\rundll32.exe
        00000009    0 <==
0000000a
        0000000b    0
Backtrace:
=>1 0xb7d59583 strlen+0x33() in libc.so.6 (0x0033eda8)
  2 0x7ea8354c in winex11 (+0x4354c) (0x0033ee38)
  3 0x7ea86296 X11DRV_setup_opengl_visual+0x3c() in winex11 (0x0033ef38)
  4 0x7ea98d64 in winex11 (+0x58d64) (0x0033f118)
  5 0x7eaa99b4 in winex11 (+0x699b4) (0x0033f138)
  6 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0033f158)
  7 0x7bc44b0a in ntdll (+0x34b0a) (0x0033f1e8)
  8 0x7bc44da4 in ntdll (+0x34da4) (0x0033f228)
  9 0x7bc47433 LdrLoadDll+0x67() in ntdll (0x0033f248)
  10 0x7b861f6a in kernel32 (+0x41f6a) (0x0033f4b8)
  11 0x7b862243 LoadLibraryExW+0x43() in kernel32 (0x0033f4d8)
  12 0x7b862322 LoadLibraryExA+0x43() in kernel32 (0x0033f4f8)
  13 0x7b862359 LoadLibraryA+0x2d() in kernel32 (0x0033f518)
  14 0x7ecc4439 in gdi32 (+0x24439) (0x0033f6a8)
  15 0x7ecbe164 CreateDCW+0x60() in gdi32 (0x0033f958)
  16 0x7ed6bc25 CreateIconFromResourceEx+0x6c1() in user32 (0x0033fa28)
  17 0x7ed6c1e4 in user32 (+0x2c1e4) (0x0033fa98)
  18 0x7ed6eb5a LoadImageW+0x45f() in user32 (0x0033fb38)
  19 0x7ed6f348 LoadImageA+0x1c0() in user32 (0x0033fc38)
  20 0x7ed6f4fa LoadCursorA+0x55() in user32 (0x0033fc68)
  21 0x7ed6368e in user32 (+0x2368e) (0x0033fc98)
  22 0x7ed636e1 in user32 (+0x236e1) (0x0033fcb8)
  23 0x7edd8a96 in user32 (+0x98a96) (0x0033fd68)
  24 0x7edecc74 in user32 (+0xacc74) (0x0033fd88)
  25 0x7bc4264d call_dll_entry_point+0x15() in ntdll (0x0033fda8)
  26 0x7bc44b0a in ntdll (+0x34b0a) (0x0033fe38)
  27 0x7bc44da4 in ntdll (+0x34da4) (0x0033fe78)
  28 0x7bc44e29 in ntdll (+0x34e29) (0x0033feb8)
  29 0x7bc4772f LdrInitializeThunk+0x27a() in ntdll (0x0033ff08)
  30 0x7b86e6a2 in kernel32 (+0x4e6a2) (0x0033ffe8)
  31 0xb7e701cf wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)




---

### Post by zvacet on 2008-01-27
Usualy winecfg should do the job.Maybe you want to try [this](http://www.wine-doors.org/wordpress/).

---

### Post by babil on 2008-01-27
thanks ... but if you dont have a .wine directory already, wine-door will apparently call wineconfig or wineprefixcreate ... thus producing the same crash

---

### Post by zvacet on 2008-01-28
Go to the synaptic and reinstall wine and see if then you get .wine folder.

---

### Post by babil on 2008-01-29
okey, seems like i've solved the problem by doing something which really doesn't make sense:

1. rm -rf $HOME/.wine*
2. apt-get remove --purge wine-doors
3. ctrl+alt+backspace
4. login ... wineconfig
5. voila !! ... wine creates the .wine directory !!!

seems like wine-door 0.1.1.2 and wine-0.9.54 has some compatibility issues to fix, not absolutely sure though, but for now, i'm keeping myself away from wine-doors.

---

