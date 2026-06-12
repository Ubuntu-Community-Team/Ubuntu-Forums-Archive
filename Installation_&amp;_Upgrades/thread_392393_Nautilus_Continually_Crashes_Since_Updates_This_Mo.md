---
title: "Nautilus Continually Crashes Since Updates This Morning (24th Mar 2007)"
date: 2007-03-24
forum: Installation &amp; Upgrades
---

### Post by mtn on 2007-03-24
Ever since accepting some Nautilus updates this morning (24th Mar 2007), Nautilus seems to continually crash and then generating a bug report. Nautilus then restarts, crashes and and starts another bug report cycle. It is really very annoying. Not found anything in the forums and re-installeding Nautilus through Synaptic has not helped. Any help with this would be greatly appreciated.

Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

> Memory status: size: 143474688 vsize: 0 resident: 143474688 share: 0 rss: 69017600 rss_rlim: 0
CPU usage: start_time: 1174760133 rtime: 0 utime: 302 stime: 0 cutime:262 cstime: 0 timeout: 40 it_real_value: 0 frequency: 23

Backtrace was generated from '/usr/bin/nautilus'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1227446608 (LWP 8521)]
[New Thread -1275831392 (LWP 8549)]
(no debugging symbols found)

(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb73c2803 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb74cbb69 in XProcessInternalConnection () from /usr/lib/libX11.so.6
#3  0xb74cbf4f in _XRead () from /usr/lib/libX11.so.6
#4  0xb74cc924 in _XReply () from /usr/lib/libX11.so.6
#5  0xb74add86 in XGetWindowProperty () from /usr/lib/libX11.so.6
#6  0xb795600e in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
#7  0xb79563bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
#8  0xb79567bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#9  0xb758c802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#10 0xb758f7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#11 0xb758fb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#12 0xb7acd574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#13 0x0807bb4a in POA_Nautilus_MetafileMonitor__init ()
#14 0xb73148cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#15 0x08067621 in ?? ()

Thread 2 (Thread -1275831392 (LWP 8549)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb760034b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7d971b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#5  0xb7328770 in raise () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#6  0xb7329ef3 in abort () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#7  0xb7595122 in g_logv () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb7595159 in g_log () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb75951d6 in g_assert_warning () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb3e5d378 in swfdec_bits_getbits () from /usr/lib/libswfdec-0.3.so.0
No symbol table info available.
#11 0xb3e5ff10 in swfdec_decoder_get_tag_func ()
   from /usr/lib/libswfdec-0.3.so.0
No symbol table info available.
#12 0xb3e5a01d in swfdec_decoder_parse () from /usr/lib/libswfdec-0.3.so.0
No symbol table info available.
#13 0xb3f23124 in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/swf_loader.so
No symbol table info available.
#14 0xb3f233ea in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/swf_loader.so
No symbol table info available.
#15 0xb3f2347c in fill_info ()
   from /usr/lib/gtk-2.0/2.10.0/loaders/swf_loader.so
No symbol table info available.
#16 0xb78eac66 in gdk_pixbuf_loader_write ()
   from /usr/lib/libgdk_pixbuf-2.0.so.0
No symbol table info available.
#17 0xb7da5ec5 in gnome_gdk_pixbuf_new_from_uri_at_scale ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#18 0xb7d9452e in gnome_thumbnail_factory_generate_thumbnail ()
   from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#19 0x08123160 in nautilus_marshal_BOOLEAN__POINTER ()
No symbol table info available.
#20 0xb75f9504 in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#21 0xb73cc51e in clone () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.

Thread 1 (Thread -1227446608 (LWP 8521)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb73c2803 in poll () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#2  0xb74cbb69 in XProcessInternalConnection () from /usr/lib/libX11.so.6
No symbol table info available.
#3  0xb74cbf4f in _XRead () from /usr/lib/libX11.so.6
No symbol table info available.
#4  0xb74cc924 in _XReply () from /usr/lib/libX11.so.6
No symbol table info available.
#5  0xb74add86 in XGetWindowProperty () from /usr/lib/libX11.so.6
No symbol table info available.
#6  0xb795600e in gdk_events_pending () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#7  0xb79563bb in _gdk_events_queue () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#8  0xb79567bf in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#9  0xb758c802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0xb758f7df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#11 0xb758fb89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#12 0xb7acd574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x0807bb4a in POA_Nautilus_MetafileMonitor__init ()
No symbol table info available.
#14 0xb73148cc in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
No symbol table info available.
#15 0x08067621 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()


---

### Post by eapache on 2007-03-24
Is there a trigger that makes it get into the crash loop, or does it do this as soon as you open a nautilus window? I got the update, and it works fine on my machine (also edgy).

---

### Post by SuSUntu on 2007-03-24
Sorry to hear that.

I hesitated this morning when I saw the updates were available, but I went ahead and installed them anyway. Luckily for me, at least so far, I haven't had any trouble at all. I've been on the system almost non-stop for several hours since the updates were installed (even rebooted a couple of times testing some other things). 

I'm running Edgy 32-bit.

---

### Post by mtn on 2007-03-27
> **eapache said:**
> Is there a trigger that makes it get into the crash loop, or does it do this as soon as you open a nautilus window? I got the update, and it works fine on my machine (also edgy).

Hey, doesn't seem to be a trigger. Just starts crashing right from when the desktop loads up! I have not been able to get into the desktop at all the last day as I was being kicking  out to the log in screen every time I tried to log in/boot up. But this afternoon has booted straight in to the desktop, though nautilus still crashing.

Doesn't look like others have had this problem so really not sure what is going on and not sure where to go with this.

---

### Post by mtn on 2007-03-27
> **SuSUntu said:**
> Sorry to hear that.

I hesitated this morning when I saw the updates were available, but I went ahead and installed them anyway. Luckily for me, at least so far, I haven't had any trouble at all. I've been on the system almost non-stop for several hours since the updates were installed (even rebooted a couple of times testing some other things). 

I'm running Edgy 32-bit.

Yeah, I was expecting to find a sticky on the the main forum page alerting people to this issue...looking like it is just me tho!

Thanks

---

### Post by mtn on 2007-03-29
Well...it got worse, could not log in at all, so have (rightly or wrongly) installed Feisty beta. Not sure about stability yet (only been running it for a day - no problems so far), but wow, so much of the post install stuff that I had to do for Edgy is done out-of-the-box, even setting up my wireless card and letting me know it was using proprietary drivers. Well impressed!

Thanks for support, didn't find the problem (I think something must have been corrupted) but has worked out good, I guess.

---

### Post by AlanRogers on 2007-03-29
I experienced a very similar problem on Monday evening, 26th March, but I'm running Dapper. I submitted a bug report to [LaunchPad]("http://www.launchpad.net/ubuntu") but haven't yet heard anything back nor have I experienced the same problem since.

At the time, I was trying to recover 22GB of data from an NTFS drive attached via USB to a Windows 2000 Professional shared folder over the network, so I suspect I was stressing it slightly. In the end, I figured out how to configure Samba and used XCopy on the Windows machine instead; effectively pulling rather than pushing the data, and had no further problem.

I'll keep a weather eye on the bug report though.

---

### Post by sistemico on 2007-04-04
> **AlanRogers said:**
> I experienced a very similar problem on Monday evening, 26th March, but I'm running Dapper. I submitted a bug report to [LaunchPad]("http://www.launchpad.net/ubuntu") but haven't yet heard anything back nor have I experienced the same problem since.

At the time, I was trying to recover 22GB of data from an NTFS drive attached via USB to a Windows 2000 Professional shared folder over the network, so I suspect I was stressing it slightly. In the end, I figured out how to configure Samba and used XCopy on the Windows machine instead; effectively pulling rather than pushing the data, and had no further problem.

I'll keep a weather eye on the bug report though.

I have the same problem, nautilus crashes always. I'm also a Dapper user.

I regularly use "Ext2 IFS for windows" ([http://www.fs-driver.org/)](http://www.fs-driver.org/)), a driver to access my linux filesystem from Windows xp. A corrupted filesystem could be the reason?

---

