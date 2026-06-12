---
title: "Wine Error - Does not run Illustrator"
date: 2023-04-04
forum: Installation &amp; Upgrades
---

### Post by gastonritsuko7 on 2023-04-04
Hi everyone. I'm relatively new in the world of linux, despite of using it 2 years ago. I tried to install Adobe Illustrator with Wine, and when I tried to launch de app, got me that message:

Unhandled exception: page fault on read access to 0x00000000 in 64-bit code (0x000000006872cb85).
Register dump:
 rip:000000006872cb85 rsp:000000000021d100 rbp:000000000021d230 eflags:00010286 (  R- --  I S - -P- )
 rax:0000000000000000 rbx:000000000021d1a8 rcx:ffffffffffffffff rdx:0000000000000000
 rsi:00007fffffb9fc20 rdi:0000000000000000  r8:00000000073a1d40  r9:0000000000000028 r10:0000000000000000
 r11:00000000073a1d40 r12:0000000000000000 r13:000000000af81268 r14:0000000006849e00 r15:0000000000000000
Stack dump:
0x000000000021d100:  00000000073a1d40 0000000000000028
0x000000000021d110:  00000000073a1d40 000000000b123640
0x000000000021d120:  000000000b123bc0 000000000434fa60
0x000000000021d130:  00000000073a1d40 0000000000000000
0x000000000021d140:  00007fffffb9fc20 0000000000000000
0x000000000021d150:  0000000000000002 0000000000000000
0x000000000021d160:  fffffffffffffffe 0000000000000000
0x000000000021d170:  00007fffffb9fc20 fffffffffffffffe
0x000000000021d180:  000000006898b1f0 00000000687c7c79
0x000000000021d190:  00007fffffb9fc20 000000006898b170
0x000000000021d1a0:  0000000000000000 0000000000000000
0x000000000021d1b0:  fffffffffffffffe 0000000000000000
Backtrace:
=>0 0x000000006872cb85 EntryPoint+0xffffffffffffffff() in dvacore (0x000000000021d230)
0x000000006872cb85 EntryPoint+0xffffffffffffffff in dvacore: repne scasw	(%rsi)
Modules:
Module	Address					Debug info	Name (114 modules)
PE	          220000-          32c000	Deferred        shlwapi
PE	          330000-          398000	Deferred        bib
PE	          3a0000-          3f0000	Deferred        bibutils
PE	          400000-         2268000	Deferred        illustrator
PE	         2270000-         232a000	Deferred        msvcp100
PE	         2620000-         2dfc000	Deferred        agm
PE	         2e00000-         3247000	Deferred        cooltype
PE	         3250000-         37e0000	Deferred        mps
PE	         37e0000-         39b5000	Deferred        ace
PE	         39c0000-         3a34000	Deferred        adobexmp
PE	         3a40000-         3b5d000	Deferred        adobexmpfiles
PE	         3b60000-         3bcf000	Deferred        are
PE	         3bd0000-         3d3b000	Deferred        wrservices
PE	         3d40000-         3edb000	Deferred        adobelinguistic
PE	         3ee0000-         4010000	Deferred        icuuc40
PE	         4010000-         42ed000	Deferred        msvcrt
PE	         42f0000-         4a60000	Deferred        dvaui
PE	         4a60000-         4cea000	Deferred        comdlg32
PE	         4cf0000-         526c000	Deferred        comctl32
PE	         5270000-         55c1000	Deferred        dvaai
PE	         55d0000-         5a8f000	Deferred        dvaadameve
PE	         5a90000-         5b8f000	Deferred        boost_regex
PE	         5b90000-         5d21000	Deferred        exo
PE	         5d30000-         5f64000	Deferred        adobeowl
PE	         5f70000-         5fa5000	Deferred        axe8sharedexpat
PE	         5fb0000-         5fc2000	Deferred        adobesplashkit
PE	         5fd0000-         5fe7000	Deferred        msimg32
PE	         5ff0000-         624b000	Deferred        amtlib
PE	         6250000-         629a000	Deferred        jsproxy
PE	         62a0000-         62ef000	Deferred        ahclient
PE	         62f0000-         630a000	Deferred        alcid
PE	         77a0000-         7978000	Deferred        aires
PE	         8130000-         82b1000	Deferred        imslib
PE	         83d0000-         852e000	Deferred        wbemprox
PE	         8550000-         8954000	Deferred        windowscodecs
PE	         d060000-         d268000	Deferred        adobehunspellplugin
PE	         d270000-         d378000	Deferred        wrliloplugin
PE	         d380000-         d465000	Deferred        aiport
PE	         d470000-         dd54000	Deferred        adobepdfl
PE	         dd60000-         de44000	Deferred        jp2klib
PE	         de50000-         df0a000	Deferred        filterport
PE	         df10000-         e05e000	Deferred        pdfport
PE	         e390000-         e3d8000	Deferred        rasterize.aip
PE	         e3e0000-         e575000	Deferred        colorharmony.aip
PE	         e580000-         e5e4000	Deferred        controlpanel.aip
PE	        10000000-        100eb000	Deferred        axedomcore
PE	        4a900000-        4aa50000	Deferred        icuin40
PE	        4ad00000-        4ba47000	Deferred        icudt40
PE	        60600000-        60618000	Deferred        action.aip
PE	        60620000-        6079b000	Deferred        action panel.aip
PE	        60af0000-        60b03000	Deferred        artconverters.aip
PE	        60dc0000-        60f0a000	Deferred        beautifulstrokes.aip
PE	        60fe0000-        61032000	Deferred        pencil tool.aip
PE	        61090000-        610ba000	Deferred        brushmanager.aip
PE	        61540000-        61663000	Deferred        advapi32
PE	        61740000-        6198b000	Deferred        wininet
PE	        61b00000-        62019000	Deferred        actxprxy
PE	        62540000-        62553000	Deferred        flatten transparency.aip
PE	        62600000-        62680000	Deferred        foconversionsuite.aip
PE	        62680000-        62698000	Deferred        fwserver.aip
PE	        62dc0000-        63039000	Deferred        rpcrt4
PE	        63280000-        6329e000	Deferred        version
PE	        63800000-        63850000	Deferred        netprofm
PE	        639c0000-        63a11000	Deferred        shcore
PE	        63c80000-        63cc7000	Deferred        pathfinder suite.aip
PE	        63f10000-        64014000	Deferred        pdfsuite.aip
PE	        641c0000-        6425e000	Deferred        photoshop adapter.aip
PE	        64840000-        64b25000	Deferred        gdiplus
PE	        64cc0000-        651bd000	Deferred        oleaut32
PE	        65380000-        653a6000	Deferred        wtsapi32
PE	        65fb0000-        66037000	Deferred        slicing.aip
PE	        66fe0000-        671ec000	Deferred        userinterface.aip
PE	        67640000-        67652000	Deferred        psapi
PE	        67c80000-        67cbe000	Deferred        boost_filesystem
PE	        67db0000-        67dc8000	Deferred        boost_threads
PE	        67ea0000-        67ebd000	Deferred        boost_signals
PE	        67ec0000-        67ecc000	Deferred        boost_system
PE	        67ed0000-        67ee8000	Deferred        boost_date_time
PE	        68300000-        68480000	Deferred        combase
PE	        68500000-        685a2000	Deferred        uxtheme
PE	        686f0000-        689dc000	Export          dvacore
PE	        69070000-        691cb000	Deferred        dvaworkspace
PE	        69330000-        69339000	Deferred        spbasic
PE	        69400000-        69539000	Deferred        winhttp
PE	        69740000-        697b3000	Deferred        propsys
PE	        6a200000-        6a76f000	Deferred        ole32
PE	        6ae80000-        6af5f000	Deferred        msvcr100
PE	        6ba00000-        6baba000	Deferred        sechost
PE	        6bac0000-        6bca8000	Deferred        setupapi
PE	        6c7c0000-        6ceaa000	Deferred        gdi32
PE	        6ea40000-        6ea5f000	Deferred        dwmapi
PE	        6eb00000-        6f293000	Deferred        user32
PE	        6f880000-        6faec000	Deferred        dbghelp
PE	        70740000-        707a4000	Deferred        mpr
PE	        70940000-        70ca0000	Deferred        ucrtbase
PE	        71000000-        71061000	Deferred        imm32
PE	        7a850000-        7a854000	Deferred        opengl32
PE	        7b000000-        7b3f1000	Deferred        kernelbase
PE	        7b600000-        7b965000	Deferred        kernel32
PE	        7bc00000-        7bf33000	Deferred        ntdll
PE	       180000000-       18005f000	Deferred        logsession
PE	       241b90000-       241bb9000	Deferred        zlib1
PE	    7fad507f0000-    7fad507f3000	Deferred        dwrite
PE	    7fad50e40000-    7fad50e44000	Deferred        wined3d
PE	    7fad510a0000-    7fad510a4000	Deferred        dxgi
PE	    7fad51900000-    7fad51904000	Deferred        winex11
PE	    7fad51b10000-    7fad51b13000	Deferred        kerberos
PE	    7fad523c0000-    7fad523cb000	Deferred        winspool
PE	    7fad52420000-    7fad52cf1000	Deferred        shell32
PE	    7fad530c0000-    7fad530c4000	Deferred        dnsapi
PE	    7fad530e0000-    7fad530e4000	Deferred        ws2_32
PE	    7fad53120000-    7fad53124000	Deferred        iphlpapi
PE	    7fad53160000-    7fad53163000	Deferred        netapi32
PE	    7fad543f0000-    7fad543f3000	Deferred        secur32
Threads:
process  tid      prio (all id:s are in hex)
00000038 services.exe
	0000003c    0
	00000040    0
	00000054    0
	00000070    0
	00000088    0
	000000ac    0
	000000e0    0
