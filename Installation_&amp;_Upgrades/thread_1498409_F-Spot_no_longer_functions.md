---
title: "F-Spot no longer functions"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by thuleni on 2010-05-31
Following the upgrade to : Release 10.04 (lucid)
Kernel Linux 2.6.32-22-generic
GNOME 2.30.0

64 bit AMD, with 1.8Gig RAM

I get the following messages in the log:

May 31 23:55:12 RNI001 kernel: [  738.778984] usb 1-4: USB disconnect, address 3
May 31 23:55:17 RNI001 kernel: [  743.550046] usb 1-4: new high speed USB device using ehci_hcd and address 4
May 31 23:55:17 RNI001 kernel: [  743.707875] usb 1-4: configuration #1 chosen from 1 choice
May 31 23:55:20 RNI001 kernel: [  747.270063] usb 1-4: reset high speed USB device using ehci_hcd and address 4

However, F-Spot does not recognise when I connect my Canon, via the USB cable. (it works on my Windows 7 set-up).

In the previous version of Ubuntu, the camera was recognised immediately, and I could import the photos with F-Spot.

Opening F-Spot via the menu works, but shuts down when I select Import (bizarre).  I re-installed F-Spot, but it makes no difference.

This is real annoying.

---

### Post by thuleni on 2010-05-31
Interestingly, this is what I get when running F-Spot from the root terminal...

** No session dbus found. Starting one **
[Info  00:09:43.612] Initializing DBus
[Info  00:09:43.895] Initializing Mono.Addins
[Info  00:09:45.383] Starting new FSpot server (f-spot 0.6.1.5)
Windows1 (149.0 GB) - gnome-dev-harddisk - Mountpoint file:///media/Windows1 True True Harddrive
Harddrive
Windows2_ (4.0 GB) - gnome-dev-harddisk - Mountpoint file:///media/Windows2_ True True Harddrive
Harddrive
Data - gnome-dev-harddisk - Mountpoint file:///media/disk-2 True True Harddrive
Harddrive
Stacktrace:

  at (wrapper managed-to-native) GdkGlx.Context.glXChooseVisual (intptr,int,int[]) <0x00075>
  at (wrapper managed-to-native) GdkGlx.Context.glXChooseVisual (intptr,int,int[]) <0xffffffff>
  at GdkGlx.Context..ctor (Gdk.Screen,GdkGlx.Context,int[]) <0x000eb>
  at GdkGlx.Context..ctor (Gdk.Screen,int[]) <0x0001f>
  at FSpot.Widgets.PhotoImageView.OnRealized () <0x0007f>
  at Gtk.Widget.realized_cb (intptr) <0x0005a>
  at (wrapper native-to-managed) Gtk.Widget.realized_cb (intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Widget.gtk_widget_show (intptr) <0x00056>
  at (wrapper managed-to-native) Gtk.Widget.gtk_widget_show (intptr) <0xffffffff>
  at Gtk.Widget.Show () <0x00017>
  at ImportCommand.ImportFromFile (PhotoStore,string) <0x006fb>
  at MainWindow.ImportFile (string) <0x0005b>
  at FSpot.Core/ImportCommand.Execute () <0x00103>
  at FSpot.Core.Import (string) <0x0004b>
  at FSpot.Driver.Main (string[]) <0x01806>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	mono() [0x47b77f]
	mono() [0x4aef3f]
	/lib/libpthread.so.0(+0xf8f0) [0x7fdc7277d8f0]
	/usr/lib/fglrx/libGL.so.1(XF86DRIQueryVersion+0xae) [0x7fdc5c91812e]
	/usr/lib/fglrx/libGL.so.1(XF86DRIQueryExtension+0x79) [0x7fdc5c9182c9]
	/usr/lib/fglrx/libGL.so.1(+0x55c70) [0x7fdc5c917c70]
	/usr/lib/fglrx/libGL.so.1(+0x35ff8) [0x7fdc5c8f7ff8]
	/usr/lib/fglrx/libGL.so.1(glXChooseVisual+0x56) [0x7fdc5c8f2146]
	[0x4009bb65]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x7fdc5dea4710 (LWP 2717)]
