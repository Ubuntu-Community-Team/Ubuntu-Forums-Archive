---
title: "Upgrading to Raring: Regression in Citrix ICAClient Wfica"
date: 2013-06-07
forum: Installation &amp; Upgrades
---

### Post by handheld-penguin on 2013-06-07
I upgraded to the latest Ubuntu at the weekend from being 2 versions old and now cannot use my Citrix client to remote into my other PC.

I try opening the Citrix client from both the web interface and the shell, it hangs for a bit and then disappears. Looking in /var/log/kern.log I see a segfault.

Has anyone else experienced this regression and how can they fix it?

I've tried opening in gdb but there is no stack trace. The last thing in ltrace is Gtk_Main. I have the latest of all the libraries including libMotif. It worked perfectly well before my update.

I thought it might be my graphics card to so I installed that and reverted to my integrated one - thus not using the dreaded Nvidia drivers. All to no avail.

I tried running firefox and wfica in sudo, again to no avail.

Does anyone know what can be done? I've tried wfica 12.1 as well as 12.0 to the same effect.

---

### Post by handheld-penguin on 2013-06-11
I've reverted to the 32bit proper (i'm on a 64 bit machine). The 64 bit version just installs the 32 bit version anyway it seems. Still getting segfault. Seems to be doing a lot of polling.
strace gives:
```

send(17, "\27\3\1\0000b\302p'zVYu\205\361u\221\25\273'\317\200d_\2245\t?\35\342\r\277"..., 53, 0) = 53
poll([{fd=3, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"7\0\4\0n\1\240\5f\1\240\5\0\0\0\0009\0\4\0l\1\240\5n\1\240\5\377\377w\0"..., 52}, {NULL, 0}, {"", 0}], 3) = 52
recv(3, 0x8c345a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {7538, 61102529}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 1 ([{fd=4, revents=POLLIN}])
read(4, "\1\0\0\0\0\0\0\0", 16)         = 8
clock_gettime(CLOCK_MONOTONIC, {7538, 61216543}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
read(4, 0xff881fdc, 16)                 = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {7538, 61334179}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {7538, 61440689}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
poll([{fd=3, events=POLLIN|POLLOUT}], 1, 4294967295) = 1 ([{fd=3, revents=POLLOUT}])
writev(3, [{"(\0\4\0o\0\240\5\246\0\0\0\0\0\0\0", 16}, {NULL, 0}, {"", 0}], 3) = 16
poll([{fd=3, events=POLLIN}], 1, 4294967295) = 1 ([{fd=3, revents=POLLIN}])
recv(3, "\1\1\243\5\0\0\0\0\345\r\340\1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0", 4096, 0) = 32
recv(3, 0x8c345a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
recv(3, 0x8c345a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {7538, 61831088}) = 0
clock_gettime(CLOCK_MONOTONIC, {7538, 61871267}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {7538, 61943288}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {7538, 62021483}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {7538, 62095922}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {7538, 62164724}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=11, events=POLLIN}, {fd=17, events=POLLIN}], 4, 0) = 0 (Timeout)
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
[ Process PID=22349 runs in 32 bit mode. ]

```


