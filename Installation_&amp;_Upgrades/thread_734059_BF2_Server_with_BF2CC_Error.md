---
title: "BF2 Server with BF2CC Error?"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by MK_Q on 2008-03-24
I'm very new to Linux and have been running Ubuntu for a few weeks and am trying to run a BF2 server with BF2CC.  I was following the doc and everything seem to work then at the end when I went to start it with mono bf2ccd.exe I got this:

** (bf2ccd.exe:17287): WARNING **: The following assembly referenced from /home/bf2srv/bf2/bf2ccd.exe could not be loaded:
     Assembly:   System.Data    (assemblyref_index=1)
     Version:    1.0.5000.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bf2srv/bf2/).


** (bf2ccd.exe:17287): WARNING **: Could not load file or assembly 'System.Data, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
Stacktrace:


Native stacktrace:

        mono [0x8194ca6]
        mono [0x81770ed]
        [0xffffe440]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x811a390]
        mono(mono_class_vtable+0x181) [0x80b29b3]
        mono(mono_object_new+0x18) [0x80b596a]
        mono(mono_exception_from_name_two_strings+0x44) [0x80f0a45]
        mono(mono_get_exception_file_not_found2+0x4f) [0x80f0b9c]
        mono [0x810f9a7]
        mono [0x8176370]
        mono [0x817699e]
        mono [0x8176a98]
        mono [0x8176f2d]
        mono(mono_runtime_invoke+0x27) [0x80b0b2f]
        mono(mono_runtime_exec_main+0x142) [0x80b5383]
        mono(mono_runtime_run_main+0x27e) [0x80b5631]
        mono(mono_jit_exec+0xbd) [0x805a4cb]
        mono [0x805a5a8]
        mono(mono_main+0x1683) [0x805bdc9]
        mono [0x8059636]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d19050]
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
[New Thread -1211099440 (LWP 17287)]
[New Thread -1220551792 (LWP 17289)]
[New Thread -1214796912 (LWP 17288)]
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
  3 Thread -1214796912 (LWP 17288)  0xffffe410 in __kernel_vsyscall ()
  2 Thread -1220551792 (LWP 17289)  0xffffe410 in __kernel_vsyscall ()
  1 Thread -1211099440 (LWP 17287)  0xffffe410 in __kernel_vsyscall ()

Thread 3 (Thread -1214796912 (LWP 17288)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7e9f6 in ?? () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0811bc9f in ?? ()
#3  0xb797a3ac in ?? ()
#4  0x00000000 in ?? ()

Thread 2 (Thread -1220551792 (LWP 17289)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7e7b676 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08120dde in ?? ()
#3  0xb78e71dc in ?? ()
#4  0xb78e71c4 in ?? ()
#5  0xb7e79541 in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#6  0x081210eb in ?? ()
#7  0xb78e71dc in ?? ()
#8  0xb78e71c4 in ?? ()
#9  0x00000000 in ?? ()

Thread 1 (Thread -1211099440 (LWP 17287)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7dcf2a1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eee780 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7eeeb4c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x08194d84 in ?? ()
#5  0xb7bbc844 in ?? ()
#6  0xb7bbc82c in ?? ()
#7  0xb7bbc828 in ?? ()
#8  0xb7bbc824 in ?? ()
#9  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)

The only thing that was different from the docs I was reading was the mono version.  It said to use 1.1.12.1 but when I do mono -V I have a different version.  I was able to download the 1.1.12.1 bin file but cant get it to install.  I dont even know if thats the problem.  Please help if you can.  Again I'm a total noob with Linux.

MK_Q

---

### Post by MK_Q on 2008-03-31
I got BF2 Server to run without BF2CC and just updated the settngs serversettings.con file to run it.  Worked for what I wanted to use it for.  I may try BF2CC again in a while and will post if I get it working.  

2 notes:

**1** - I kept getting an error and I think this was the fix I used.  I didnt write it down but I'm pretty sure:

[COLOR="Red"] If you get error messages about libstdc++.so.5, similar to this one: "error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory", install libstdc++-v3 using this command:

emerge -av libstdc++-v3 
[/COLOR]
[http://gentoo-wiki.com/HOWTO_Setup_A_Battlefield_2_Dedicated_Server](http://gentoo-wiki.com/HOWTO_Setup_A_Battlefield_2_Dedicated_Server)


**2** -[COLOR="Red"] I had a problem where the server showed Status: [no game] when I put anything other than my LAN IP in the server IP (I kept thinking it needed to be my WAN IP).  Use your LAN IP.[/COLOR]

---

