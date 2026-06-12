---
title: "Linux version of Bibble 5 Pro no longer launches"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GARoss on 2009-03-18
When 1st installed Ubuntu 8.10 AMD64 in early Feb the Nvidia driver was v177.??. I loaded a Linux beta version of Bibble 5 Pro & it worked fine.
Then, I dual booted with Ubuntu jaunty. Had problems with v180.35. Reloaded & used v173 (no 177 to be found). Now, I have v180.37 but for some reason Bibble 5 Pro will not launch. I re-check 8.10 (which also uses v180.35 via update) & it will not launch there, either. So, I don't believe it's an alpha problem but a driver issue & this has been confirmed @ the Bibble forum, too. 
Anyway, when launching from the terminal it reads;  

george@jauntygeorge-desktop:~$ bibble5pro
Using existing Pictures folder
Install Path:  /opt/bibble5pro
LD_PATH:       /opt/bibble5pro/lib:
	linux-gate.so.1 =>  (0xf7eee000)
	libkodakcms.so => /opt/bibble5pro/lib/libkodakcms.so (0xf7e72000)
	libuuid.so.1 => /opt/bibble5pro/lib/libuuid.so.1 (0x0070c000)
	libtcmalloc.so.0 => /opt/bibble5pro/lib/libtcmalloc.so.0 (0xf7e2c000)
	libQtScript.so.4 => /opt/bibble5pro/lib/libQtScript.so.4 (0xf7d0b000)
	libQtSvg.so.4 => /opt/bibble5pro/lib/libQtSvg.so.4 (0xf7cbf000)
	libQt3Support.so.4 => /opt/bibble5pro/lib/libQt3Support.so.4 (0xf79da000)
	libQtSql.so.4 => /opt/bibble5pro/lib/libQtSql.so.4 (0xf7940000)
	libQtOpenGL.so.4 => /opt/bibble5pro/lib/libQtOpenGL.so.4 (0xf78cb000)
	libGLU.so.1 => /usr/lib32/libGLU.so.1 (0xf7844000)
	libGL.so.1 => /usr/lib32/libGL.so.1 (0xf778a000)
	libQtNetwork.so.4 => /opt/bibble5pro/lib/libQtNetwork.so.4 (0xf768e000)
	libQtDesigner.so.4 => /opt/bibble5pro/lib/libQtDesigner.so.4 (0xf73b1000)
	libQtXml.so.4 => /opt/bibble5pro/lib/libQtXml.so.4 (0xf736c000)
	libQtGui.so.4 => /opt/bibble5pro/lib/libQtGui.so.4 (0xf6a84000)
	libpng12.so.0 => /usr/lib32/libpng12.so.0 (0xf6a5e000)
	libSM.so.6 => /usr/lib32/libSM.so.6 (0xf6a55000)
	libICE.so.6 => /usr/lib32/libICE.so.6 (0xf6a3c000)
	libXi.so.6 => /usr/lib32/libXi.so.6 (0xf6a32000)
	libXrender.so.1 => /usr/lib32/libXrender.so.1 (0xf6a28000)
	libXrandr.so.2 => /usr/lib32/libXrandr.so.2 (0xf6a20000)
	libfreetype.so.6 => /usr/lib32/libfreetype.so.6 (0xf69aa000)
	libfontconfig.so.1 => /usr/lib32/libfontconfig.so.1 (0xf697c000)
	libXext.so.6 => /usr/lib32/libXext.so.6 (0xf696d000)
	libX11.so.6 => /usr/lib32/libX11.so.6 (0xf687e000)
	libQtCore.so.4 => /opt/bibble5pro/lib/libQtCore.so.4 (0xf6659000)
	libz.so.1 => /usr/lib32/libz.so.1 (0xf6643000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf663d000)
	librt.so.1 => /lib32/librt.so.1 (0xf6633000)
	libglib-2.0.so.0 => /usr/lib32/libglib-2.0.so.0 (0xf657b000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf6577000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf655e000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf646f000)
	libm.so.6 => /lib32/libm.so.6 (0xf6449000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf6439000)
	libc.so.6 => /lib32/libc.so.6 (0xf62d6000)
	/lib/ld-linux.so.2 (0xf7eef000)
	libGLcore.so.1 => /usr/lib32/libGLcore.so.1 (0xf53bf000)
	libnvidia-tls.so.1 => /usr/lib32/tls/libnvidia-tls.so.1 (0xf53bd000)
	libexpat.so.1 => /usr/lib32/libexpat.so.1 (0xf5395000)
	libXau.so.6 => /usr/lib32/libXau.so.6 (0xf5391000)
	libxcb.so.1 => /usr/lib32/libxcb.so.1 (0xf5377000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf5345000)
	libXdmcp.so.6 => /usr/lib32/libXdmcp.so.6 (0xf533f000)