ldd gives
```

opt/Citrix/ICAClient/wfica:
        linux-gate.so.1 =>  (0xf77a5000)
        libdl.so.2 => /lib/i386-linux-gnu/libdl.so.2 (0xf7775000)
        libasound.so.2 => /usr/lib/i386-linux-gnu/libasound.so.2 (0xf7682000)
        libgthread-2.0.so.0 => /usr/lib/i386-linux-gnu/libgthread-2.0.so.0 (0xf767f000)
        librt.so.1 => /lib/i386-linux-gnu/librt.so.1 (0xf7676000)
        libgtk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgtk-x11-2.0.so.0 (0xf720d000)
        libgdk-x11-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0 (0xf715f000)
        libatk-1.0.so.0 => /usr/lib/i386-linux-gnu/libatk-1.0.so.0 (0xf713d000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/i386-linux-gnu/libgdk_pixbuf-2.0.so.0 (0xf711a000)
        libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf70d7000)
        libpangocairo-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangocairo-1.0.so.0 (0xf70ca000)
        libpango-1.0.so.0 => /usr/lib/i386-linux-gnu/libpango-1.0.so.0 (0xf707f000)
        libcairo.so.2 => /usr/lib/i386-linux-gnu/libcairo.so.2 (0xf6f67000)
        libgobject-2.0.so.0 => /usr/lib/i386-linux-gnu/libgobject-2.0.so.0 (0xf6f17000)
        libgmodule-2.0.so.0 => /usr/lib/i386-linux-gnu/libgmodule-2.0.so.0 (0xf6f12000)
        libglib-2.0.so.0 => /lib/i386-linux-gnu/libglib-2.0.so.0 (0xf6e11000)
        libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf6df6000)
        libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf6c42000)
        libX11.so.6 => /usr/lib/i386-linux-gnu/libX11.so.6 (0xf6b0b000)
        libXext.so.6 => /usr/lib/i386-linux-gnu/libXext.so.6 (0xf6af9000)
        libXrender.so.1 => /usr/lib/i386-linux-gnu/libXrender.so.1 (0xf6aef000)
        libXinerama.so.1 => /usr/lib/i386-linux-gnu/libXinerama.so.1 (0xf6aeb000)
        /lib/ld-linux.so.2 (0xf77a6000)
        libXfixes.so.3 => /usr/lib/i386-linux-gnu/libXfixes.so.3 (0xf6ae3000)
        libgio-2.0.so.0 => /usr/lib/i386-linux-gnu/libgio-2.0.so.0 (0xf697f000)
        libpangoft2-1.0.so.0 => /usr/lib/i386-linux-gnu/libpangoft2-1.0.so.0 (0xf696b000)
        libfontconfig.so.1 => /usr/lib/i386-linux-gnu/libfontconfig.so.1 (0xf6932000)
        libXi.so.6 => /usr/lib/i386-linux-gnu/libXi.so.6 (0xf6922000)
        libXrandr.so.2 => /usr/lib/i386-linux-gnu/libXrandr.so.2 (0xf6916000)
        libXcursor.so.1 => /usr/lib/i386-linux-gnu/libXcursor.so.1 (0xf690b000)
        libXcomposite.so.1 => /usr/lib/i386-linux-gnu/libXcomposite.so.1 (0xf6907000)
        libXdamage.so.1 => /usr/lib/i386-linux-gnu/libXdamage.so.1 (0xf6903000)
        libfreetype.so.6 => /usr/lib/i386-linux-gnu/libfreetype.so.6 (0xf6868000)
        libpixman-1.so.0 => /usr/lib/i386-linux-gnu/libpixman-1.so.0 (0xf67cd000)
        libpng12.so.0 => /lib/i386-linux-gnu/libpng12.so.0 (0xf67a4000)
        libxcb-shm.so.0 => /usr/lib/i386-linux-gnu/libxcb-shm.so.0 (0xf67a0000)
        libxcb-render.so.0 => /usr/lib/i386-linux-gnu/libxcb-render.so.0 (0xf6796000)
        libxcb.so.1 => /usr/lib/i386-linux-gnu/libxcb.so.1 (0xf6774000)
        libz.so.1 => /lib/i386-linux-gnu/libz.so.1 (0xf675a000)
        libffi.so.6 => /usr/lib/i386-linux-gnu/libffi.so.6 (0xf6753000)
        libpcre.so.3 => /lib/i386-linux-gnu/libpcre.so.3 (0xf6712000)
        libselinux.so.1 => /lib/i386-linux-gnu/libselinux.so.1 (0xf66f3000)
        libresolv.so.2 => /lib/i386-linux-gnu/libresolv.so.2 (0xf66dc000)
        libharfbuzz.so.0 => /usr/lib/i386-linux-gnu/libharfbuzz.so.0 (0xf6640000)
        libexpat.so.1 => /lib/i386-linux-gnu/libexpat.so.1 (0xf6618000)
        libXau.so.6 => /usr/lib/i386-linux-gnu/libXau.so.6 (0xf6614000)
        libXdmcp.so.6 => /usr/lib/i386-linux-gnu/libXdmcp.so.6 (0xf660d000)
        libicule.so.48 => /usr/lib/i386-linux-gnu/libicule.so.48 (0xf65d6000)
        libicuuc.so.48 => /usr/lib/i386-linux-gnu/libicuuc.so.48 (0xf6471000)
        libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf6388000)
        libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf636b000)
        libicudata.so.48 => /usr/lib/i386-linux-gnu/libicudata.so.48 (0xf51fa000)

```

---

### Post by handheld-penguin on 2013-06-11
moving to xfce, it seems to sometimes get stuck in a loop
```

aitpid(-1, 0xffaa2adc, WNOHANG)        = -1 ECHILD (No child processes)
gettimeofday({1370979372, 955535}, NULL) = 0
gettimeofday({1370979372, 955590}, NULL) = 0
select(0, NULL, NULL, NULL, {0, 10000}) = 0 (Timeout)
setsockopt(14, SOL_SOCKET, SO_ERROR, [11], 4) = -1 ENOPROTOOPT (Protocol not available)
recv(3, 0x92be5a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
recv(3, 0x92be5a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {929, 483855828}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=14, events=POLLIN}], 4, 90) = 0 (Timeout)
clock_gettime(CLOCK_MONOTONIC, {929, 574154421}) = 0
waitpid(-1, 0xffaa2adc, WNOHANG)        = -1 ECHILD (No child processes)
gettimeofday({1370979373, 56627}, NULL) = 0
gettimeofday({1370979373, 56675}, NULL) = 0
select(0, NULL, NULL, NULL, {0, 10000}) = 0 (Timeout)
setsockopt(14, SOL_SOCKET, SO_ERROR, [11], 4) = -1 ENOPROTOOPT (Protocol not available)
recv(3, 0x92be5a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
recv(3, 0x92be5a0, 4096, 0)             = -1 EAGAIN (Resource temporarily unavailable)
clock_gettime(CLOCK_MONOTONIC, {929, 584763187}) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=7, events=POLLIN}, {fd=14, events=POLLIN}], 4, 90^Z

```

