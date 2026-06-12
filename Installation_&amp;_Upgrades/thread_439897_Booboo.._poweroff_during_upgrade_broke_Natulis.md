---
title: "Booboo.. poweroff during upgrade broke Natulis"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by 2dere on 2007-05-11
Hmm, how to explain. Was upgrading 6.06 to 6.10 (I was planning I getting to Fiesty.) using the ```
gksu "update-manager -c"
``` As recommended and halfway during the upgrade my Dad accidently pulled out the multi-box the computer was plugged into when fiddling with the tv. I wasn't in the room when it happened but it mentioned something about not being able to get a huge list of programs. And in an attempt to upgrade again gets the same results. Since then Natulis hasn't been working and I can't use "Places" from the errr 'Taskbar' (I'm a recent convert :P) firefox still works and I can still use the list of software from applications. Plus the Desktop picture is gone and same with all the icons that was there  too. Plus I can't shake off an error message telling me Natulis is broken. Any ideas how to fix it? I posted in this forum because I was trying to upgrade but redirected me if it'll be easier. 

Whew, 2dere.

Oh managed to get something outta Bug buddy. 
```
Backtrace was generated from '/usr/bin/nautilus'

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
[Thread debugging using libthread_db enabled]
[New Thread -1226044768 (LWP 4913)]
[New Thread -1227805792 (LWP 4914)]
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
#1  0xb76f434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e078e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7c81365 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7c81b04 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7c81be7 in gtk_ui_manager_ensure_update ()
   from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb767faa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
#11 0xb7681802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#12 0xb76847df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#13 0xb7684b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#14 0xb7ba3765 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
#16 0xb741f8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#17 0x080672e1 in ?? ()

Thread 2 (Thread -1227805792 (LWP 4914)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74cd803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb7684813 in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb7684b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb77737e0 in link_set_io_thread () from /usr/lib/libORBit-2.so.0
No symbol table info available.
#5  0xb769f38f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb76ed504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#7  0xb74d751e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1226044768 (LWP 4913)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb76f434b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e078e6 in libgnomeui_module_info_get ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7c81365 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7c80ab0 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7c81b04 in _gtk_menu_is_empty () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7c81be7 in gtk_ui_manager_ensure_update ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb767faa1 in g_source_is_destroyed () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb7681802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb76847df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#13 0xb7684b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#14 0xb7ba3765 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0x08079e66 in POA_Nautilus_MetafileFactory__fini ()
No symbol table info available.
#16 0xb741f8cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#17 0x080672e1 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by bapoumba on 2007-05-11
Hello,
try:
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by 2dere on 2007-05-11
> **bapoumba said:**
> 
```
sudo aptitude update
sudo aptitude dist-upgrade
```


Cheers thats what was needed. Thanks.

---

### Post by bapoumba on 2007-05-12
You're welcome. Glad to see you got it to work :)

---