*** glibc detected *** ./bibblepro: free(): invalid pointer: 0x0a06af00 ***
======= Backtrace: =========
/lib32/libc.so.6[0xf6413204]
/lib32/libc.so.6(cfree+0x96)[0xf64151e6]
/usr/lib32/tls/libnvidia-tls.so.1[0xf548aaa0]
======= Memory map: ========
0070c000-0070f000 r-xp 00000000 08:07 263599                             /opt/bibble5pro/lib/libuuid.so
0070f000-00710000 rwxp 00002000 08:07 263599                             /opt/bibble5pro/lib/libuuid.so
08048000-08c7f000 r-xp 00000000 08:07 263608                             /opt/bibble5pro/bin/bibblepro
08c7f000-08c97000 rwxp 00c37000 08:07 263608                             /opt/bibble5pro/bin/bibblepro
08c97000-08cbc000 rwxp 08c97000 00:00 0 
09fe5000-0a165000 rwxp 09fe5000 00:00 0                                  [heap]
f540a000-f540c000 rwxp f540a000 00:00 0 
f540c000-f5410000 r-xp 00000000 08:07 61232                              /usr/lib32/libXdmcp.so.6.0.0
f5410000-f5411000 rwxp 00003000 08:07 61232                              /usr/lib32/libXdmcp.so.6.0.0
f5411000-f5412000 rwxp f5411000 00:00 0 
f5412000-f5442000 r-xp 00000000 08:07 53850                              /lib32/libpcre.so.3.12.1
f5442000-f5443000 r-xp 0002f000 08:07 53850                              /lib32/libpcre.so.3.12.1
f5443000-f5444000 rwxp 00030000 08:07 53850                              /lib32/libpcre.so.3.12.1
f5444000-f545c000 r-xp 00000000 08:07 61228                              /usr/lib32/libxcb.so.1.1.0
f545c000-f545d000 r-xp 00017000 08:07 61228                              /usr/lib32/libxcb.so.1.1.0
f545d000-f545e000 rwxp 00018000 08:07 61228                              /usr/lib32/libxcb.so.1.1.0
f545e000-f5460000 r-xp 00000000 08:07 61224                              /usr/lib32/libXau.so.6.0.0
f5460000-f5461000 r-xp 00001000 08:07 61224                              /usr/lib32/libXau.so.6.0.0
f5461000-f5462000 rwxp 00002000 08:07 61224                              /usr/lib32/libXau.so.6.0.0
f5462000-f5486000 r-xp 00000000 08:07 56584                              /usr/lib32/libexpat.so.1.5.2
f5486000-f5488000 r-xp 00023000 08:07 56584                              /usr/lib32/libexpat.so.1.5.2
f5488000-f5489000 rwxp 00025000 08:07 56584                              /usr/lib32/libexpat.so.1.5.2
f5489000-f548a000 rwxp f5489000 00:00 0 
f548a000-f548b000 r-xp 00000000 08:07 16293                              /usr/lib32/tls/libnvidia-tls.so.180.37
f548b000-f548c000 rwxp 00000000 08:07 16293                              /usr/lib32/tls/libnvidia-tls.so.180.37
f548c000-f61a5000 r-xp 00000000 08:07 16297                              /usr/lib32/libGLcore.so.180.37
f61a5000-f6396000 rwxp 00d19000 08:07 16297                              /usr/lib32/libGLcore.so.180.37
f6396000-f63a3000 rwxp f6396000 00:00 0 
f63a3000-f64ff000 r-xp 00000000 08:07 21759                              /lib32/libc-2.9.so
f64ff000-f6500000 ---p 0015c000 08:07 21759                              /lib32/libc-2.9.so
f6500000-f6502000 r-xp 0015c000 08:07 21759                              /lib32/libc-2.9.so
f6502000-f6503000 rwxp 0015e000 08:07 21759                              /lib32/libc-2.9.so
f6503000-f6506000 rwxp f6503000 00:00 0 
f6506000-f6513000 r-xp 00000000 08:07 13037                              /usr/lib32/libgcc_s.so.1
f6513000-f6514000 r-xp 0000c000 08:07 13037                              /usr/lib32/libgcc_s.so.1
f6514000-f6515000 rwxp 0000d000 08:07 13037                              /usr/lib32/libgcc_s.so.1
f6515000-f6516000 rwxp f6515000 00:00 0 
f6516000-f653a000 r-xp 00000000 08:07 21763                              /lib32/libm-2.9.so
f653a000-f653b000 r-xp 00023000 08:07 21763                              /lib32/libm-2.9.so
f653b000-f653c000 rwxp 00024000 08:07 21763                              /lib32/libm-2.9.so
f653c000-f6620000 r-xp 00000000 08:07 11919                              /usr/lib32/libstdc++.so.6.0.10
f6620000-f6624000 r-xp 000e3000 08:07 11919                              /usr/lib32/libstdc++.so.6.0.10
f6624000-f6625000 rwxp 000e7000 08:07 11919                              /usr/lib32/libstdc++.so.6.0.10
f6625000-f662b000 rwxp f6625000 00:00 0 
f662b000-f6640000 r-xp 00000000 08:07 21773                              /lib32/libpthread-2.9.so
f6640000-f6641000 r-xp 00014000 08:07 21773                              /lib32/libpthread-2.9.so
f6641000-f6642000 rwxp 00015000 08:07 21773                              /lib32/libpthread-2.9.so
f6642000-f6644000 rwxp f6642000 00:00 0 
f6644000-f6646000 r-xp 00000000 08:07 21762                              /lib32/libdl-2.9.so
f6646000-f6647000 r-xp 00001000 08:07 21762                              /lib32/libdl-2.9.so
f6647000-f6648000 rwxp 00002000 08:07 21762                              /lib32/libdl-2.9.so
f6648000-f66fe000 r-xp 00000000 08:07 56628                              /usr/lib32/libglib-2.0.so.0.1905.0
f66fe000-f66ff000 r-xp 000b5000 08:07 56628                              /usr/lib32/libglib-2.0.so.0.1905.0
f66ff000-f6700000 rwxp 000b6000 08:07 56628                              /usr/lib32/libglib-2.0.so.0.1905.0
f6700000-f6707000 r-xp 00000000 08:07 21775                              /lib32/librt-2.9.so
f6707000-f6708000 r-xp 00006000 08:07 21775                              /lib32/librt-2.9.so
f6708000-f6709000 rwxp 00007000 08:07 21775                              /lib32/librt-2.9.so
f6709000-f670a000 rwxp f6709000 00:00 0 
f670a000-f670e000 r-xp 00000000 08:07 56631                              /usr/lib32/libgthread-2.0.so.0.1905.0
f670e000-f670f000 r-xp 00003000 08:07 56631                              /usr/lib32/libgthread-2.0.so.0.1905.0
f670f000-f6710000 rwxp 00004000 08:07 56631                              /usr/lib32/libgthread-2.0.so.0.1905.0
f6710000-f6724000 r-xp 00000000 08:07 38164                              /usr/lib32/libz.so.1.2.3.3
f6724000-f6726000 rwxp 00013000 08:07 38164                              /usr/lib32/libz.so.1.2.3.3
f6726000-f6943000 r-xp 00000000 08:07 263604                             /opt/bibble5pro/lib/libQtCore.so.4
f6943000-f694a000 rwxp 0021d000 08:07 263604                             /opt/bibble5pro/lib/libQtCore.so.4
f694a000-f694b000 rwxp f694a000 00:00 0 
f694b000-f6a35000 r-xp 00000000 08:07 61223                              /usr/lib32/libX11.so.6.2.0
f6a35000-f6a36000 ---p 000ea000 08:07 61223                              /usr/lib32/libX11.so.6.2.0
f6a36000-f6a37000 r-xp 000ea000 08:07 61223                              /usr/lib32/libX11.so.6.2.0
f6a37000-f6a39000 rwxp 000eb000 08:07 61223                              /usr/lib32/libX11.so.6.2.0
f6a39000-f6a3a000 rwxp f6a39000 00:00 0 
f6a3a000-f6a47000 r-xp 00000000 08:07 61233                              /usr/lib32/libXext.so.6.4.0
f6a47000-f6a49000 rwxp 0000c000 08:07 61233                              /usr/lib32/libXext.so.6.4.0
f6a49000-f6a74000 r-xp 00000000 08:07 56592                              /usr/lib32/libfontconfig.so.1.3.0
f6a74000-f6a75000 r-xp 0002a000 08:07 56592                              /usr/lib32/libfontconfig.so.1.3.0
f6a75000-f6a76000 rwxp 0002b000 08:07 56592                              /usr/lib32/libfontconfig.so.1.3.0
f6a76000-f6a77000 rwxp f6a76000 00:00 0 
f6a77000-f6ae8000 r-xp 00000000 08:07 56593                              /usr/lib32/libfreetype.so.6.3.18
f6ae8000-f6aec000 r-xp 00070000 08:07 56593                              /usr/lib32/libfreetype.so.6.3.18
f6aec000-f6aed000 rwxp 00074000 08:07 56593                              /usr/lib32/libfreetype.so.6.3.18
f6aed000-f6af3000 r-xp 00000000 08:07 61243                              /usr/lib32/libXrandr.so.2.2.0
f6af3000-f6af4000 r-xp 00005000 08:07 61243                              /usr/lib32/libXrandr.so.2.2.0
f6af4000-f6af5000 rwxp 00006000 08:07 61243                              /usr/lib32/libXrandr.so.2.2.0
f6af5000-f6afd000 r-xp 00000000 08:07 61244                              /usr/lib32/libXrender.so.1.3.0
f6afd000-f6afe000 r-xp 00007000 08:07 61244                              /usr/lib32/libXrender.so.1.3.0
f6afe000-f6aff000 rwxp 00008000 08:07 61244                              /usr/lib32/libXrender.so.1.3.0
f6aff000-f6b07000 r-xp 00000000 08:07 61236                              /usr/lib32/libXi.so.6.0.0
f6b07000-f6b08000 r-xp 00007000 08:07 61236                              /usr/lib32/libXi.so.6.0.0
f6b08000-f6b09000 rwxp 00008000 08:07 61236       **Aborted (core dumped)**
george@jauntygeorge-desktop:~$