[New Thread 0x7fdc5f3a3710 (LWP 2710)]
[New Thread 0x7fdc5f5a8710 (LWP 2709)]
[New Thread 0x7fdc62a0f710 (LWP 2707)]
[New Thread 0x7fdc70f17710 (LWP 2691)]
[New Thread 0x7fdc7347e710 (LWP 2690)]
0x00007fdc7277c93d in read () from /lib/libpthread.so.0
  7 Thread 0x7fdc7347e710 (LWP 2690)  0x00007fdc7277d11d in nanosleep ()
   from /lib/libpthread.so.0
  6 Thread 0x7fdc70f17710 (LWP 2691)  0x00007fdc7277bb50 in sem_wait ()
   from /lib/libpthread.so.0
  5 Thread 0x7fdc62a0f710 (LWP 2707)  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  4 Thread 0x7fdc5f5a8710 (LWP 2709)  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  3 Thread 0x7fdc5f3a3710 (LWP 2710)  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
  2 Thread 0x7fdc5dea4710 (LWP 2717)  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/libpthread.so.0
* 1 Thread 0x7fdc73476740 (LWP 2685)  0x00007fdc7277c93d in read ()
   from /lib/libpthread.so.0

Thread 7 (Thread 0x7fdc7347e710 (LWP 2690)):
#0  0x00007fdc7277d11d in nanosleep () from /lib/libpthread.so.0
#1  0x0000000000556342 in ?? ()
#2  0x00007fdc727749ca in start_thread () from /lib/libpthread.so.0
#3  0x00007fdc7224f6cd in clone () from /lib/libc.so.6
#4  0x0000000000000000 in ?? ()

Thread 6 (Thread 0x7fdc70f17710 (LWP 2691)):
#0  0x00007fdc7277bb50 in sem_wait () from /lib/libpthread.so.0
#1  0x00000000004e4aaa in ?? ()
#2  0x0000000000505035 in ?? ()
#3  0x0000000000570073 in ?? ()
#4  0x000000000058de21 in ?? ()
#5  0x00007fdc727749ca in start_thread () from /lib/libpthread.so.0
#6  0x00007fdc7224f6cd in clone () from /lib/libc.so.6
#7  0x0000000000000000 in ?? ()

Thread 5 (Thread 0x7fdc62a0f710 (LWP 2707)):
#0  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b51c in ?? ()
#2  0x0000000000573885 in ?? ()
#3  0x00000000005025cb in ?? ()
#4  0x000000004188d22e in ?? ()
#5  0x0000000002397470 in ?? ()
#6  0x00007fdc6a31bb90 in ?? ()
#7  0x00007fdc6003f0a8 in ?? ()
#8  0x000000004188cfa4 in ?? ()
#9  0x00007fdc732f8990 in ?? ()
#10 0x00007fdc62a0ec50 in ?? ()
#11 0x00007fdc62a0ebc0 in ?? ()
#12 0x00007fdc62a0f710 in ?? ()
#13 0x0000000000000000 in ?? ()

Thread 4 (Thread 0x7fdc5f5a8710 (LWP 2709)):
#0  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b51c in ?? ()
#2  0x0000000000573885 in ?? ()
#3  0x00000000005014b3 in ?? ()
#4  0x00000000413693c8 in ?? ()
#5  0x000000000270d790 in ?? ()
#6  0x00007fdc5f5a8710 in ?? ()
#7  0x0000000000000000 in ?? ()

