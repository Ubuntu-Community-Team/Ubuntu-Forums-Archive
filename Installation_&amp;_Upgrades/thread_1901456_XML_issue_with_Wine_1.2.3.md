---
title: "XML issue with Wine 1.2.3"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by pdavison9241 on 2011-12-28
I have Ubuntu 11.10 and have just installed Wine 1.2.3.  I am now trying to install IDS 75 (which is Ford's diagnostic software) and am running into a problem.  It says upon trying to install that there is a file error - XML (CRequired).  The program will finish installing, but every time that I try to open it I will get a message that states XMLRegistryD.exe has encountered a serious problem.  I thought that it was an issue with my firewall, but I encounter the same problem even after I have turned the firewall off.  Any thoughts for a noob?

---

### Post by pdavison9241 on 2011-12-28
> **pdavison9241 said:**
> I have Ubuntu 11.10 and have just installed Wine 1.2.3.  I am now trying to install IDS 75 (which is Ford's diagnostic software) and am running into a problem.  It says upon trying to install that there is a file error - XML (CRequired).  The program will finish installing, but every time that I try to open it I will get a message that states XMLRegistryD.exe has encountered a serious problem.  I thought that it was an issue with my firewall, but I encounter the same problem even after I have turned the firewall off.  Any thoughts for a noob?

Here is the command line from Terminal:

paul@Lenovo-Escort:~$ env WINEPREFIX="/home/paul/.wine" wine C:\\Program\ Files\\Ford\ Motor\ Company\\IDS\\Runtime\\Tabman.exe 
fixme:process:SetProcessShutdownParameters (00000100, 00000001): partial stub.
fixme:msxml:domelem_setAttributeNode (0x1344c0)->(0x134558 0x75e7a8)
fixme:msxml:domelem_QueryInterface interface {df0b3d60-548f-101b-8e65-08002b2bd119} not implemented
wine: Unhandled exception 0xe06d7363 at address 0x7edba429 (thread 000b), starting debugger...
First chance exception: illegal instruction in 32-bit code (0x0075eaa0).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0075eaa0 ESP:0075e220 EBP:00000001 EFLAGS:00210216(  R- --  I   -A-P- )
 EAX:00000000 EBX:0075e6c8 ECX:00000000 EDX:00000000
 ESI:7efe3ff4 EDI:0075e6c8
Stack dump:
0x0075e220:  0075e238 0075e6c8 0075ea38 0075e358
0x0075e230:  0075e30c 004303e4 0075e6c8 0075e358
0x0075e240:  00000000 0075ea38 0075e6c8 7efe3ff4
0x0075e250:  0075e6c8 0075eaa0 0075e288 7efaa6f5
0x0075e260:  0075e6c8 0075eaa0 0075e358 0075e30c
0x0075e270:  0075e860 7efaa710 0075eaa0 7efc9398
Backtrace:
0x0075eaa0:     
Modules:
Module    Address            Debug info    Name (86 modules)
PE      400000-  44e000    Deferred        xmlregistryd
PE    10000000-10015000    Deferred        xmlregistry
PE    5d360000-5d36c000    Deferred        mfc90enu
PE    78480000-7850d000    Deferred        msvcp90
PE    78520000-785c3000    Deferred        msvcr90
PE    785e0000-786fd000    Deferred        mfc90
ELF    7bf00000-7bf04000    Deferred        <wine-loader>
ELF    7da8a000-7dac6000    Deferred        libxslt.so.1
ELF    7dafa000-7db5c000    Deferred        wininet<elf>
  \-PE    7db00000-7db5c000    \               wininet
ELF    7db5c000-7dd45000    Deferred        shell32<elf>
  \-PE    7db70000-7dd45000    \               shell32
ELF    7dd45000-7ddae000    Deferred        urlmon<elf>
  \-PE    7dd50000-7ddae000    \               urlmon
ELF    7ddae000-7defb000    Deferred        libxml2.so.2
ELF    7defb000-7df62000    Deferred        msxml3<elf>
  \-PE    7df00000-7df62000    \               msxml3
ELF    7dfa8000-7dfcd000    Deferred        mpr<elf>
  \-PE    7dfb0000-7dfcd000    \               mpr
ELF    7dfcd000-7dfe3000    Deferred        msxml4<elf>
  \-PE    7dfd0000-7dfe3000    \               msxml4
ELF    7dfe3000-7e019000    Deferred        uxtheme<elf>
  \-PE    7dff0000-7e019000    \               uxtheme
ELF    7e047000-7e04d000    Deferred        libxfixes.so.3
ELF    7e04d000-7e058000    Deferred        libxcursor.so.1
ELF    7e058000-7e05c000    Deferred        libxcomposite.so.1
ELF    7e05c000-7e065000    Deferred        libxrandr.so.2
ELF    7e065000-7e070000    Deferred        libxrender.so.1
ELF    7e070000-7e076000    Deferred        libxxf86vm.so.1
ELF    7e076000-7e07a000    Deferred        libxinerama.so.1
ELF    7e07a000-7e09d000    Deferred        imm32<elf>
  \-PE    7e080000-7e09d000    \               imm32
ELF    7e09d000-7e0a4000    Deferred        libxdmcp.so.6
ELF    7e0a4000-7e0a8000    Deferred        libxau.so.6
ELF    7e0a8000-7e0c7000    Deferred        libxcb.so.1
ELF    7e0c7000-7e0cd000    Deferred        libuuid.so.1
ELF    7e0cd000-7e0e7000    Deferred        libice.so.6
ELF    7e0e7000-7e21d000    Deferred        libx11.so.6
ELF    7e21d000-7e230000    Deferred        libxext.so.6
ELF    7e230000-7e239000    Deferred        libsm.so.6
ELF    7e249000-7e2f6000    Deferred        winex11<elf>
  \-PE    7e260000-7e2f6000    \               winex11
ELF    7e33f000-7e369000    Deferred        libexpat.so.1
ELF    7e369000-7e39e000    Deferred        libfontconfig.so.1
ELF    7e3ae000-7e3c3000    Deferred        libz.so.1
ELF    7e3c3000-7e45a000    Deferred        libfreetype.so.6
ELF    7e45a000-7e46e000    Deferred        lz32<elf>
  \-PE    7e460000-7e46e000    \               lz32
ELF    7e46e000-7e488000    Deferred        version<elf>
  \-PE    7e470000-7e488000    \               version
ELF    7e488000-7e4aa000    Deferred        iphlpapi<elf>
  \-PE    7e490000-7e4aa000    \               iphlpapi
ELF    7e4aa000-7e4da000    Deferred        ws2_32<elf>
  \-PE    7e4b0000-7e4da000    \               ws2_32
ELF    7e4da000-7e4f5000    Deferred        wsock32<elf>
  \-PE    7e4e0000-7e4f5000    \               wsock32
ELF    7e4f5000-7e5ed000    Deferred        comctl32<elf>
  \-PE    7e500000-7e5ed000    \               comctl32
ELF    7e5ed000-7e6f6000    Deferred        oleaut32<elf>
  \-PE    7e600000-7e6f6000    \               oleaut32
ELF    7e6f6000-7e772000    Deferred        rpcrt4<elf>
  \-PE    7e700000-7e772000    \               rpcrt4
ELF    7e772000-7e89a000    Deferred        ole32<elf>
  \-PE    7e790000-7e89a000    \               ole32
ELF    7e89a000-7e904000    Deferred        shlwapi<elf>
  \-PE    7e8b0000-7e904000    \               shlwapi
ELF    7e904000-7e966000    Deferred        advapi32<elf>
  \-PE    7e910000-7e966000    \               advapi32
ELF    7e966000-7e9fd000    Deferred        gdi32<elf>
  \-PE    7e970000-7e9fd000    \               gdi32
ELF    7e9fd000-7eb42000    Deferred        user32<elf>
  \-PE    7ea10000-7eb42000    \               user32
ELF    7eb42000-7eb4f000    Deferred        libnss_files.so.2
ELF    7eb4f000-7eb5b000    Deferred        libnss_nis.so.2
ELF    7eb5b000-7eb74000    Deferred        libnsl.so.1
ELF    7ed84000-7ef0e000    Deferred        kernel32<elf>
  \-PE    7eda0000-7ef0e000    \               kernel32
ELF    7ef0e000-7ef38000    Deferred        libm.so.6
ELF    7ef38000-7f000000    Deferred        ntdll<elf>
  \-PE    7ef50000-7f000000    \               ntdll
ELF    b7506000-b750b000    Deferred        libdl.so.2
ELF    b750b000-b7687000    Deferred        libc.so.6
ELF    b7688000-b76a3000    Deferred        libpthread.so.0
ELF    b76a8000-b76b2000    Deferred        libnss_compat.so.2
ELF    b76b3000-b77f5000    Deferred        libwine.so.1
ELF    b77f7000-b7817000    Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e services.exe
    0000001d    0
    00000014    0
    00000010    0
    0000000f    0
00000011 winedevice.exe
    00000017    0
    00000013    0
    00000012    0
00000018 TDSNetSetup.exe
    00000021    0
    0000001e    0
    0000001c    0
    00000019    0
0000001a explorer.exe
    0000001b    0
0000001f TDSNetConfig.exe
    0000003e    0
    0000003d    0
    00000035    0
    00000034    0
    0000002a    0
    00000020    0
0000002b CodeServeD.exe
    00000024    0
    00000032    0
    00000031    0
    0000002e    0
    0000002c    0
0000002f Tabman.exe
    00000040    0
00000028 (D) C:\Program Files\Ford Motor Company\IDS\Runtime\XMLRegistryD.exe
    0000000b    0 <==
    00000025    0
    00000023    0
Backtrace:
err:seh:raise_exception Unhandled exception code c000001d flags 0 addr 0x75eaa0
paul@Lenovo-Escort:~$

---

