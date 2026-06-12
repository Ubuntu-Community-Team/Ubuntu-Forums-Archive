---
title: "SIGABRT when trying to run gnome-do"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2008-02-13
I'm trying to install gnome-do from this repo:

deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main

But attempting to run it results in a sigabrt on eeeXubuntu 7.10. the output is as follows...

```
Selecting previously deselected package mono-common.
(Reading database ... 81538 files and directories currently installed.)
Unpacking mono-common (from .../mono-common_1.2.4-6ubuntu6.1_i386.deb) ...
Selecting previously deselected package mono-jit.
Unpacking mono-jit (from .../mono-jit_1.2.4-6ubuntu6.1_i386.deb) ...
Selecting previously deselected package libmono-corlib2.0-cil.
Unpacking libmono-corlib2.0-cil (from .../libmono-corlib2.0-cil_1.2.4-6ubuntu6.1_all.deb) ...
Selecting previously deselected package libmono-cairo2.0-cil.
Unpacking libmono-cairo2.0-cil (from .../libmono-cairo2.0-cil_1.2.4-6ubuntu6.1_all.deb) ...
Selecting previously deselected package xclip.
Unpacking xclip (from .../archives/xclip_0.08-7_i386.deb) ...
Selecting previously deselected package gnome-do.
Unpacking gnome-do (from .../gnome-do_0.3~bzr173-gutsy1_i386.deb) ...
Setting up mono-common (1.2.4-6ubuntu6.1) ...

Setting up mono-jit (1.2.4-6ubuntu6.1) ...

Setting up libmono-corlib2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up libmono-cairo2.0-cil (1.2.4-6ubuntu6.1) ...
Setting up xclip (0.08-7) ...
Setting up gnome-do (0.3~bzr173-gutsy1) ...
khaal@khalleeee:~$ gnome-do -q
/usr/bin/gnome-do: 6: pkg-config: not found

** (/usr/lib/do/Do.exe:6626): WARNING **: The following assembly referenced from /usr/lib/do/Do.exe could not be loaded:
     Assembly:   Mono.GetOptions    (assemblyref_index=7)
     Version:    2.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/do).


** (/usr/lib/do/Do.exe:6626): WARNING **: Could not load file or assembly 'Mono.GetOptions, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.

** (/usr/lib/do/Do.exe:6626): WARNING **: Missing method .ctor in assembly /usr/lib/do/Do.exe, type Mono.AuthorAttribute

** ERROR **: Can't find custom attr constructor image: /usr/lib/do/Do.exe mtoken: 0x0a00019b
aborting...
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x8177154]
        [0xffffe440]
        /lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7cf2201]
        /usr/lib/libglib-2.0.so.0(g_logv+0x4ca) [0xb7e88f4a]
        /usr/lib/libglib-2.0.so.0(g_log+0x29) [0xb7e88f89]
        mono(mono_custom_attrs_from_index+0x18a) [0x81a1722]
        mono(mono_custom_attrs_from_assembly+0x31) [0x81a1a3a]
        mono(mono_assembly_load_from_full+0x544) [0x80ff7b8]
        mono(mono_assembly_open_full+0x272) [0x80ffb7d]
        mono(mono_assembly_open+0x20) [0x80ffc27]
        mono(mono_main+0x1565) [0x805bcab]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cdc050]
        mono [0x80595b1]

Debug info from gdb:

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1211349296 (LWP 6626)]
[New Thread -1221014640 (LWP 6631)]
[New Thread -1215267952 (LWP 6630)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
  3 Thread -1215267952 (LWP 6630)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1221014640 (LWP 6631)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211349296 (LWP 6626)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1215267952 (LWP 6630)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e419f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb79073ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1221014640 (LWP 6631)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e3e676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb78761dc in ?? ()
#4  0xb78761c4 in ?? ()
#5  0xb7e3c541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb78761dc in ?? ()
#8  0xb78761c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1211349296 (LWP 6626)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7d922a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb1780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb1b4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xbff89e74 in ?? ()
#6  0xbff89e5c in ?? ()
#7  0xbff89e58 in ?? ()
#8  0xbff89e54 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

```

---

