---
title: "mono apps won't run after edgy upgrade"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by steven43126 on 2006-10-27
Just upgraded to edgy and my mono apps won't run :(
Here is an example of the output i get 

steven@pirate:/usr/bin$ beagle-search 

** (/usr/lib/beagle/Search.exe:23996): WARNING **: The following assembly referenced from /usr/lib/beagle/Search.exe could not be loaded:
     Assembly:   gnome-sharp    (assemblyref_index=10)
     Version:    2.16.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Search.exe:23996): WARNING **: Could not load file or assembly 'gnome-sharp, Version=2.16.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
*** glibc detected *** beagle-search: free(): invalid pointer: 0x081dbe44 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7d388bd]
/lib/tls/i686/cmov/libc.so.6(__libc_free+0x84)[0xb7d38a44]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb7e91b51]
beagle-search(mono_metadata_parse_mh_full+0x3d8)[0x80ddbcb]
beagle-search(mono_method_get_header+0x12f)[0x80e4af8]
beagle-search[0x8137533]
beagle-search[0x81390e8]
beagle-search[0x813957c]
beagle-search(mono_runtime_exec_main+0x5c)[0x80942b3]
beagle-search(mono_runtime_run_main+0x175)[0x80974de]
beagle-search(mono_main+0x1059)[0x805d35b]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc)[0xb7ce78cc]
beagle-search[0x805bdc1]
======= Memory map: ========
00001000-00051000 rw-p 00001000 00:00 0 
08048000-081be000 r-xp 00000000 03:04 36163      /usr/local/bin/mono
081be000-081c0000 rw-p 00176000 03:04 36163      /usr/local/bin/mono
081c0000-081d3000 rw-p 081c0000 00:00 0 
081d3000-081d4000 rwxp 081d3000 00:00 0 
081d4000-08271000 rw-p 081d4000 00:00 0 
b6d00000-b6d21000 rw-p b6d00000 00:00 0 
b6d21000-b6e00000 ---p b6d21000 00:00 0 
b6ebf000-b6ec9000 r-xp 00000000 03:46 10288      /lib/libgcc_s.so.1
b6ec9000-b6eca000 rw-p 00009000 03:46 10288      /lib/libgcc_s.so.1
b6edb000-b6ee6000 r-xp 00000000 03:04 2426164    /usr/lib/beagle/Beagle.dll
b6ee6000-b6f12000 r-xp 00000000 03:04 2540838    /usr/lib/mono/gac/gdk-sharp/1.0.0.0__35e10195dab3c99f/gdk-sharp.dll
b6f12000-b6fd5000 r-xp 00000000 03:04 114913     /usr/local/lib/mono/gac/System/1.0.5000.0__b77a5c561934e089/System.dll.mdb
b6fd5000-b708e000 r-xp 00000000 03:04 114912     /usr/local/lib/mono/gac/System/1.0.5000.0__b77a5c561934e089/System.dll
b708e000-b70a3000 r-xp 00000000 03:04 2540840    /usr/lib/mono/gac/atk-sharp/1.0.0.0__35e10195dab3c99f/atk-sharp.dll
b70a3000-b70ad000 r-xp 00000000 03:04 2540834    /usr/lib/mono/gac/glib-sharp/1.0.0.0__35e10195dab3c99f/glib-sharp.dll
b70ad000-b7176000 r-xp 00000000 03:04 2539965    /usr/lib/mono/gac/gtk-sharp/1.0.0.0__35e10195dab3c99f/gtk-sharp.dll
b7176000-b732d000 r-xp 00000000 03:04 114906     /usr/local/lib/mono/1.0/mscorlib.dll.mdb
b732d000-b732e000 ---p b732d000 00:00 0 
b732e000-b742e000 rw-p b732e000 00:00 0 
b742e000-b743e000 rwxp b742e000 00:00 0 
b743e000-b77c3000 rw-s 00000000 03:03 3577742    /home/steven/.wapi/shared_fileshare-pirate-Linux-i686-36-10-0
b77c3000-b78f8000 rw-s 00000000 03:03 3577678    /home/steven/.wapi/shared_data-pirate-Linux-i686-308-10-0
b78f8000-b7965000 rw-p b78f8000 00:00 0 
b7965000-b796e000 r-xp 00000000 03:46 5840       /lib/tls/i686/cmov/libnss_files-2.4.so
b796e000-b7970000 rw-p 00008000 03:46 5840       /lib/tls/i686/cmov/libnss_files-2.4.so
b7970000-b7978000 r-xp 00000000 03:46 5842       /lib/tls/i686/cmov/libnss_nis-2.4.so
b7978000-b797a000 rw-p 00007000 03:46 5842       /lib/tls/i686/cmov/libnss_nis-2.4.so
b797a000-b7981000 r-xp 00000000 03:46 5838       /lib/tls/i686/cmov/libnss_compat-2.4.so
b7981000-b7983000 rw-p 00006000 03:46 5838       /lib/tls/i686/cmov/libnss_compat-2.4.so
b798c000-b7990000 r-xp 00000000 03:04 2425065    /usr/lib/beagle/UiUtil.dll
b7990000-b7991000 ---p b7990000 00:00 0 
b7991000-b7994000 rw-p b7991000 00:00 0 
b7994000-b7999000 r--p 00000000 03:04 1999333    /usr/share/locale-langpack/en_GB/LC_MESSAGES/glib20.mo
b7999000-b79b8000 r--p 00000000 03:04 2003782    /usr/share/locale-langpack/en_GB/LC_MESSAGES/libc.mo
b79b8000-b7b9b000 r-xp 00000000 03:04 114905     /usr/local/lib/mono/1.0/mscorlib.dll
b7b9b000-b7bb6000 r-xp 00000000 03:04 2426182    /usr/lib/beagle/Search.exe
b7bb6000-b7bc6000 rwxp b7bb6000 00:00 0 
b7bc6000-b7bf9000 r--p 00000000 03:04 2361197    /usr/lib/locale/en_GB.utf8/LC_CTYPE
b7bf9000-b7cd0000 r--p 00000000 03:04 2361200    /usr/lib/locale/en_GB.utf8/LC_COLLATE
b7cd0000-b7cd2000 rw-p b7cd0000 00:00 0 
b7cd2000-b7dff000 r-xp 00000000 03:46 2829       /lib/tls/i686/cmov/libc-2.4.so
b7dff000-b7e01000 r--p 0012c000 03:46 2829       /lib/tls/i686/cmov/libc-2.4.so
b7e01000-b7e03000 rw-p 0012e000 03:46 2829       /lib/tls/i686/cmov/libc-2.4.so
b7e03000-b7e06000 rw-p b7e03000 00:00 0 
b7e06000-b7e0d000 r-xp 00000000 03:46 5847       /lib/tls/i686/cmov/librt-2.4.so
b7e0d000-b7e0f000 rw-p 00006000 03:46 5847       /lib/tls/i686/cmov/librt-2.4.so
b7e0f000-b7e33000 r-xp 00000000 03:46 5835       /lib/tls/i686/cmov/libm-2.4.so
b7e33000-b7e35000 rw-p 00023000 03:46 5835       /lib/tls/i686/cmov/libm-2.4.so
b7e35000-b7e36000 rw-p b7e35000 00:00 0 
b7e36000-b7e45000 r-xp 00000000 03:46 5845       /lib/tls/i686/cmov/libpthread-2.4.so
b7e45000-b7e47000 rw-p 0000f000 03:46 5845       /lib/tls/i686/cmov/libpthread-2.4.so
b7e47000-b7e49000 rw-p b7e47000 00:00 0 
b7e49000-b7e5b000 r-xp 00000000 03:46 5837       /lib/tls/i686/cmov/libnsl-2.4.so
b7e5b000-b7e5d000 rw-p 00011000 03:46 5837       /lib/tls/i686/cmov/libnsl-2.4.so
b7e5d000-b7e5f000 rw-p b7e5d000 00:00 0 
b7e5f000-b7ef0000 r-xp 00000000 03:04 2262183    /usr/lib/libglib-2.0.so.0.1200.4
b7ef0000-b7ef1000 rw-p 00091000 03:04 2262183    /usr/lib/libglib-2.0.so.0.1200.4
b7ef1000-b7ef3000 r-xp 00000000 03:46 5834       /lib/tls/i686/cmov/libdl-2.4.so
b7ef3000-b7ef5000 rw-p 00001000 03:46 5834       /lib/tls/i686/cmov/libdl-2.4.so
b7ef5000-b7ef8000 r-xp 00000000 03:04 2262187    /usr/lib/libgmodule-2.0.so.0.1200.4
b7ef8000-b7ef9000 rw-p 00002000 03:04 2262187    /usr/lib/libgmodule-2.0.so.0.1200.4
b7ef9000-b7efd000 r-xp 00000000 03:04 2262189    /usr/lib/libgthread-2.0.so.0.1200.4
b7efd000-b7efe000 rw-p 00003000 03:04 2262189    /usr/lib/libgthread-2.0.so.0.1200.4
b7efe000-b7eff000 rw-p b7efe000 00:00 0 
b7eff000-b7f00000 r--p 00000000 03:04 2361198    /usr/lib/locale/en_GB.utf8/LC_NUMERIC
b7f00000-b7f01000 r--p 00000000 03:04 2540553    /usr/lib/locale/en_GB.utf8/LC_TIME
b7f01000-b7f02000 r--p 00000000 03:04 2540554    /usr/lib/locale/en_GB.utf8/LC_MONETARY
b7f02000-b7f03000 r--p 00000000 03:04 2361203    /usr/lib/locale/en_GB.utf8/LC_MESSAGES/SYS_LC_MESSAGES
b7f03000-b7f04000 r--p 00000000 03:04 2361204    /usr/lib/locale/en_GB.utf8/LC_PAPER
b7f04000-b7f05000 r--p 00000000 03:04 2361205    /usr/lib/locale/en_GB.utf8/LC_NAME
b7f05000-b7f06000 r--p 00000000 03:04 2540556    /usr/lib/locale/en_GB.utf8/LC_ADDRESS
b7f06000-b7f07000 r--p 00000000 03:04 2540557    /usr/lib/locale/en_GB.utf8/LC_TELEPHONE
b7f07000-b7f08000 r--p 00000000 03:04 2361208    /usr/lib/locale/en_GB.utf8/LC_MEASUREMENT
b7f08000-b7f0f000 r--s 00000000 03:04 2261908    /usr/lib/gconv/gconv-modules.cache
b7f0f000-b7f10000 r--p 00000000 03:04 2540558    /usr/lib/locale/en_GB.utf8/LC_IDENTIFICATION
b7f10000-b7f11000 rw-p b7f10000 00:00 0 
b7f11000-b7f2a000 r-xp 00000000 03:46 30856      /lib/ld-2.4.so
b7f2a000-b7f2c000 rw-p 00018000 03:46 30856      /lib/ld-2.4.so
bf9cc000-bf9e1000 rw-p bf9cc000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Stacktrace:


