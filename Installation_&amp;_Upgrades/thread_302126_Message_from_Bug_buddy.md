---
title: "Message from Bug buddy"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by msn on 2006-11-18
Memory status: size: 31948800 vsize: 0 resident: 31948800 share: 0 rss: 4501504 rss_rlim: 0
CPU usage: start_time: 1163844535 rtime: 0 utime: 7 stime: 0 cutime:5 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/gnome-power-manager'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
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
[New Thread -1225058640 (LWP 9728)]
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
0xb79fcbfe in __waitpid_nocancel () from /lib/libpthread.so.0
#0  0xb79fcbfe in __waitpid_nocancel () from /lib/libpthread.so.0
#1  0xb7f751b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#2  <signal handler called>
#3  0xb7104986 in raise () from /lib/libc.so.6
#4  0xb7106043 in abort () from /lib/libc.so.6
#5  0xb7238122 in g_logv () from /usr/lib/libglib-2.0.so.0
#6  0xb7238159 in g_log () from /usr/lib/libglib-2.0.so.0
#7  0xb72381d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
#8  0xb768bb0c in dbus_g_proxy_call_no_reply ()
   from /usr/lib/libdbus-glib-1.so.2
#9  0xb768c909 in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
#10 0xb768d4da in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
#11 0xb768dbee in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
#12 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#13 0xb72de7e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#14 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#15 0xb768c268 in dbus_g_proxy_get_bus_name ()
   from /usr/lib/libdbus-glib-1.so.2
#16 0x0805e7f6 in ?? ()
#17 0x0805b0f4 in ?? ()
#18 0xb72f889a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#19 0xb72df952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#20 0x0805af68 in ?? ()
#21 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#22 0xb72de73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#23 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#24 0x0805ae2c in ?? ()
#25 0x08054598 in ?? ()
#26 0xb72f889a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#27 0xb72df952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#28 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#29 0xb72de73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#30 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#31 0x080534ec in ?? ()
#32 0x08051bee in ?? ()
#33 0xb70f18cc in __libc_start_main () from /lib/libc.so.6
#34 0x0804dbe1 in ?? ()

Thread 1 (Thread -1225058640 (LWP 9728)):
#0  0xb79fcbfe in __waitpid_nocancel () from /lib/libpthread.so.0
No symbol table info available.
#1  0xb7f751b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0xb7104986 in raise () from /lib/libc.so.6
No symbol table info available.
#4  0xb7106043 in abort () from /lib/libc.so.6
No symbol table info available.
#5  0xb7238122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7238159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb72381d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb768bb0c in dbus_g_proxy_call_no_reply ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#9  0xb768c909 in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#10 0xb768d4da in dbus_g_proxy_new_for_name ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#11 0xb768dbee in dbus_g_proxy_set_interface ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#12 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb72de7e9 in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb768c268 in dbus_g_proxy_get_bus_name ()
   from /usr/lib/libdbus-glib-1.so.2
No symbol table info available.
#16 0x0805e7f6 in ?? ()
No symbol table info available.
#17 0x0805b0f4 in ?? ()
No symbol table info available.
#18 0xb72f889a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb72df952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0x0805af68 in ?? ()
No symbol table info available.
#21 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb72de73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0x0805ae2c in ?? ()
No symbol table info available.
#25 0x08054598 in ?? ()
No symbol table info available.
#26 0xb72f889a in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb72df952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb72ddbdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb72de73f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb72de8f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#31 0x080534ec in ?? ()
No symbol table info available.
#32 0x08051bee in ?? ()
No symbol table info available.
#33 0xb70f18cc in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#34 0x0804dbe1 in ?? ()
No symbol table info available.
#0  0xb79fcbfe in __waitpid_nocancel () from /lib/libpthread.so.0

The above is the message.... Please help me to install Ubuntu 6.10 on my PC.

I appreciate your help much in this and i will be greatful if someone helps me to install this on my PC.:(

---

### Post by msn on 2006-11-23
No one can't help on this topic??? 

I thought that i will get plenty of reply to this post.

Even people here in ubuntu forums can't help then i think that i can't install ubuntu on my Pc and enjoy... :(

---

### Post by computer_freak on 2007-03-15
i have a similar problem with bug buddy and this link helped me:
[http://www.ubuntuforums.org/showthread.php?t=311258]("http://www.ubuntuforums.org/showthread.php?t=311258"):biggrin:

hope it helps you too

---

