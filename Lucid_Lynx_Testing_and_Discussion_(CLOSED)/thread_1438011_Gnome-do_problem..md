---
title: "Gnome-do problem."
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2010-03-24
I am not able to summon Gnome-do properly. Some time it shows up other time it didn't. When i ran gnome-do in terminal i get following result.

> 
[Error 13:00:40.016] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.062] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.070] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.078] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.091] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.104] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.112] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.121] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:40.203] gnome-keyring-daemon could not be reached!
[Error 13:00:40.205] gnome-keyring-daemon could not be reached!
[Error 13:00:40.207] gnome-keyring-daemon could not be reached!
[Error 13:00:40.306] gnome-keyring-daemon could not be reached!
[Error 13:00:40.307] gnome-keyring-daemon could not be reached!
[Error 13:00:40.308] gnome-keyring-daemon could not be reached!
[Error 13:00:41.025] An error has occurred in UpdateCalendars
[Error 13:00:41.142] GMailContacts Error: Error authenticating (check service name): Unknown
[Error 13:00:59.321] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.367] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.375] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.384] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.397] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.410] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.418] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.427] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 13:00:59.512] gnome-keyring-daemon could not be reached!
[Error 13:00:59.514] gnome-keyring-daemon could not be reached!
[Error 13:00:59.516] gnome-keyring-daemon could not be reached!
[Error 13:00:59.617] gnome-keyring-daemon could not be reached!
[Error 13:00:59.618] gnome-keyring-daemon could not be reached!
[Error 13:00:59.619] gnome-keyring-daemon could not be reached!
[Error 13:01:00.361] An error has occurred in UpdateCalendars


Thanks.

---

### Post by donniezazen on 2010-04-06
Do still not working. Please help.

> 

(Do:9973): Wnck-CRITICAL **: wnck_set_client_type got called multiple times.