00000044 winedevice.exe
	00000048    0
	0000005c    0
	00000060    0
	00000064    0
0000004c explorer.exe
	00000050    0
	000000c8    0
	000000cc    0
00000068 plugplay.exe
	0000006c    0
	00000074    0
	00000078    0
	0000007c    0
	00000098    0
00000080 winedevice.exe
	00000084    0
	0000008c    0
	00000090    0
	00000094    0
	000000a0    0
000000a4 svchost.exe
	000000a8    0
	000000b0    0
	000000b4    0
000000b8 IllustratorCC64.exe
	000000bc    0
000000d8 rpcss.exe
	000000dc    0
	000000e8    0
	000000ec    0
	000000f0    0
	000000f4    0
	000000f8    0
	00000134    0
00000128 (D) Z:\home\gaston\.illustratorCC17\IllustratorCC17\App\Illustrator64\Support Files\Contents\Windows\Illustrator.exe
	0000012c    0 <==
	00000130    0
	0000013c    0
	00000140    0
	0000014c    0
System information:
    Wine build: wine-6.0 (Ubuntu 6.0+repack-1ubuntu1)
    Platform: x86_64
    Version: Windows 7
    Host system: Linux
    Host version: 5.19.0-38-generic

I have installed before in linux mint, but i've changed to ubuntu 22.04 and now i can't. Can someone help me?

