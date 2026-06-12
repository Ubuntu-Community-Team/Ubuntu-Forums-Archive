---
title: "My Xubuntu starts with error message"
date: 2007-03-21
forum: Installation &amp; Upgrades
---

### Post by HeroVina on 2007-03-21
Hello all,
I am a newbie of Ubuntu Linux. After install Xubuntu from Ubuntu, I restart the session and use xfce. The problem occurs when Xubuntu starts:

--------------------
Memory status: size: 60223488 vsize: 0 resident: 60223488 share: 0 rss: 9805824 rss_rlim: 0
CPU usage: start_time: 1174532052 rtime: 0 utime: 10 stime: 0 cutime:8 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/evolution-alarm-notify'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233189200 (LWP 8164)]
[New Thread -1234453600 (LWP 8173)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb727b6cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7d9e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xffffe410 in __kernel_vsyscall ()
#5  0xb7216770 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0xb7217ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0xb73e8122 in g_logv () from /usr/lib/libglib-2.0.so.0
#8  0xb73e8159 in g_log () from /usr/lib/libglib-2.0.so.0
#9  0x0805d500 in main ()

Thread 2 (Thread -1234453600 (LWP 8173)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb72b0803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb73e2813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb73e2b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb797c7e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb73fd38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7024504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb72ba51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1233189200 (LWP 8164)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb727b6cb in waitpid () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7d9e1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7216770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7217ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb73e8122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb73e8159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0x0805d500 in main ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
--------------------

Anybody know about this and how to fix ?
BTW, I am using the Edgy version.

---

### Post by twikletoes on 2007-03-23
This isn't exactly a problem it happened to me also.
All that i did was (in xfce) right click,  then click settings then choose autostarted applications and uncheck the evolution alarm notifier.
 
this worked just fine for me.

---