Native stacktrace:

        beagle-search(mono_handle_native_sigsegv+0xde) [0x814d282]
        [0xffffe440]
        /lib/tls/i686/cmov/libc.so.6(abort+0x103) [0xb7cfcef3]
        /lib/tls/i686/cmov/libc.so.6 [0xb7d30d0b]
        /lib/tls/i686/cmov/libc.so.6 [0xb7d388bd]
        /lib/tls/i686/cmov/libc.so.6(__libc_free+0x84) [0xb7d38a44]
        /usr/lib/libglib-2.0.so.0(g_free+0x31) [0xb7e91b51]
        beagle-search(mono_metadata_parse_mh_full+0x3d8) [0x80ddbcb]
        beagle-search(mono_method_get_header+0x12f) [0x80e4af8]
        beagle-search [0x8137533]
        beagle-search [0x81390e8]
        beagle-search [0x813957c]
        beagle-search(mono_runtime_exec_main+0x5c) [0x80942b3]
        beagle-search(mono_runtime_run_main+0x175) [0x80974de]
        beagle-search(mono_main+0x1059) [0x805d35b]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7ce78cc]
        beagle-search [0x805bdc1]
Aborted



I have gnome-sharp installed i have removed and re-installed it, it does not seem to make a difference to the error

Any ideas ?

---