---

### Post by MAFoElffen on 2023-04-05
Have you tried this? [https://github.com/Gictorbit/illustratorCClinux](https://github.com/Gictorbit/illustratorCClinux)

Then again, Adobe Illustrator has a native Linux version... [https://www.educba.com/adobe-illustrator-for-linux/](https://www.educba.com/adobe-illustrator-for-linux/)

---

### Post by gastonritsuko7 on 2023-04-05
Yes, i've tried that link from github, in fact i've installed with that instructions but then pop up that error message.

On the other hand, i don't understand that link with an Adobe Illustrator for Linux, it has intructions for Windows. It's weird.

I think it's an error from Wine, but I can't identify what is.

---

### Post by MAFoElffen on 2023-04-05
Yes. Very weird. IDK. 

All through the article it says "For Linux"... but following their links to their own installation page and in the system requirements, it only says Windows and MacOS, That whole thing seems like a ghost chase. 

Sorry for posting that. I should have checked it closer, in more details, before posting it.

I checked at Adobe's Official site and they do not say they ever made a version for Linux.

Hmmmm. My KVM Server ate a PSU last night, or I would spin up a VM to test an install and see how it went. Waiting fro the stores to open up here to see what I can afford to shell out. Hopefully that is all that is wrong with it.

---

### Post by ajohnl on 2023-04-19
This site maintains a list of apps wine supports
[https://www.winehq.org/](https://www.winehq.org/)

There is also a support forum but they will insist that the latest version of wine is installed and help is rather limited anyway due to how Microsoft arrange their code.

There was also a utility available that installs a number of dll's but afraid I can't remember it' name.

Often a search for linux the win apps name brings up alternatives eg
[https://www.makeuseof.com/adobe-illustrator-alternatives-for-linux/](https://www.makeuseof.com/adobe-illustrator-alternatives-for-linux/)

---

