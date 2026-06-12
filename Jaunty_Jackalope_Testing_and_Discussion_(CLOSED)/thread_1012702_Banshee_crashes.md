---
title: "Banshee crashes"
date: 2008-12-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by FarJumper on 2008-12-16
Banshee player crashes after recent jaunty upgrading.

```
vbuell@vbuell-home:~$ banshee
[Info  11:56:56.615] Running Banshee 1.4.1
[Info  11:56:59.302] All services are started 2.164021s

** (Banshee:9196): WARNING **: The following assembly referenced from /usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f/gdk-sharp.dll could not be loaded:
     Assembly:   Mono.Cairo    (assemblyref_index=2)
     Version:    2.0.0.0
     Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/mono/gac/gdk-sharp/2.12.0.0__35e10195dab3c99f).


** (Banshee:9196): WARNING **: Could not load file or assembly 'Mono.Cairo, Version=2.0.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.
Stacktrace:

  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x0006c>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x00007>
  at Banshee.Gui.GtkBaseClient.Run () <0x00035>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00031>
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.CleanRoomStartup/StartupInvocationHandler) <0x000a2>
  at Banshee.Gui.GtkBaseClient.Startup () <0x00038>
  at Banshee.Gui.GtkBaseClient.Startup (string[]) <0x000a6>
  at Nereid.Client.Main (string[]) <0x0000a>
  at (wrapper runtime-invoke) Nereid.Client.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0x00004>
  at (wrapper managed-to-native) System.AppDomain.ExecuteAssembly (System.Reflection.Assembly,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssemblyInternal (System.Reflection.Assembly,string[]) <0x00028>
  at System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0x00021>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string,System.Security.Policy.Evidence,string[]) <0xffffffff>
  at System.AppDomain.ExecuteAssembly (string) <0x00014>
  at (wrapper remoting-invoke-with-check) System.AppDomain.ExecuteAssembly (string) <0xffffffff>
  at Booter.Booter.BootClient (string) <0x00055>
  at Booter.Booter.Main () <0x00188>
  at (wrapper runtime-invoke) System.Object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	banshee-1 [0x806d954]
	banshee-1 [0x808618b]
	[0xb7f24410]
	banshee-1 [0x813435c]
	banshee-1 [0x81345bd]
	banshee-1 [0x81358da]
	banshee-1 [0x81360c9]
	banshee-1(mono_get_method_full+0xa1) [0x8136421]
	banshee-1 [0x81882f0]
	banshee-1 [0x81a0be8]
	banshee-1 [0x81afc55]
	banshee-1 [0x81b1b61]
	banshee-1 [0x807029f]
	[0xb7b34066]
	[0xb4e48328]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb679ebd8]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6c31093]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c310c1]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6bfb85d]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6c31c66]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c33350]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb679ebd8]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6c31093]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6d86a9b]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb679ebd8]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6c31093]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c310c1]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6bfb85d]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6c31c66]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c33350]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb679ebd8]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6c31093]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c310c1]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6bff806]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6c31c66]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c33350]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd8) [0xb679ebd8]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1b3) [0xb6c31093]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c310c1]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6bfb85d]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x96) [0xb6c31c66]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c33350]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6de9d71]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6cbafa6]
	/usr/lib/libgobject-2.0.so.0 [0xb679d409]
	/usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1ab) [0xb679ecab]
	/usr/lib/libgobject-2.0.so.0 [0xb67b633d]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x68b) [0xb67b7c5b]
	/usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0xb67b8256]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6dd020e]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x52d) [0xb6cb50ad]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb6b19a35]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_all_updates+0xff) [0xb6b1a04f]
	/usr/lib/libgtk-x11-2.0.so.0 [0xb6c31dff]
	/usr/lib/libgdk-x11-2.0.so.0 [0xb6afd4bb]
	/usr/lib/libglib-2.0.so.0 [0xb7e9bbb1]
	/usr/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1e8) [0xb7e9dae8]
	/usr/lib/libglib-2.0.so.0 [0xb7ea1193]
	/usr/lib/libglib-2.0.so.0(g_main_loop_run+0x1d2) [0xb7ea16b2]
	/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0xb6cb5319]
	[0xb23426be]
	[0xb2342688]
	[0xb2342466]
	[0xb70d9852]
	[0xb70d973b]
	[0xb70d9659]
	[0xb70d1da7]
	[0xb70cdbc3]
	[0xb70cdb53]
	banshee-1(mono_runtime_exec_main+0xe5) [0x80bad95]
	[0xb70cdafd]
	[0xb70cda21]
	[0xb70cd91a]
	[0xb70cd8c6]
	[0xb70cd83d]
	[0xb70cd7fa]
	[0xb70cc93e]
	[0xb78aa3a9]
	[0xb78aa1ae]
	banshee-1(mono_runtime_exec_main+0xe5) [0x80bad95]
	banshee-1(mono_runtime_run_main+0x16b) [0x80bb50b]
	banshee-1(mono_main+0x1737) [0x805c927]
	banshee-1 [0x805ac62]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7cae775]
	banshee-1 [0x805aba1]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c646e0 (LWP 9196)]
[New Thread 0xb2bffb90 (LWP 9208)]
[New Thread 0xb2ed3b90 (LWP 9207)]
[New Thread 0xb2fd8b90 (LWP 9206)]
[New Thread 0xb62f0b90 (LWP 9200)]
[New Thread 0xb74b5b90 (LWP 9198)]
[New Thread 0xb78a9b90 (LWP 9197)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f24430 in __kernel_vsyscall ()
  7 Thread 0xb78a9b90 (LWP 9197)  0xb7f24430 in __kernel_vsyscall ()
  6 Thread 0xb74b5b90 (LWP 9198)  0xb7f24430 in __kernel_vsyscall ()
  5 Thread 0xb62f0b90 (LWP 9200)  0xb7f24430 in __kernel_vsyscall ()
  4 Thread 0xb2fd8b90 (LWP 9206)  0xb7f24430 in __kernel_vsyscall ()
  3 Thread 0xb2ed3b90 (LWP 9207)  0xb7f24430 in __kernel_vsyscall ()
  2 Thread 0xb2bffb90 (LWP 9208)  0xb7f24430 in __kernel_vsyscall ()
  1 Thread 0xb7c646e0 (LWP 9196)  0xb7f24430 in __kernel_vsyscall ()

Thread 7 (Thread 0xb78a9b90 (LWP 9197)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2d8f6 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08149308 in ?? ()
#3  0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb74b5b90 (LWP 9198)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2a0e5 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c627 in ?? ()
#3  0x0814f214 in ?? ()
#4  0x0814f27c in ?? ()
#5  0x08169b22 in ?? ()
#6  0x080d567a in ?? ()
#7  0x080f7659 in ?? ()
#8  0x081653d6 in ?? ()
#9  0x08183375 in ?? ()
#10 0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0



#11 0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb62f0b90 (LWP 9200)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2a412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5d8 in ?? ()
#3  0x0814f214 in ?? ()
#4  0x0814f27c in ?? ()
#5  0x08169b22 in ?? ()
#6  0x080f4603 in ?? ()
#7  0xb630e342 in ?? ()
#8  0xb630e183 in ?? ()
#9  0xb630c6b8 in ?? ()
#10 0xb78ac859 in ?? ()
#11 0x080b8994 in mono_runtime_delegate_invoke ()
#12 0x080f76df in ?? ()
#13 0x081653d6 in ?? ()
#14 0x08183375 in ?? ()
#15 0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb2fd8b90 (LWP 9206)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2a412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5d8 in ?? ()
#3  0x0814c6a2 in ?? ()
#4  0x0816a075 in ?? ()
#5  0x080f6179 in ?? ()
#6  0xb2fda43f in ?? ()
#7  0xb2fda06e in ?? ()
#8  0xb2fd9e47 in ?? ()
#9  0xb2fd9bfe in ?? ()
#10 0x080bd02a in mono_runtime_invoke_array ()
#11 0x080bd234 in ?? ()
#12 0x080fa953 in ?? ()
#13 0x080fad70 in ?? ()
#14 0x080f7659 in ?? ()
#15 0x081653d6 in ?? ()
#16 0x08183375 in ?? ()
#17 0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb2ed3b90 (LWP 9207)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2a412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5d8 in ?? ()
#3  0x0814c6a2 in ?? ()
#4  0x0816a075 in ?? ()
#5  0x080f6179 in ?? ()
#6  0xb2fda43f in ?? ()
#7  0xb2fda06e in ?? ()
#8  0xb2fd9e47 in ?? ()
#9  0xb2fd9bfe in ?? ()
#10 0x080bd02a in mono_runtime_invoke_array ()
#11 0x080bd234 in ?? ()
#12 0x080fa953 in ?? ()
#13 0x080fad70 in ?? ()
#14 0x080f7659 in ?? ()
#15 0x081653d6 in ?? ()
#16 0x08183375 in ?? ()
#17 0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb2bffb90 (LWP 9208)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2a412 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0814c5d8 in ?? ()
#3  0x0814c6a2 in ?? ()
#4  0x0816a075 in ?? ()
#5  0x080f6179 in ?? ()
#6  0xb2fda43f in ?? ()
#7  0xb2fda06e in ?? ()
#8  0xb2fd9e47 in ?? ()
#9  0xb2fd9bfe in ?? ()
#10 0x080bd02a in mono_runtime_invoke_array ()
#11 0x080bd234 in ?? ()
#12 0x080fa953 in ?? ()
#13 0x080fad70 in ?? ()
#14 0x080f7659 in ?? ()
#15 0x081653d6 in ?? ()
#16 0x08183375 in ?? ()
#17 0xb7e264ff in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7d7c33e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c646e0 (LWP 9196)):
#0  0xb7f24430 in __kernel_vsyscall ()
#1  0xb7e2d0fb in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0806da6e in ?? ()
#3  0x0808618b in ?? ()
#4  <signal handler called>
#5  0x0811ae45 in mono_metadata_signature_equal ()
#6  0x0813435c in ?? ()
#7  0x081345bd in ?? ()
#8  0x081358da in ?? ()
#9  0x081360c9 in ?? ()
#10 0x08136421 in mono_get_method_full ()
#11 0x081882f0 in ?? ()
#12 0x081a0be8 in ?? ()
#13 0x081afc55 in ?? ()
#14 0x081b1b61 in ?? ()
#15 0x0807029f in ?? ()
#16 0xb7b34066 in ?? ()
#17 0xb4e48328 in ?? ()
#18 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#20 0xb679ebd8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#21 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#22 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#23 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#24 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#25 0xb6c31093 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb6c310c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#27 0xb6bfb85d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb6c31c66 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb6c33350 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#30 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#32 0xb679ebd8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#33 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#34 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#35 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#36 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb6c31093 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb6d86a9b in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#41 0xb679ebd8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#42 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#43 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#44 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#45 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb6c31093 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#47 0xb6c310c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb6bfb85d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#49 0xb6c31c66 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#50 0xb6c33350 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#51 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#52 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#53 0xb679ebd8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#54 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#55 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#56 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#57 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#58 0xb6c31093 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#59 0xb6c310c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#60 0xb6bff806 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#61 0xb6c31c66 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#62 0xb6c33350 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#63 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#64 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#65 0xb679ebd8 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#66 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#67 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#68 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#69 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#70 0xb6c31093 in gtk_container_propagate_expose () from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb6c310c1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#72 0xb6bfb85d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#73 0xb6c31c66 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#74 0xb6c33350 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#75 0xb6de9d71 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#76 0xb6cbafa6 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#77 0xb679d409 in ?? () from /usr/lib/libgobject-2.0.so.0
#78 0xb679ecab in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#79 0xb67b633d in ?? () from /usr/lib/libgobject-2.0.so.0
#80 0xb67b7c5b in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#81 0xb67b8256 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#82 0xb6dd020e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#83 0xb6cb50ad in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#84 0xb6b19a35 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#85 0xb6b1a04f in gdk_window_process_all_updates () from /usr/lib/libgdk-x11-2.0.so.0
#86 0xb6c31dff in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#87 0xb6afd4bb in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#88 0xb7e9bbb1 in ?? () from /usr/lib/libglib-2.0.so.0
#89 0xb7e9dae8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#90 0xb7ea1193 in ?? () from /usr/lib/libglib-2.0.so.0
#91 0xb7ea16b2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#92 0xb6cb5319 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#93 0xb23426be in ?? ()
#94 0xb2342688 in ?? ()
#95 0xb2342466 in ?? ()
#96 0xb70d9852 in ?? ()
#97 0xb70d973b in ?? ()
#98 0xb70d9659 in ?? ()
#99 0xb70d1da7 in ?? ()
#100 0xb70cdbc3 in ?? ()
#101 0xb70cdb53 in ?? ()
#102 0x080bad95 in mono_runtime_exec_main ()
#103 0xb70cdafd in ?? ()
#104 0xb70cda21 in ?? ()
#105 0xb70cd91a in ?? ()
#106 0xb70cd8c6 in ?? ()
#107 0xb70cd83d in ?? ()
#108 0xb70cd7fa in ?? ()
#109 0xb70cc93e in ?? ()
#110 0xb78aa3a9 in ?? ()
#111 0xb78aa1ae in ?? ()
#112 0x080bad95 in mono_runtime_exec_main ()
#113 0x080bb50b in mono_runtime_run_main ()
#114 0x0805c927 in mono_main ()
#115 0x0805ac62 in ?? ()
#116 0xb7cae775 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#117 0x0805aba1 in ?? ()
#0  0xb7f24430 in __kernel_vsyscall ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
vbuell@vbuell-home:~$ 

```

