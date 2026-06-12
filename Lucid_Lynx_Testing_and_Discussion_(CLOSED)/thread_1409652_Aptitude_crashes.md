---
title: "Aptitude crashes"
date: 2010-02-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-02-17
Anyone else that uses aptitude experiencing crashes. I've had four in as many days. Core dump crashes. I used the auto bug feature to report it. Each crash reports different results.

I re-installed aptitude. I'll see what happens. I use aptitude in lieu of update-manager:
 'sudo aptitude update && sudo aptitude safe-upgrade'

This is the first time I've had aptitude crash in the last three releases.

---

### Post by Seren on 2010-02-18
Same here.

Luckily I had apt-get still installed.

Edit : Launchpad does not have bug tracking enabled for aptitude so where should we fill bugs ?

---

### Post by mikeyphi on 2010-02-18
Strange - I've used aptitude for some time and never had this problem...including 10 minutes ago!

Edit: as an afterthought I'll add that I removed Plymouth some time ago because my system kept freezing during the boot process however, I wouldn't think that Plymouth affects aptitude?

---

### Post by Seren on 2010-02-18
Does anyone know how to get a core when you are executing a command as root ?

I must probably change ulimit for root, but I am not sure how to do it... "su -" does not seem to work, and sudo ulimit does not work either...

Edit :

That is pretty weird.

If I run 
'sudo aptitude update && sudo aptitude safe-upgrade'  --> crash

If I run
'sudo aptitude update' and then 'sudo aptitude safe-upgrade' --> no crash

Can anyone confirm that behaviour ?


For whatever it worth, here is the backtrace, the crash is systematic.

sudo gdb aptitude
run update && safe-upgrade

```

Program received signal SIGABRT, Aborted.                                                                                                               
0x0012d422 in __kernel_vsyscall ()
(gdb) bt
#0  0x0012d422 in __kernel_vsyscall ()
#1  0x006475e1 in raise () from /lib/tls/i686/cmov/libc.so.6
#2  0x0064aa42 in abort () from /lib/tls/i686/cmov/libc.so.6
#3  0x0067e53d in ?? () from /lib/tls/i686/cmov/libc.so.6
#4  0x006885e1 in ?? () from /lib/tls/i686/cmov/libc.so.6
#5  0x00689e38 in ?? () from /lib/tls/i686/cmov/libc.so.6
#6  0x0068cefd in free () from /lib/tls/i686/cmov/libc.so.6
#7  0x0059e271 in operator delete(void*) () from /usr/lib/libstdc++.so.6
#8  0x0059e2cd in operator delete[](void*) () from /usr/lib/libstdc++.so.6
#9  0x081693bf in ~AcqTextStatus (this=0x8478690, __in_chrg=<value optimized out>) at acqprogress.cc:42
#10 0x081872dd in sigc::internal::signal_emit1<void, download_signal_log&, sigc::nil>::emit (this=0x31a) at /usr/include/sigc++-2.0/sigc++/signal.h:1010
#11 sigc::signal1<void, download_signal_log&, sigc::nil>::emit (this=0x31a) at /usr/include/sigc++-2.0/sigc++/signal.h:2777
#12 sigc::signal1<void, download_signal_log&, sigc::nil>::operator() (this=0x31a) at /usr/include/sigc++-2.0/sigc++/signal.h:2785
#13 download_signal_log::Complete (this=0x31a) at download_signal_log.cc:133
#14 0x0818490e in download_update_manager::finish (this=0xbffff554, res=pkgAcquire::Continue, progress=...) at download_update_manager.cc:275
#15 0x081492a0 in cmdline_do_download (m=0xbffff554, verbose=0) at cmdline_util.cc:404
#16 0x08144ea1 in cmdline_update (argc=1, argv=0xbffff8c8, verbose=0) at cmdline_update.cc:54
#17 0x0805efce in main (argc=2, argv=0xbffff8c4) at main.cc:596
(gdb) q

```

---

### Post by xebian on 2010-02-18
Had the same problem earlier.  Fixed it by using apt-get to purge aptitude and clean the cache and then reinstall.

---

### Post by VMC on 2010-02-18
> **Seren said:**
> Does anyone know how to get a core when you are executing a command as root ?

If I run 
'sudo aptitude update && sudo aptitude safe-upgrade'  --> crash

If I run
'sudo aptitude update' and then 'sudo aptitude safe-upgrade' --> no crash

Can anyone confirm that behaviour ?



That's exactly what I was thinking but first used apt-get to test. No crash. Weird is right. I have used that combination for months without failure until recently.

---

### Post by emarkay on 2010-02-18
"sudo aptitude update && sudo aptitude safe-upgrade" here gives no crash.

I have also removed Plymouth...

---

### Post by VMC on 2010-03-05
Aptitude is still crashing. Here's the latest with this bug report: **[Bug#515525]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/515525")**.
**[SIZE=2]aptitude  assert failure: *** glibc detected *** aptitude: double free or  corruption (!prev): [/SIZE]**

---

### Post by VMC on 2010-03-06
There's a temporary solution for running aptitude until a more permanent fix is issued. Use the "**-q**" option.

> -q : In command-line mode, suppress the incremental progress             indicators.

```
sudo aptitude -q update && sudo aptitude -q safe-upgrade
```

I used it and aptitude completed without incident.

---

### Post by VMC on 2010-04-09
The "real" fix has just arrived - aptitude 0.4.11.11-1ubuntu10

---