Thread 3 (Thread 0x7fdc5f3a3710 (LWP 2710)):
#0  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b51c in ?? ()
#2  0x0000000000573885 in ?? ()
#3  0x00000000005014b3 in ?? ()
#4  0x00000000413693c8 in ?? ()
#5  0x000000000270d6d0 in ?? ()
#6  0x0000000000000001 in ?? ()
#7  0x0000000000000206 in ?? ()
#8  0x00007fdc5f3a3710 in ?? ()
#9  0x00007fdc60046bc0 in ?? ()
#10 0x00007fdc5f3a2cc0 in ?? ()
#11 0x00007fdc5f3a2bf0 in ?? ()
#12 0x00007fdc5f3a3710 in ?? ()
#13 0x0000000000000000 in ?? ()

Thread 2 (Thread 0x7fdc5dea4710 (LWP 2717)):
#0  0x00007fdc7277985c in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/libpthread.so.0
#1  0x000000000055b51c in ?? ()
#2  0x0000000000573885 in ?? ()
#3  0x00000000005014b3 in ?? ()
#4  0x00000000413693c8 in ?? ()
#5  0x0000000002ac7480 in ?? ()
#6  0x00007fdc5f624118 in ?? ()
#7  0x0000000000000180 in ?? ()
#8  0x0000000000000000 in ?? ()

Thread 1 (Thread 0x7fdc73476740 (LWP 2685)):
#0  0x00007fdc7277c93d in read () from /lib/libpthread.so.0
#1  0x000000000047b8f4 in ?? ()
#2  0x00000000004aef3f in ?? ()
#3  <signal handler called>
#4  0x00007fdc5c91812e in XF86DRIQueryVersion () from /usr/lib/fglrx/libGL.so.1
#5  0x00007fdc5c9182c9 in XF86DRIQueryExtension ()
   from /usr/lib/fglrx/libGL.so.1
#6  0x00007fdc5c917c70 in ?? () from /usr/lib/fglrx/libGL.so.1
#7  0x00007fdc5c8f7ff8 in ?? () from /usr/lib/fglrx/libGL.so.1
#8  0x00007fdc5c8f2146 in glXChooseVisual () from /usr/lib/fglrx/libGL.so.1
#9  0x000000004009bb65 in ?? ()
#10 0x00007fffb7336c30 in ?? ()
#11 0x0000000002ae7e00 in ?? ()
#12 0x00007fdc732f8000 in ?? ()
#13 0x00007fffb7334ac0 in ?? ()
#14 0x000000000248e800 in ?? ()
#15 0x00007fffb7334880 in ?? ()
#16 0x00007fffb7334680 in ?? ()
#17 0x0000000002ae7e00 in ?? ()
#18 0x00007fdc732f8000 in ?? ()
#19 0x00007fffb7334ac0 in ?? ()
#20 0x00007fdc732f8000 in ?? ()
#21 0x000000004009b3bc in ?? ()
#22 0x0000000000000001 in ?? ()
#23 0x00007fdc6a51bc58 in ?? ()
#24 0x00000000022caa90 in ?? ()
#25 0x00007fdc6a52db98 in ?? ()
#26 0x0000000000000000 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

---

### Post by thuleni on 2010-12-10
I had to re-load Ubuntu due to a gross error in judgement on my behalf.  A new version of F-Spot was included and it now works...

Go Figure

---

### Post by danellisuk on 2011-12-29
I solved this particular crash when pressing the import button (with the same stacktrace), by re-enabling Visual Effects (under System -> Preferences -> Appearance).

I had previously broken visual effects by playing around with my X config, and forgot to put it back.  The simple way was to deactivate and re-activate the AMD graphics driver (System -> Administration -> Hardware Drivers).

I don't know why this affected f-spot, but it did.  Please post if this affected you, and we can raise a bug on launchpad.

---

### Post by directhex on 2011-12-29
F-Spot uses OpenGL to handle some display tasks. It doesn't matter if you don't have an accelerated driver, as software rendering is fast enough - it DOES matter if your 3D drivers are hosed.

---

