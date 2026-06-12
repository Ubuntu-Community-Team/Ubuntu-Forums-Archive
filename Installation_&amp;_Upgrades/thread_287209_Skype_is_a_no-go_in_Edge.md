---
title: "Skype is a no-go in Edge"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by mr_fong on 2006-10-28
Who can take a look at this Skype backtrace and tell me what is wrong here after the Edge upgrade. Thanks --Hans

```
*** glibc detected *** skype: free(): invalid pointer: 0x08a9b158 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb74418bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7441a44]
/usr/lib/libstdc++.so.6(_ZdlPv+0x21)[0xb7200fc1]
/usr/lib/libstdc++.so.6(_ZNSs4_Rep10_M_destroyERKSaIcE+0x1d)[0xb71ddd3d]
/usr/lib/libscim-1.0.so.8[0xb6d73633]
/usr/lib/libscim-1.0.so.8(_ZN4scim20scim_get_module_listERSt6vectorISsSaISsEERKSs+0x37)[0xb6d748c7]
/usr/lib/libscim-1.0.so.8(_ZN4scim29scim_get_imengine_module_listERSt6vectorISsSaISsEE+0x45)[0xb6d6f0c5]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim23QScimInputContextGlobal10initializeEv+0x257)[0xb6e11cf7]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN4scim17QScimInputContextC1Ev+0x31e)[0xb6e13ace]
/usr/lib/qt3/plugins/inputmethods/libqscim.so(_ZN22ScimInputContextPlugin6createERK7QString+0x7e)[0xb6e0ccae]
/usr/lib/libqt-mt.so.3(_ZN26QInputContextPluginPrivate6createERK7QString+0x25)[0xb7bf701f]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0x94)[0xb7bf6bec]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext17changeInputMethodE7QString+0xc3)[0xb6f6a85b]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext5slaveEv+0x43)[0xb6f6aa0f]
/usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so(_ZN18QMultiInputContext15setHolderWidgetEP7QWidget+0x26)[0xb6f6ac7e]
/usr/lib/libqt-mt.so.3(_ZN20QInputContextFactory6createERK7QStringP7QWidget+0xb8)[0xb7bf6c10]
/usr/lib/libqt-mt.so.3(_ZN7QWidget18createInputContextEv+0x8f)[0xb7949a8d]
/usr/lib/libqt-mt.so.3(_ZN7QWidget17resetInputContextEv+0x1d)[0xb7949d93]
/usr/lib/libqt-mt.so.3(_ZN9QLineEdit7setTextERK7QString+0x1d)[0xb7aca19d]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setLineEditEP9QLineEdit+0x82)[0xb7a9149e]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox13setUpLineEditEv+0x60)[0xb7a8bd68]
/usr/lib/libqt-mt.so.3(_ZN9QComboBox11setEditableEb+0x67)[0xb7a8f021]
skype[0x81944a7]
skype[0x8078989]
skype[0x8075972]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb73f08cc]
skype(_ZN6QFrame10paintEventEP11QPaintEvent+0x6d)[0x806f7b1]
======= Memory map: ========
08048000-08988000 rwxp 00000000 03:02 1582266    /usr/bin/skype
08988000-08ab5000 rw-p 08988000 00:00 0          [heap]
b6b00000-b6b21000 rw-p b6b00000 00:00 0
b6b21000-b6c00000 ---p b6b21000 00:00 0
b6ce6000-b6d0a000 r-xp 00000000 03:02 1715416    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d0a000-b6d0b000 rw-p 00024000 03:02 1715416    /usr/lib/qt3/plugins/inputmethods/libqsimple.so
b6d0b000-b6de0000 r-xp 00000000 03:02 1586895    /usr/lib/libscim-1.0.so.8.1.0
b6de0000-b6dee000 rw-p 000d5000 03:02 1586895    /usr/lib/libscim-1.0.so.8.1.0
b6df2000-b6dfd000 r-xp 00000000 03:02 1715420    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6dfd000-b6dfe000 rw-p 0000a000 03:02 1715420    /usr/lib/qt3/plugins/inputmethods/libqxim.so
b6dfe000-b6e1c000 r-xp 00000000 03:02 1713013    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e1c000-b6e1d000 rw-p 0001e000 03:02 1713013    /usr/lib/qt3/plugins/inputmethods/libqscim.so
b6e1d000-b6e8e000 r--p 00000000 03:02 1808361    /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b6e8e000-b6eb8000 r-xp 00000000 03:02 1581028    /usr/lib/liblcms.so.1.0.15
b6eb8000-b6eb9000 rw-p 00029000 03:02 1581028    /usr/lib/liblcms.so.1.0.15
b6eb9000-b6ebc000 rw-p b6eb9000 00:00 0
b6ebc000-b6f27000 r-xp 00000000 03:02 1581030    /usr/lib/libmng.so.1.1.0.9
b6f27000-b6f2a000 rw-p 0006a000 03:02 1581030    /usr/lib/libmng.so.1.1.0.9
b6f32000-b6f34000 r-xp 00000000 03:02 1586896    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f34000-b6f35000 rw-p 00001000 03:02 1586896    /usr/lib/libscim-x11utils-1.0.so.8.1.0
b6f35000-b6f39000 r-xp 00000000 03:02 1715415    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f39000-b6f3a000 rw-p 00003000 03:02 1715415    /usr/lib/qt3/plugins/inputmethods/libqimsw-none.so
b6f3a000-b6f64000 r-xp 00000000 03:02 1581691    /usr/lib/libkdefx.so.4.2.0
b6f64000-b6f65000 rw-p 00029000 03:02 1581691    /usr/lib/libkdefx.so.4.2.0
b6f65000-b6f6e000 r-xp 00000000 03:02 1715414    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f6e000-b6f6f000 rw-p 00008000 03:02 1715414    /usr/lib/qt3/plugins/inputmethods/libqimsw-multi.so
b6f6f000-b6f74000 r-xp 00000000 03:02 1715413    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f74000-b6f75000 rw-p 00004000 03:02 1715413    /usr/lib/qt3/plugins/imageformats/libqmng.so
b6f75000-b6f93000 r-xp 00000000 03:02 1629358    /usr/lib/kde3/plugins/styles/plastik.so
b6f93000-b6f94000 rw-p 0001e000 03:02 1629358    /usr/lib/kde3/plugins/styles/plastik.so
b6f94000-b6f95000 ---p b6f94000 00:00 0
b6f95000-b7015000 rw-p b6f95000 00:00 0
b7015000-b7016000 r-xp 00000000 03:02 1905774    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7016000-b7017000 rw-p 00000000 03:02 1905774    /usr/lib/X11/locale/common/xlcUTF8Load.so.2.0.0
b7017000-b704a000 r--p 00000000 03:02 101194     /usr/lib/locale/en_US.utf8/LC_CTYPE
b704a000-b704b000 r--p 00000000 03:02 101195     /usr/lib/locale/en_US.utf8/LC_NUMERIC
b704b000-b7122000 r--p 00000000 03:02 101197     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7122000-b7124000 rw-p b7122000 00:00 0
b7124000-b7128000 r-xp 00000000 03:02 1580717    /usr/lib/libXfixes.so.3.1.0
b7128000-b7129000 rw-p 00003000 03:02 1580717    /usr/lib/libXfixes.so.3.1.0
b7129000-b7145000 r-xp 00000000 03:02 37472      /usr/lib/libexpat.so.1.0.0
b7145000-b7147000 rw-p 0001c000 03:02 37472      /usr/lib/libexpat.so.1.0.0
b7147000-b7148000 rw-p b7147000 00:00 0
b7148000-b714c000 r-xp 00000000 03:02 35477      /usr/lib/libXdmcp.so.6.0.0
b714c000-b714d000 rw-p 00003000 03:02 35477      /usr/lib/libXdmcp.so.6.0.0
b714d000-b714f000 r-xp 00000000 03:02 35475      /usr/lib/libXau.so.6.0.0
b714f000-b7150000 rw-p 00001000 03:02 35475      /usr/lib/libXau.so.6.0.0
b7150000-b7224000 r-xp 00000000 03:02 1579952    /usr/lib/libstdc++.so.6.0.8
b7224000-b7227000 r--p 000d4000 03:02 1579952    /usr/lib/libstdc++.so.6.0.8
b7227000-b7229000 rw-p 000d7000 03:02 1579952    /usr/lib/libstdc++.so.6.0.8
b7229000-b722f000 rw-p b7229000 00:00 0
b722f000-b7244000 r-xp 00000000 03:02 35471      /usr/lib/libICE.so.6.3.0
b7244000-b7245000 rw-p 00014000 03:02 35471      /usr/lib/libICE.so.6.3.0
b7245000-b7247000 rw-p b7245000 00:00 0
b7247000-b724f000 r-xp 00000000 03:02 35473      /usr/lib/libSM.so.6.0.0
b724f000-b7250000 rw-p 00007000 03:02 35473      /usr/lib/libSM.so.6.0.0
b7250000-b7251000 rw-p b7250000 00:00 0
b7251000-b72b8000 r-xp 00000000 03:02 37474      /usr/lib/libfreetype.so.6.3.10
b72b8000-b72bb000 rw-p 00067000 03:02 37474      /usr/lib/libfreetype.so.6.3.10
b72bb000-b72cc000 r-xp 00000000 03:02 1580139    /usr/lib/libXft.so.2.1.2
b72cc000-b72cd000 rw-p 00010000 03:02 1580139    /usr/lib/libXft.so.2.1.2
b72cd000-b72cf000 r-xp 00000000 03:02 1581066    /usr/lib/libXinerama.so.1.0.0
b72cf000-b72d0000 rw-p 00001000 03:02 1581066    /usr/lib/libXinerama.so.1.0.0
b72d0000-b72d8000 r-xp 00000000 03:02 1581012    /usr/lib/libXcursor.so.1.0.2
b72d8000-b72d9000 rw-p 00007000 03:02 1581012    /usr/lib/libXcursor.so.1.0.2
b72d9000-b72db000 r-xp 00000000 03:02 1581085    /usr/lib/libXrandr.so.2.0.0
b72db000-b72dc000 rw-p 00002000 03:02 1581085    /usr/lib/libXrandr.so.2.0.0
b72dc000-b72e3000 r-xp 00000000 03:02 1580062    /usr/lib/libXrender.so.1.3.0
b72e3000-b72e4000 rw-p 00006000 03:02 1580062    /usr/lib/libXrender.so.1.3.0
b72e4000-b72e5000 rw-p b72e4000 00:00 0
b72e5000-b72ec000 r-xp 00000000 03:02 1580212    /usr/lib/libXi.so.6.0.0
b72ec000-b72ed000 rw-p 00006000 03:02 1580212    /usr/lib/libXi.so.6.0.0
b72ed000-b7300000 r-xp 00000000 03:02 1580669    /usr/lib/libz.so.1.2.3
b7300000-b7301000 rw-p 00012000 03:02 1580669    /usr/lib/libz.so.1.2.3
b7301000-b7323000 r-xp 00000000 03:02 37469      /usr/lib/libpng12.so.0.1.2.8
b7323000-b7324000 rw-p 00021000 03:02 37469      /usr/lib/libpng12.so.0.1.2.8
b7324000-b7342000 r-xp 00000000 03:02 1581949    /usr/lib/libjpeg.so.62.0.0
b7342000-b7343000 rw-p 0001d000 03:02 1581949    /usr/lib/libjpeg.so.62.0.0
b7343000-b738d000 r-xp 00000000 03:02 35487      /usr/lib/libXt.so.6.0.0
b738d000-b7391000 rw-p 00049000 03:02 35487      /usr/lib/libXt.so.6.0.0
b7391000-b73a6000 r-xp 00000000 03:02 35490      /usr/lib/libaudio.so.2.4
b73a6000-b73a7000 rw-p 00014000 03:02 35490      /usr/lib/libaudio.so.2.4
b73a7000-b73a8000 rw-p b73a7000 00:00 0
b73a8000-b73d1000 r-xp 00000000 03:02 1580670    /usr/lib/libfontconfig.so.1.0.4
b73d1000-b73d6000 rw-p 00028000 03:02 1580670    /usr/lib/libfontconfig.so.1.0.4
b73d6000-b73d7000 rw-p b73d6000 00:00 0
b73d7000-b73d9000 r-xp 00000000 03:02 277360     /lib/tls/i686/cmov/libdl-2.4.so
b73d9000-b73db000 rw-p 00001000 03:02 277360     /lib/tls/i686/cmov/libdl-2.4.so
b73db000-b7508000 r-xp 00000000 03:02 277357     /lib/tls/i686/cmov/libc-2.4.so
b7508000-b750a000 r--p 0012c000 03:02 277357     /lib/tls/i686/cmov/libc-2.4.so
b750a000-b750c000 rw-p 0012e000 03:02 277357     /lib/tls/i686/cmov/libc-2.4.so
b750c000-b750f000 rw-p b750c000 00:00 0
b750f000-b7519000 r-xp 00000000 03:02 1531099    /lib/libgcc_s.so.1
b7519000-b751a000 rw-p 00009000 03:02 1531099    /lib/libgcc_s.so.1
b751a000-b753e000 r-xp 00000000 03:02 277361     /lib/tls/i686/cmov/libm-2.4.so
b753e000-b7540000 rw-p 00023000 03:02 277361     /lib/tls/i686/cmov/libm-2.4.so
b7540000-b75f0000 r-xp 00000000 03:02 1582083    /usr/lib/libstdc++.so.5.0.7
b75f0000-b75f5000 rw-p 000af000 03:02 1582083    /usr/lib/libstdc++.so.5.0.7
b75f5000-b75fb000 rw-p b75f5000 00:00 0
b75fb000-b760a000 r-xp 00000000 03:02 277371     /lib/tls/i686/cmov/libpthread-2.4.so
b760a000-b760c000 rw-p 0000f000 03:02 277371     /lib/tls/i686/cmov/libpthread-2.4.so
b760c000-b760e000 rw-p b760c000 00:00 0
b760e000-b76d4000 r-xp 00000000 03:02 35485      /usr/lib/libX11.so.6.2.0
b76d4000-b76d7000 rw-p 000c5000 03:02 35485      /usr/lib/libX11.so.6.2.0
b76d7000-b76e3000 r-xp 00000000 03:02 1580209    /usr/lib/libXext.so.6.4.0
b76e3000-b76e4000 rw-p 0000c000 03:02 1580209    /usr/lib/libXext.so.6.4.0
b76e4000-b7e79000 r-xp 00000000 03:02 1581441    /usr/lib/libqt-mt.so.3.3.6
b7e79000-b7ec0000 rw-p 00794000 03:02 1581441    /usr/lib/libqt-mt.so.3.3.6
b7ec0000-b7ec3000 rw-p b7ec0000 00:00 0
b7ec3000-b7f76000 r-xp 00000000 03:02 35469      /usr/lib/libasound.so.2.0.0
b7f76000-b7f7b000 rw-p 000b2000 03:02 35469      /usr/lib/libasound.so.2.0.0
b7f7b000-b7f82000 r-xp 00000000 03:02 277373     /lib/tls/i686/cmov/librt-2.4.so
b7f82000-b7f84000 rw-p 00006000 03:02 277373     /lib/tls/i686/cmov/librt-2.4.so
b7f84000-b7f85000 rw-p b7f84000 00:00 0
b7f85000-b7f86000 r--p 00000000 03:02 98412      /usr/lib/locale/en_US.utf8/LC_TIME
b7f86000-b7f87000 r--p 00000000 03:02 98413      /usr/lib/locale/en_US.utf8/LC_MONETARY
b7f87000-b7f88000 r--p 00000000 03:02 101200     /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f88000-b7f89000 r--p 00000000 03:02 101221     /usr/lib/locale/en_US.utf8/LC_PAPER
b7f89000-b7f8a000 r--p 00000000 03:02 98414      /usr/lib/locale/en_US.utf8/LC_NAME
b7f8a000-b7f8b000 r--p 00000000 03:02 98415      /usr/lib/locale/en_US.utf8/LC_ADDRESS
b7f8b000-b7f8c000 r--p 00000000 03:02 98416      /usr/lib/locale/en_US.utf8/LC_TELEPHONE
b7f8c000-b7f8d000 r--p 00000000 03:02 98418      /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
b7f8d000-b7f94000 r--s 00000000 03:02 1613428    /usr/lib/gconv/gconv-modules.cache
b7f94000-b7f95000 r--p 00000000 03:02 98419      /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
b7f95000-b7f96000 rw-p b7f95000 00:00 0
b7f96000-b7faf000 r-xp 00000000 03:02 1532215    /lib/ld-2.4.so
b7faf000-b7fb1000 rw-p 00018000 03:02 1532215    /lib/ld-2.4.so
bfa6c000-bfa82000 rw-p bfa6c000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]
Aborted
```

---

### Post by Dinerty on 2006-10-28
Try installing skype this way in Edgy:

```
sudo gedit /etc/apt/sources.list
```

then add this

## skype (official)
## only uncomment it if you need it
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

then save file and close it, then

```
sudo apt-get update
```

then 

```
sudo apt-get install skype
```

---

### Post by mr_fong on 2006-10-28
Still a no-go, only no backtrace when you run Skype in a console. What is this different from downloading the deb from the Skype website? I tried that also, but again a no-go. What I want to know what glibc has against Skype (see the first line)? --Hans

---

### Post by Dinerty on 2006-10-28
Intresting .... do you use SCIM by any chance?, if so try

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype) and scroll down to "Invalid pointer section"

---

### Post by mr_fong on 2006-10-29
Hey there Dinerty, thanks for the help in pointing to the right solution. I am new to SCIM and didn't think it would have such an influence on other programs. This makes me wonder if my vmplayer problems are also related to SCIM.

Also funny that I didn't hit the page you pointed out while googling. All the key words are inthe page: skype, glibc, invalid pointer, ubuntu. Pity, because it could have saved us some postings in this forum.

--Hans

---

