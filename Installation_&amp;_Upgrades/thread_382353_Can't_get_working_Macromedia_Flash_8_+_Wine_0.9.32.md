---
title: "Can't get working Macromedia Flash 8 + Wine 0.9.32"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by baldercm on 2007-03-12
Hi!
I've just installed Wine + Macromedia Flash 8 following this tutorial
[http://web.archive.org/web/20060505145757/http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working]("http://web.archive.org/web/20060505145757/http://www.zwhlug.nl/content/wine_how_to_get_macromedia_dreamweaver_8_fireworks_8_and_flash_8_working")

I've coppied all the files from my VMWare Server Installation, exported/imported the registry and when I try to start Flash using
```
wine Flash.exe
```
I get this message
```
wine Flash.exe &
[1] 21310
balder@PortatilBalder:~/.wine/drive_c/Archivos de programa/Macromedia/Flash 8$ libGL warning: 3D driver claims to not support visual 0x4b
ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No existe el fichero ó directorio
libGL warning: 3D driver claims to not support visual 0x4b
err:shell:SHGetFileInfoW pidl is null!
fixme:wintab32:WTInfoW (0, 0, (nil)): stub
fixme:wininet:InternetGetConnectedState always returning LAN connection.
fixme:storage:StgCreateDocfile Transacted mode not implemented.
fixme:imm:ImmSetCandidateWindow (0x161dc0, 0x34bec0): stub
fixme:imm:ImmReleaseContext (0x100ce, 0x161dc0): stub
fixme:imm:ImmReleaseContext (0x100ce, 0x161dc0): stub
wine: Unhandled page fault on read access to 0x000007e0 at address 0x7e0 (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x000007e0 in 32-bit code (0x000007e0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:000007e0 ESP:0034e9dc EBP:00000000 EFLAGS:00210216(   - 00      -RIAP1)
 EAX:0000010a EBX:000003ef ECX:00000014 EDX:00000014
 ESI:00002254 EDI:01430478
Stack dump:
0x0034e9dc:  0000001f 00002254 0034eb4c 0034ead4
0x0034e9ec:  00000014 044166c8 00cb24a3 00002238
0x0034e9fc:  000003ef 00000000 05411e28 05411e28
0x0034ea0c:  0034eb4c 01b57b9f 00ccb2a3 01880000
0x0034ea1c:  00000000 00000001 04c8af14 00000000
0x0034ea2c:  00000000 01016b08 00002244 00000000
Backtrace:
=>1 0x000007e0 (0x00000000)
0x000007e0: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (124 modules)
PE      3d0000-3d8000   Deferred        emlaunch
PE      3f0000-3f7000   Deferred        flfile
PE      400000-154d000  Deferred        flash
PE      1990000-1d6a000 Deferred        flashresources
PE      1d70000-1e73000 Deferred        mfc71
PE      4c90000-4d92000 Deferred        mfc71u
PE      10000000-1022f000       Deferred        flash_8_video_extension
PE      12000000-121ae000       Deferred        xerces-c_2_6
PE      13000000-13191000       Deferred        mmxptresources
PE      30000000-30256000       Deferred        authplay
ELF     7b800000-7b926000       Deferred        kernel32<elf>
  \-PE  7b820000-7b926000       \               kernel32
ELF     7bc00000-7bc94000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc94000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
PE      7c340000-7c396000       Deferred        msvcr71
ELF     7cd6d000-7cd8c000       Deferred        wintab32<elf>
  \-PE  7cd70000-7cd8c000       \               wintab32
ELF     7d103000-7d123000       Deferred        mlang<elf>
  \-PE  7d110000-7d123000       \               mlang
ELF     7d123000-7d171000       Deferred        crypt32<elf>
  \-PE  7d130000-7d171000       \               crypt32
ELF     7d171000-7d18b000       Deferred        wsock32<elf>
  \-PE  7d180000-7d18b000       \               wsock32
ELF     7d18b000-7d1a0000       Deferred        midimap<elf>
  \-PE  7d190000-7d1a0000       \               midimap
PE      7d1b0000-7d1b8000       --none--        msacm32
ELF     7d1b8000-7d270000       Deferred        libasound.so.2
ELF     7d270000-7d29b000       Deferred        winealsa<elf>
  \-PE  7d280000-7d29b000       \               winealsa
ELF     7d29b000-7d2d7000       Deferred        wineoss<elf>
  \-PE  7d2a0000-7d2d7000       \               wineoss
ELF     7d2d7000-7d325000       Deferred        libgcrypt.so.11
ELF     7d325000-7d338000       Deferred        libtasn1.so.3
ELF     7d338000-7d366000       Deferred        libcrypt.so.1
ELF     7d872000-7d876000       Deferred        libgpg-error.so.0
ELF     7d886000-7d8f5000       Deferred        libgnutls.so.13
ELF     7d8f5000-7d924000       Deferred        libcups.so.2
ELF     7d93d000-7d96f000       Deferred        uxtheme<elf>
  \-PE  7d940000-7d96f000       \               uxtheme
ELF     7d971000-7d976000       Deferred        libxfixes.so.3
ELF     7d976000-7d97f000       Deferred        libxcursor.so.1
ELF     7d97f000-7d99d000       Deferred        ximcp.so.2
ELF     7d99d000-7d9a0000       Deferred        libxrandr.so.2
ELF     7d9a0000-7d9a8000       Deferred        libxrender.so.1
ELF     7d9a8000-7d9ab000       Deferred        libxinerama.so.1
ELF     7dfad000-7e1d8000       Deferred        i915_dri.so
ELF     7e1d8000-7e1df000       Deferred        libdrm.so.2
ELF     7e1df000-7e24e000       Deferred        libgl.so.1
ELF     7e24e000-7e317000       Deferred        libx11.so.6
ELF     7e317000-7e324000       Deferred        libxext.so.6
ELF     7e324000-7e33c000       Deferred        libice.so.6
ELF     7e33c000-7e3c9000       Deferred        winex11<elf>
  \-PE  7e350000-7e3c9000       \               winex11
ELF     7e3c9000-7e3e7000       Deferred        libexpat.so.1
ELF     7e3e7000-7e416000       Deferred        libfontconfig.so.1
ELF     7e416000-7e42a000       Deferred        libz.so.1
ELF     7e42a000-7e494000       Deferred        libfreetype.so.6
ELF     7e494000-7e4b6000       Deferred        oledlg<elf>
  \-PE  7e4a0000-7e4b6000       \               oledlg
ELF     7e4b6000-7e4d5000       Deferred        mpr<elf>
  \-PE  7e4c0000-7e4d5000       \               mpr
ELF     7e4d5000-7e51c000       Deferred        wininet<elf>
  \-PE  7e4e0000-7e51c000       \               wininet
ELF     7e51c000-7e548000       Deferred        ws2_32<elf>
  \-PE  7e520000-7e548000       \               ws2_32
ELF     7e548000-7e5e1000       Deferred        oleaut32<elf>
  \-PE  7e560000-7e5e1000       \               oleaut32
ELF     7e5e1000-7e5f5000       Deferred        msimg32<elf>
  \-PE  7e5f0000-7e5f5000       \               msimg32
ELF     7e5f5000-7e612000       Deferred        imm32<elf>
  \-PE  7e600000-7e612000       \               imm32
ELF     7e612000-7e627000       Deferred        psapi<elf>
  \-PE  7e620000-7e627000       \               psapi
ELF     7e627000-7e64e000       Deferred        msvfw32<elf>
  \-PE  7e630000-7e64e000       \               msvfw32
ELF     7e64e000-7e674000       Deferred        msacm32<elf>
ELF     7e674000-7e6ae000       Deferred        avifil32<elf>
  \-PE  7e680000-7e6ae000       \               avifil32
ELF     7e6ae000-7e73c000       Deferred        winmm<elf>
  \-PE  7e6c0000-7e73c000       \               winmm
ELF     7e73c000-7e750000       Deferred        lz32<elf>
  \-PE  7e740000-7e750000       \               lz32
ELF     7e750000-7e769000       Deferred        version<elf>
  \-PE  7e760000-7e769000       \               version
ELF     7e769000-7e79c000       Deferred        winspool<elf>
  \-PE  7e770000-7e79c000       \               winspool
ELF     7e79c000-7e83c000       Deferred        comdlg32<elf>
  \-PE  7e7a0000-7e83c000       \               comdlg32
ELF     7e83c000-7e8f8000       Deferred        comctl32<elf>
  \-PE  7e850000-7e8f8000       \               comctl32
ELF     7e8f8000-7e90b000       Deferred        libresolv.so.2
ELF     7e90b000-7e929000       Deferred        iphlpapi<elf>
  \-PE  7e910000-7e929000       \               iphlpapi
ELF     7e929000-7e97e000       Deferred        rpcrt4<elf>
  \-PE  7e940000-7e97e000       \               rpcrt4
ELF     7e97e000-7eab8000       Deferred        user32<elf>
  \-PE  7e9a0000-7eab8000       \               user32
ELF     7eab8000-7eb51000       Deferred        ole32<elf>
  \-PE  7ead0000-7eb51000       \               ole32
ELF     7eb51000-7eba9000       Deferred        shlwapi<elf>
  \-PE  7eb60000-7eba9000       \               shlwapi
ELF     7eba9000-7ec9d000       Deferred        shell32<elf>
  \-PE  7ebc0000-7ec9d000       \               shell32
ELF     7ec9d000-7eca8000       Deferred        libgcc_s.so.1
ELF     7eca8000-7ecaa000       Deferred        xlcutf8load.so.2
ELF     7ecaa000-7ecaf000       Deferred        libxdmcp.so.6
ELF     7ecaf000-7ecb8000       Deferred        libsm.so.6
ELF     7ed97000-7ee4e000       Deferred        gdi32<elf>
  \-PE  7edb0000-7ee4e000       \               gdi32
ELF     7ee4e000-7ee93000       Deferred        advapi32<elf>
  \-PE  7ee60000-7ee93000       \               advapi32
ELF     7efa9000-7efb4000       Deferred        libnss_files.so.2
ELF     7efb4000-7efca000       Deferred        libnsl.so.1
ELF     7efca000-7eff0000       Deferred        libm.so.6
ELF     7eff1000-7eff6000       Deferred        libxxf86vm.so.1
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7ca0000-b7ca3000       Deferred        libxau.so.6
ELF     b7ca4000-b7cad000       Deferred        libnss_compat.so.2
ELF     b7cae000-b7cb2000       Deferred        libdl.so.2
ELF     b7cb2000-b7de6000       Deferred        libc.so.6
ELF     b7de7000-b7dfa000       Deferred        libpthread.so.0
ELF     b7e0a000-b7f1b000       Deferred        libwine.so.1
ELF     b7f1d000-b7f38000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a
        0000000c    0
        0000000b    0
00000008 (D) C:\Archivos de programa\Macromedia\Flash 8\Flash.exe
        0000000f    0
        0000000e    0
        0000000d   15
        00000009    0 <==

[1]+  Done                    wine Flash.exe
```
I can see Flash's splash screen, but when it reaches the "Generating workspace" stage, it closes.

I hope somene can help me. Thank you!

---