Both libmono-cairo1.0-cil and libmono-cairo2.0-cil are installed. Please pay attention of publicKeys of installed on my machine assemblies. I don't know all about mono, but it looks that it tries to load assembly 'Mono.Cairo' with PublicKeyToken=35e10195dab3c99f.

```
vbuell@vbuell-home:/usr/lib/mono/gac/Mono.Cairo$ ls -l
total 8
drwxr-xr-x 2 root root 4096 2008-12-14 17:20 1.0.5000.0__0738eb9f132ed756
drwxr-xr-x 2 root root 4096 2008-12-14 15:02 2.0.0.0__0738eb9f132ed756
vbuell@vbuell-home:/usr/lib/mono/gac/Mono.Cairo$ 

```

Ubuntu: Intrepid
Banshee: 1.4.1-1ubuntu1
libmono-cairo1.0-cil: 2.0.1-0ubuntu2
libmono-cairo2.0-cil: 2.0.1-0ubuntu2

---

### Post by FarJumper on 2008-12-16
Filled bug: [https://bugs.launchpad.net/bugs/308520](https://bugs.launchpad.net/bugs/308520)

---

### Post by ronacc on 2008-12-16
getting the same here on 64bit jaunty .

---

### Post by directhex on 2008-12-16
Looks like a bad GTK# upload. Will probably be affecting all GTK# apps (e.g. Tomboy, F-Spot)

35e10195dab3c99f is the pubkey for gtk-sharp:
```
jms@osc-franzibald:/tmp$ sn -T /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll | tail -1
Public Key Token: 35e10195dab3c99f
```

It seems for whatever reason the Mono.Cairo reference has been encoded incorrectly, as Mono.Cairo should definitely use the Mono signing key:
```
jms@osc-franzibald:/tmp$ sn -T /usr/lib/mono/gac/Mono.Cairo/2.0.0.0__0738eb9f132ed756/Mono.Cairo.dll | tail -1
Public Key Token: 0738eb9f132ed756

jms@osc-franzibald:/tmp$ monodis --assemblyref /usr/lib/mono/gac/gtk-sharp/2.12.0.0__35e10195dab3c99f/gtk-sharp.dll| grep -A3 Mono.Cairo
	Name=Mono.Cairo
	Flags=0x00000000
	Public Key:
0x00000000: 07 38 EB 9F 13 2E D7 56 
```

I'll investigate

---

### Post by directhex on 2008-12-16
Patched, sending fix to Launchpad.

---

### Post by directhex on 2008-12-16
lp:308619

---

### Post by directhex on 2008-12-16
2.12.7-1ubuntu2


    * Published 42 minutes ago

---

### Post by tawmas on 2008-12-16
> **directhex said:**
> 2.12.7-1ubuntu2

This package fixes the crasher for me, but now I'm seeing a (probably unrelated) issue. If I ask Banshee to rescan the music library, it suddenly starts using Way Too Much CPU And Some More (sorry, I myself can't believe the % reported in the attached top screenshot, but the fans in my desktop have a different opinion). Stopping the rescan doesn't bring CPU usage down, only quitting will do.

I could replicate this three times in a row, and, btw, I let the first rescan complete, so it doesn't have much to do. I won't attempt the fourth rescan in a row...

I did a rescan a couple of days ago, and didn't notice anything strange, so this might be related to this or other mono updates.

---

