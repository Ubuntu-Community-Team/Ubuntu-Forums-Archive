---
title: "Upgraded to 11.04 - now K9copy is broken - help"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by jfl on 2011-06-22
Last week I did the upgrade from Ubuntu 10.10 to 11.04.
Did it on-line, and it went really well; actually the best upgrade since I started with Dapper !
I promptly got rid of the Unity desktop and went back to Gnome.

Everything worked normally, except ..........** K9copy does not work any more**. Whether I invoke it from the terminal or the Apps menu, it open the first window and crashes when trying to read the DVD; here is the terminal output:

```
jf@mainu:~$ k9copy

*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***


*** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1088 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 + 4 ***

KCrash: Application 'k9copy' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/jf/.kde/socket-mainu/kdeinit4__0
QSocketNotifier: Invalid socket 26 and type 'Read', disabling...

[1]+  Stopped                 k9copy
jf@mainu:~$ 
```

The "KDE Crash Handler"  shows this:

```
Application: k9copy (k9copy), signal: Segmentation fault
[Current thread is 1 (Thread 0xb7878710 (LWP 5414))]

Thread 4 (Thread 0xb7625b70 (LWP 5415)):
#0  0x01c04dda in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#1  0x01c44691 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#2  0x0581efd4 in g_main_context_prepare () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x0581fe63 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x0582092b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x01c9d304 in ?? () from /usr/lib/i386-linux-gnu/libgio-2.0.so.0
#6  0x058492df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x00df2e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#8  0x01ffc73e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 3 (Thread 0xb6cffb70 (LWP 5416)):
#0  0x0054f416 in __kernel_vsyscall ()
#1  0x00df7834 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/i386-linux-gnu/libpthread.so.0
#2  0x0200a454 in pthread_cond_timedwait () from /lib/i386-linux-gnu/libc.so.6
#3  0x009d3f0e in ?? () from /usr/lib/i386-linux-gnu/libgthread-2.0.so.0
#4  0x057f342c in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x057f3f6d in g_async_queue_timed_pop () from /lib/i386-linux-gnu/libglib-2.0.so.0
#6  0x0584b980 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#7  0x058492df in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#8  0x00df2e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#9  0x01ffc73e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 2 (Thread 0xb4627b70 (LWP 5417)):
#0  0x0054f416 in __kernel_vsyscall ()
#1  0x01fedf76 in poll () from /lib/i386-linux-gnu/libc.so.6
#2  0x0583084b in g_poll () from /lib/i386-linux-gnu/libglib-2.0.so.0
#3  0x058201af in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
#4  0x05820524 in g_main_context_iteration () from /lib/i386-linux-gnu/libglib-2.0.so.0
#5  0x06705577 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#6  0x066d7289 in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#7  0x066d7522 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/libQtCore.so.4
#8  0x065e12a0 in QThread::exec() () from /usr/lib/libQtCore.so.4
#9  0x066b8fdb in ?? () from /usr/lib/libQtCore.so.4
#10 0x065e3da2 in ?? () from /usr/lib/libQtCore.so.4
#11 0x00df2e99 in start_thread () from /lib/i386-linux-gnu/libpthread.so.0
#12 0x01ffc73e in clone () from /lib/i386-linux-gnu/libc.so.6

Thread 1 (Thread 0xb7878710 (LWP 5414)):
[KCrash Handler]
#7  0x01f99f83 in ?? () from /lib/i386-linux-gnu/libc.so.6
#8  0x01f9bf53 in malloc () from /lib/i386-linux-gnu/libc.so.6
#9  0x08154433 in ifoRead_VTS_PTT_SRPT ()
#10 0x08156925 in ?? ()
#11 0x08156b69 in ifoOpen ()
#12 0x08128e03 in ?? ()
#13 0x08124df8 in ?? ()
#14 0x0811dcd3 in ?? ()
#15 0x080c090d in _start ()
```

This application was working fine for a long time, it always upsets me when an system upgrade destroys functionality without a clue on fixing it.

Thanks in advance for your help !!!

---

### Post by sandoz on 2011-09-03
Are there any news on that?

I still have the same issue.

Thanks,
sandoz

---

### Post by taiwanjohn on 2011-09-07
Same here, I've got the exact same issue. The GUI starts up fine, but as soon as I go to open a disc, it just spouts the following in an endless loop.  

> *** libdvdread: CHECK_VALUE failed in /build/buildd/k9copy-2.3.6/src/dvdread/ifo_read.c:1124 ***
*** for data[i] + sizeof(ptt_info_t) <= vts_ptt_srpt->last_byte + 1 ***


---

### Post by aheller on 2011-09-11
I have the same exact problem and read out as the initial poster. Odd thing is that it was working fine in 11.04, but just quit one day-- no new installs or anything unusual.  Help would be greatly appreciated!

---