Could not locate Tomboy on D-Bus. Perhaps it's not running?
[Error 19:21:22.658] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.701] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.709] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.718] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.733] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.744] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.753] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
[Error 19:21:22.762] Could not load desktop item: File 'file:///usr/share/applications/openoffice.org3-startcenter.desktop' is not a regular file or directory.
**
ERROR:gkr-operation.c:169:gkr_operation_set_result: assertion failed: ((int) res != INCOMPLETE)
Stacktrace:

  at (wrapper managed-to-native) Gnome.Keyring.Ring.gnome_keyring_find_items_sync (Gnome.Keyring.ItemType,intptr,intptr&) <0x00004>
  at (wrapper managed-to-native) Gnome.Keyring.Ring.gnome_keyring_find_items_sync (Gnome.Keyring.ItemType,intptr,intptr&) <0xffffffff>
  at Gnome.Keyring.Ring.Find (Gnome.Keyring.ItemType,System.Collections.Hashtable) <0x00073>
  at Do.Platform.Linux.GnomeKeyringSecurePreferencesService.TryGet (string,string&) <0x000ae>
  at Do.Platform.SecurePreferencesServiceWrapper.TryGet<object> (string,object&) <0x00054>
  at (wrapper static-rgctx-invoke) Do.Platform.SecurePreferencesServiceWrapper.static_rgctx_invoke_bool__this___string_string& (string,string&) <0xffffffff>
  at Do.Platform.Preferences.PreferencesImplementation`1<object>.TryGet<object> (Do.Platform.IPreferencesService,string,object&) <0x00060>
  at Do.Platform.Preferences.PreferencesImplementation`1<object>.TryGet<object> (Do.Platform.IPreferencesService,string,object,object&) <0x0002b>
  at Do.Platform.Preferences.PreferencesImplementation`1<object>.GetSecure<object> (string,object) <0x00050>
  at (wrapper static-rgctx-invoke) Do.Platform.Preferences.PreferencesImplementation`1<GMail.GMailPreferences>.static_rgctx_invoke_string__this___string_string (string,string) <0xffffffff>
  at GMail.GMailPreferences.get_Password () <0x00033>
  at GMail.GMail..cctor () <0x0009b>
  at (wrapper runtime-invoke) object.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at GMail.GMailItemSource.get_Items () <0xffffffff>
  at GMail.GMailItemSource.get_Items () <0x0000b>
  at Do.Universe.Safe.SafeItemSource.get_Items () <0x00032>
  at Do.Core.UniverseManager.ReloadSource (Do.Universe.ItemSource,System.Collections.Generic.Dictionary`2<string, Do.Universe.Item>) <0x00058>
  at Do.Core.UniverseManager/<ReloadUniverse>c__AnonStoreyD.<>m__22 (Do.Universe.ItemSource) <0x0001b>
  at System.Linq.EnumerableExtensions.ForEach<object> (System.Collections.Generic.IEnumerable`1<object>,System.Action`1<object>) <0x000cc>
  at Do.Core.UniverseManager.ReloadUniverse () <0x000cd>
  at Do.Core.UniverseManager.InitializeAsync () <0x00010>
  at Do.Platform.ApplicationService/<RunOnThread>c__AnonStoreyF.<>m__28 () <0x0001c>
  at (wrapper runtime-invoke) object.runtime_invoke_void__this__ (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/cli() [0x80ca6e4]
	[0x6f1410]
	/lib/tls/i686/cmov/libc.so.6(abort+0x182) [0xe22a72]
	/lib/libglib-2.0.so.0(g_assertion_message+0x163) [0xb2ddd3]
	/lib/libglib-2.0.so.0(+0x6342d) [0xb2e42d]
	/usr/lib/libgnome-keyring.so.0(+0x7802) [0x6b92802]
	/usr/lib/libgnome-keyring.so.0(+0x6b55) [0x6b91b55]
	/usr/lib/libgnome-keyring.so.0(+0x78fc) [0x6b928fc]
	/usr/lib/libgnome-keyring.so.0(+0x85b1) [0x6b935b1]
	/usr/lib/libgnome-keyring.so.0(gnome_keyring_find_items_sync+0x45) [0x6b9c985]
	[0x27bf56b]
	[0x27becec]
	[0x27be657]
	[0x27be4cd]
	[0x27be464]
	[0x577d3c1]
	[0x577d304]
	[0x27be411]
	[0x2d11b24]
	[0x2d11ab4]
	[0x2d1139c]
	[0xdcc8f3]
	/usr/bin/cli() [0x8116fca]
	/usr/bin/cli(mono_runtime_class_init+0x19) [0x8117669]
	/usr/bin/cli() [0x8063061]
	/usr/bin/cli() [0x80d42bb]
	[0xcb5066]
	[0x6eba383]
	[0x6eb9f41]
	[0x6eb9ed4]
	[0x6eb9d2d]
	[0x6eb74b6]
	[0x6eb7369]
	[0x6eb728d]
	[0x682711]
	/usr/bin/cli(mono_runtime_delegate_invoke+0x34) [0x8110ef4]
	/usr/bin/cli() [0x815285b]
	/usr/bin/cli() [0x81c3062]
	/usr/bin/cli() [0x81e1925]
	/lib/tls/i686/cmov/libpthread.so.0(+0x596e) [0x17796e]
	/lib/tls/i686/cmov/libc.so.6(clone+0x5e) [0xec29de]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x2fafb70 (LWP 9979)]
[New Thread 0x5b08b70 (LWP 9978)]
[New Thread 0x2a25b70 (LWP 9976)]
[New Thread 0x8d6b70 (LWP 9975)]
[New Thread 0x1a5b70 (LWP 9974)]
0x006f1422 in __kernel_vsyscall ()
  6 Thread 0x1a5b70 (LWP 9974)  0x006f1422 in __kernel_vsyscall ()
  5 Thread 0x8d6b70 (LWP 9975)  0x006f1422 in __kernel_vsyscall ()
  4 Thread 0x2a25b70 (LWP 9976)  0x006f1422 in __kernel_vsyscall ()
  3 Thread 0x5b08b70 (LWP 9978)  0x006f1422 in __kernel_vsyscall ()
  2 Thread 0x2fafb70 (LWP 9979)  0x00e68188 in ?? ()
   from /lib/tls/i686/cmov/libc.so.6
* 1 Thread 0x1416f0 (LWP 9973)  0x006f1422 in __kernel_vsyscall ()

Thread 6 (Thread 0x1a5b70 (LWP 9974)):
#0  0x006f1422 in __kernel_vsyscall ()
#1  0x0017f736 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a6af8 in ?? ()
#3  0x0017796e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x00ec29de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0x8d6b70 (LWP 9975)):
#0  0x006f1422 in __kernel_vsyscall ()
#1  0x0017e245 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812e199 in ?? ()
#3  0x081527ea in ?? ()
#4  0x081c3062 in ?? ()
#5  0x081e1925 in ?? ()
#6  0x0017796e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x00ec29de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x2a25b70 (LWP 9976)):
#0  0x006f1422 in __kernel_vsyscall ()
#1  0x0017ef5b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080ca87e in ?? ()
#3  <signal handler called>
#4  0x006f1422 in __kernel_vsyscall ()
#5  0x00e1f641 in raise () from /lib/tls/i686/cmov/libc.so.6
#6  0x00e22a72 in abort () from /lib/tls/i686/cmov/libc.so.6
#7  0x00b2ddd3 in g_assertion_message () from /lib/libglib-2.0.so.0
#8  0x00b2e42d in g_assertion_message_expr () from /lib/libglib-2.0.so.0
#9  0x06b92802 in ?? () from /usr/lib/libgnome-keyring.so.0
#10 0x06b91b55 in ?? () from /usr/lib/libgnome-keyring.so.0
#11 0x06b928fc in ?? () from /usr/lib/libgnome-keyring.so.0
#12 0x06b935b1 in ?? () from /usr/lib/libgnome-keyring.so.0
#13 0x06b9c985 in gnome_keyring_find_items_sync ()
   from /usr/lib/libgnome-keyring.so.0
#14 0x027bf56b in ?? ()
#15 0x027becec in ?? ()
#16 0x027be657 in ?? ()
#17 0x027be4cd in ?? ()
#18 0x027be464 in ?? ()
#19 0x0577d3c1 in ?? ()
#20 0x0577d304 in ?? ()
#21 0x027be411 in ?? ()
#22 0x02d11b24 in ?? ()
#23 0x02d11ab4 in ?? ()
#24 0x02d1139c in ?? ()
#25 0x00dcc8f3 in ?? ()
#26 0x08116fca in ?? ()
#27 0x08117669 in mono_runtime_class_init ()
#28 0x08063061 in ?? ()
#29 0x080d42bb in ?? ()
#30 0x00cb5066 in ?? ()
#31 0x06eba383 in ?? ()
#32 0x06eb9f41 in ?? ()
#33 0x06eb9ed4 in ?? ()
#34 0x06eb9d2d in ?? ()
#35 0x06eb74b6 in ?? ()
#36 0x06eb7369 in ?? ()
#37 0x06eb728d in ?? ()
#38 0x00682711 in ?? ()
#39 0x08110ef4 in mono_runtime_delegate_invoke ()
#40 0x0815285b in ?? ()
#41 0x081c3062 in ?? ()
#42 0x081e1925 in ?? ()
#43 0x0017796e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#44 0x00ec29de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x5b08b70 (LWP 9978)):
#0  0x006f1422 in __kernel_vsyscall ()
#1  0x00eb4b56 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x00b174eb in g_poll () from /lib/libglib-2.0.so.0
#3  0x00b0a0ac in ?? () from /lib/libglib-2.0.so.0
#4  0x00b0a817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x02e05160 in ?? () from /usr/lib/libORBit-2.so.0
#6  0x00b30dcf in ?? () from /lib/libglib-2.0.so.0
#7  0x0017796e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#8  0x00ec29de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x2fafb70 (LWP 9979)):
#0  0x00e68188 in ?? () from /lib/tls/i686/cmov/libc.so.6
#1  0x00b2b814 in g_str_equal () from /lib/libglib-2.0.so.0
#2  0x00af756a in g_hash_table_lookup () from /lib/libglib-2.0.so.0
#3  0x081180ca in ?? ()
#4  0x0805f44b in ?? ()
#5  0x080e164e in ?? ()
#6  0x0805e7d8 in ?? ()
#7  0x0806215b in ?? ()
#8  0x08062e68 in ?? ()
#9  0x080d42bb in ?? ()
#10 0x00cb5066 in ?? ()
#11 0x02d1f1d3 in ?? ()
#12 0x02d1ed89 in ?? ()
#13 0x02d1ea63 in ?? ()
#14 0x02d1e21a in ?? ()
#15 0x02d1da9a in ?? ()
#16 0x02d15c88 in ?? ()
#17 0x02d1548a in ?? ()
#18 0x02d1471b in ?? ()
#19 0x02d13da4 in ?? ()
#20 0x02d13d43 in ?? ()
#21 0x02d13a81 in ?? ()
#22 0x02d138db in ?? ()
#23 0x02d11d2f in ?? ()
#24 0x02d11b80 in ?? ()
#25 0x02d115cc in ?? ()
#26 0x02d112a4 in ?? ()
#27 0x00682711 in ?? ()
#28 0x08110ef4 in mono_runtime_delegate_invoke ()
#29 0x0815285b in ?? ()
#30 0x081c3062 in ?? ()
#31 0x081e1925 in ?? ()
#32 0x0017796e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0x00ec29de in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0x1416f0 (LWP 9973)):
#0  0x006f1422 in __kernel_vsyscall ()
#1  0x00eb4b56 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0x00b174eb in g_poll () from /lib/libglib-2.0.so.0
#3  0x00b0a0ac in ?? () from /lib/libglib-2.0.so.0
#4  0x00b0a817 in g_main_loop_run () from /lib/libglib-2.0.so.0
#5  0x01427299 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#6  0x06eb7fd0 in ?? ()
#7  0x06eb7f7b in ?? ()
#8  0x00dcc4bf in ?? ()
#9  0x00dcc204 in ?? ()
#10 0x08113b1e in mono_runtime_exec_main ()
#11 0x0811429a in mono_runtime_run_main ()
#12 0x080b3524 in mono_main ()
#13 0x0805ad25 in ?? ()
#14 0x00e0bbd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#15 0x0805ac61 in ?? ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted (core dumped)


---