Aborted (core dumped)? What's happening?

---

### Post by GARoss on 2009-03-18
No question about it, it's the driver. 
Using v173 the program works. With v180.37 & v185.13 the program fails to launch.
Bummer!

---

### Post by GARoss on 2009-03-19
I have no idea how many will run across the error I have posted here but there is a fix other than running an older nVidia driver to fix a bug in Bibble 5 Pro, which was my solution. I found some good info from some fellow Linux users over at Bibble Support Forums ([http://support.bibblelabs.com](http://support.bibblelabs.com)) so give credit were it is due!.

Apparently, some libraries are missing in Bibble 5 Pro causing the software to fail to launch with any nVidia driver v180 & above including beta v185.13 (v173.14.16 & v177.82 do work). An explanation can be found here:

[http://support.bibblelabs.com/webboard/viewtopic.php?t=11977&postdays=0&postorder=asc&highlight=linux+nvidia&start=0&sid=30e684daa5c9918833739c587db10171](http://support.bibblelabs.com/webboard/viewtopic.php?t=11977&postdays=0&postorder=asc&highlight=linux+nvidia&start=0&sid=30e684daa5c9918833739c587db10171)

And here,

[http://support.bibblelabs.com/webboard/download.php?id=2498&sid=30e684daa5c9918833739c587db10171](http://support.bibblelabs.com/webboard/download.php?id=2498&sid=30e684daa5c9918833739c587db10171)

is where a number of lib files from an older 177.82 nVidia driver can be downloaded & pasted into /opt/bibble5pro/lib folder. The folder is root protected so you'll have to use Run Application to navigate to it, change permissions & paste the new libs.
I'm sure all this will be corrected once a full version of Bibble 5 Pro is released. For now, this will do.
HTH:P

---