---

### Post by handheld-penguin on 2013-06-11
And from valgrind
```

==4307== 
==4307== Conditional jump or move depends on uninitialised value(s)
==4307==    at 0x402E226: memcpy (in /usr/lib/valgrind/vgpreload_memcheck-x86-linux.so)
==4307==    by 0x80904B4: NewObject (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x8094158: InterpretTw2Cmd (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x808FE26: TwDispatchCmd (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80B4119: IcaVirtualWrite (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BBC5E: ReallyEmulProcessInput (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BC8C9: EmulProcessInput (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F7E6F: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307==    by 0x80C3F1F: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C6BDE: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C3599: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F73A1: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307== 
==4307== Use of uninitialised value of size 4
==4307==    at 0x402E226: memcpy (in /usr/lib/valgrind/vgpreload_memcheck-x86-linux.so)
==4307==    by 0x80904B4: NewObject (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x8094158: InterpretTw2Cmd (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x808FE26: TwDispatchCmd (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80B4119: IcaVirtualWrite (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BBC5E: ReallyEmulProcessInput (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BC8C9: EmulProcessInput (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F7E6F: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307==    by 0x80C3F1F: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C6BDE: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C3599: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F73A1: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307== 
==4307== Conditional jump or move depends on uninitialised value(s)
==4307==    at 0x80C3DE5: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C6BDE: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C3599: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F73A1: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307==    by 0x80C2FE3: WdPoll (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x81364EC: Call_WD (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80FAB32: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80FA5FC: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x490F106: ??? (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490E3B2: g_main_context_dispatch (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490E74F: ??? (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490EC2A: g_main_loop_run (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307== 
==4307== Conditional jump or move depends on uninitialised value(s)
==4307==    at 0x80C3E1E: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C6BDE: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C3599: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x75F73A1: ??? (in /opt/Citrix/ICAClient/PDCRYPT1.DLL)
==4307==    by 0x80C2FE3: WdPoll (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x81364EC: Call_WD (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80FAB32: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80FA5FC: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x490F106: ??? (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490E3B2: g_main_context_dispatch (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490E74F: ??? (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490EC2A: g_main_loop_run (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307== 
==4307== Conditional jump or move depends on uninitialised value(s)
==4307==    at 0x80C0EEC: EmulSetInformation (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C1402: WdSetInformation (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x81065D4: EngSrccCallback (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80E1ACD: SRCCRedrawRegion (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x810BFDA: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x812A6FB: NCSXWinRedrawRect (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x812A6BB: NCSXWinRedraw (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x812A931: X_GDK_event_filter (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x46220CD: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x462390A: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x46239BC: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x490E3B2: g_main_context_dispatch (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307== 
==4307== Conditional jump or move depends on uninitialised value(s)
==4307==    at 0x80BCA77: AppendICAPacket (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BD299: ??? (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80BD884: WD_send_unicode (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C0DE8: EmulSetInformation (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x80C1402: WdSetInformation (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x8106C34: wdUnicodeCode (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x812B602: do_unicode_key_up (in /opt/Citrix/ICAClient/wfica)
==4307==    by 0x46220CD: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x462390A: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x46239BC: ??? (in /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0.2400.17)
==4307==    by 0x490E3B2: g_main_context_dispatch (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307==    by 0x490E74F: ??? (in /lib/i386-linux-gnu/libglib-2.0.so.0.3600.0)
==4307== 
==4307== Use of uninitialised value of size 4
==4307==    at 0x812B609: do_unicode_key_up (in /opt/Citrix/ICAClient/wfica)
==4307== 
==4307== Jump to the invalid address stated on the next line
==4307==    at 0x0: ???
==4307==  Address 0x0 is not stack'd, malloc'd or (recently) free'd
==4307== 
==4307== 
==4307== Process terminating with default action of signal 11 (SIGSEGV)
==4307==  Bad permissions for mapped region at address 0x0
==4307==    at 0x0: ???



```

I'm suspicious of the libgdk

---

### Post by handheld-penguin on 2013-06-16
Thanks to a lot of googling and zeroes replies here I somehow fixed it.

* I forced downgrade to libgtk2 by removing libgtk3 doing something like this: [http://askubuntu.com/questions/18631/how-to-downgrade-gtk2-0-package-to-workaround-bug-693758](http://askubuntu.com/questions/18631/how-to-downgrade-gtk2-0-package-to-workaround-bug-693758)
* I remove the oxygen theme from kde: [http://askubuntu.com/questions/177909/restore-gtk-integration-after-removing-kde](http://askubuntu.com/questions/177909/restore-gtk-integration-after-removing-kde)
* Remove icaclient
* use gtkorphan to remove all deps
* reboot
* reinstall icaclient (12.1) along with all deps (be careful not to install libgtk2.0

lmk if you have any problems! This was a huge pain for me and wouldn't wish it upon anyone.

---

### Post by handheld-penguin on 2013-06-16
Upon even more investigation. Its the oxygen them. Just delete it and be done.

---

