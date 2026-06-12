---
title: "Downgrading Anjuta"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by muxecoid on 2006-11-06
Hi. I've just upgraded to Edgy and the new version of Anjuta does not work. How do I downgrade to the earlier version without downgrading the entire system to Dapper?

Here is the bugreport that appears on crash, where can I send it to?

```

Memory status: size: 135757824 vsize: 0 resident: 135757824 share: 0 rss: 30031872 rss_rlim: 0
CPU usage: start_time: 1162815627 rtime: 0 utime: 295 stime: 0 cutime:239 cstime: 0 timeout: 56 it_real_value: 0 frequency: 180

Backtrace was generated from '/usr/bin/anjuta'

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
[Thread debugging using libthread_db enabled]
[New Thread -1225484624 (LWP 8820)]
[New Thread -1276884064 (LWP 9840)]
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
#1  0xb745b34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f621b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb74c9c3d in g_slice_get_config () from /usr/lib/libglib-2.0.so.0
#5  0xb74c9d55 in g_slice_get_config () from /usr/lib/libglib-2.0.so.0
#6  0xb74cb0c7 in g_slice_free1 () from /usr/lib/libglib-2.0.so.0
#7  0xb754221e in g_signal_handlers_destroy ()
   from /usr/lib/libgobject-2.0.so.0
#8  0xb7a7cffd in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7b70433 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb79c7d72 in _gtk_container_dequeue_resize_handler ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b87101 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb7539b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#13 0xb752afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#14 0xb752c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#15 0xb753d34f in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#16 0xb753e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#17 0xb753e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#18 0xb7a7d0f1 in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb7b77d41 in gtk_widget_hide () from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7b84006 in _gtk_window_unset_focus_and_default ()
   from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb752ee30 in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#22 0xb7a7cdfe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#23 0xb7b77f25 in gtk_widget_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#24 0xb4a49fc4 in fv_init () from /usr/lib/anjuta/libanjuta-file-manager.so
#25 0xb7a5cb00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb752c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0xb753cb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#28 0xb753de7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0xb753e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0xb7b705f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb7a55ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb7a570f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb77c77ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#34 0xb74b3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#35 0xb74b67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#36 0xb74b6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#37 0xb7a57574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#38 0x080527ef in ?? ()
#39 0x080ac018 in ?? ()
#40 0x0808c420 in ?? ()
#41 0x00000000 in ?? ()

Thread 2 (Thread -1276884064 (LWP 9840)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb745a3fb in __read_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb74b445d in g_main_context_wakeup () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#3  0xb74d138f in g_thread_create_full () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb7454504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#5  0xb73e851e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1225484624 (LWP 8820)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb745b34b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f621b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb74c9c3d in g_slice_get_config () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb74c9d55 in g_slice_get_config () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb74cb0c7 in g_slice_free1 () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb754221e in g_signal_handlers_destroy ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7a7cffd in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7b70433 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb79c7d72 in _gtk_container_dequeue_resize_handler ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b87101 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb7539b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb752afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb752c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb753d34f in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb753e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb753e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb7a7d0f1 in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#19 0xb7b77d41 in gtk_widget_hide () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0xb7b84006 in _gtk_window_unset_focus_and_default ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb752ee30 in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb7a7cdfe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#23 0xb7b77f25 in gtk_widget_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#24 0xb4a49fc4 in fv_init () from /usr/lib/anjuta/libanjuta-file-manager.so
No symbol table info available.
#25 0xb7a5cb00 in _gtk_marshal_BOOLEAN__BOXED ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#26 0xb752c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb753cb93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb753de7f in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb753e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb7b705f8 in gtk_widget_get_default_style ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0xb7a55ef3 in gtk_propagate_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0xb7a570f7 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0xb77c77ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#34 0xb74b3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#35 0xb74b67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#36 0xb74b6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#37 0xb7a57574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0x080527ef in ?? ()
No symbol table info available.
#39 0x080ac018 in ?? ()
No symbol table info available.
#40 0x0808c420 in ?? ()
No symbol table info available.
#41 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

---

### Post by muxecoid on 2006-11-06
Another question is "F., who is the F. deciding to put ubstable alpha Anjuta v2.0.2 to the distribution which must be stable?"

Thanks, the solution is at [http://ubuntuforums.org/showthread.php?t=288480&highlight=Anjuta](http://ubuntuforums.org/showthread.php?t=288480&highlight=Anjuta) . Please remove this thread.

---

### Post by daniloeu on 2006-11-06
Hi guys!

I think that everbody know, its not easy to install anjuta1.2.4 on Edgy.
So I resolve it. I edit some Dapper packages, and create a new package named anjuta1.2.4,  and with 3 easy steps you can install anjuta 1.2.4 on Ubuntu Edgy.

```

echo "deb http://www.danilocesar.com/ubuntu debs/" >> /etc/apt/sources.list
apt-get update
apt-get install anjuta1.2.4
```

If you have any problems, please tell me:
danilo.eu [on] gmail [dot] com

---

### Post by grinias on 2006-11-07
Very nice daniloeu . Thank you :)

---

### Post by muxecoid on 2006-11-09
Did not work. When I try to create a new project it fails to configure.

---

### Post by daniloeu on 2006-11-13
Yes...

"Create project" function is not working..
I dont know why... I dont use that function.. I always create my Makefile's myself..
I receiving some emails about this error, so I trying to fix it...

If somebody knows a way to fix it, please mail me =)

Danilo Cesar
[http://www.danilocesar.com](http://www.danilocesar.com)

---

### Post by daniloeu on 2006-11-15
Mux, install package automake1.9
I think that this package solve this problem!


=)

---

### Post by UpsideDownFace on 2006-11-21
> **muxecoid said:**
> Did not work. When I try to create a new project it fails to configure.

I have failed to get anjuta-1.2.4a to compile under ubuntu breezy and dapper, this is because the universe repository needs to be enabled, I can't do this because my internet connection is not linux.

It may help if you do some or all of :-
    sudo aptitude install ubuntu-minimal
    sudo aptitude install ubuntu-base
    sudo aptitude install ubuntu-desktop
    sudo aptitude install build-essential
    sudo aptitude update
    sudo aptitude upgrade
    sudo aptitude dist-upgrade

I am using anjuta-1.2.4a under suse 10.1, which I loaded from a DVD that came with my Linux magazine.

I couldn't use the breakpoints in anjuta. The cure for this was in anjuta to goto settings->commands->language->C++
and also in settings->commands->compiler and linker check the "debug" box has a mark in it.

I hope this may save somebody some of the frustration I have had.
( its no good telling me to RTFM, because my browser won't display it correctly! and the "help"  in anjuta is not working on my computer)

---

