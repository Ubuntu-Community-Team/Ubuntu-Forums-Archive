---
title: "Cannot Adjust Date &amp; Time"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by jahmike on 2006-10-27
When trying to Adjust Date & Time I get the following error.

I've tried reinstalling Gnome Tools as well as restarting (not an MS product I guess :)) but nothing gives.  

Any help will be appreciated
  Mike



Bug Buddy Info

[COLOR="Navy"]
[I]
Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 50544640 vsize: 0 resident: 50544640 share: 0 rss: 10838016 rss_rlim: 0
CPU usage: start_time: 1161965236 rtime: 0 utime: 51 stime: 0 cutime:27 cstime: 0 timeout: 24 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/time-admin'

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
[New Thread -1225718096 (LWP 22537)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7324323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eb71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x0804fede in ?? ()
#5  0x08082e50 in ?? ()
#6  0x00000000 in ?? ()

Thread 1 (Thread -1225718096 (LWP 22537)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7324323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eb71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x0804fede in ?? ()
No symbol table info available.
#5  0x08082e50 in ?? ()
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

[/I]
[/COLOR]

---

### Post by pradeepadapa on 2006-10-27
i think still there are many bugs in the edgy eft UBUNTU , so just try to install libthread_db again.

---

### Post by jahmike on 2006-10-27
Not sure how to do this.  Couldn't find under Package Manager as well as console --> aptitude search libthread_db (not sure if it's the same thing).

New 2 linux/ubuntu so bear with me.

Thx for your help.

---

### Post by jahmike on 2006-10-28
Interesting ... 

I installed Xming on windows and connected to my ubuntu box, ran time-admin and bam ... date time interface.

I already adjusted the time via date but this was just an interesting find.

BTW - *nix rabbit hole is deep, but wonderful ... man I'm feeling like such a windows sheep, but I'm not the only one so I guess it's ok :D.

Mike

---

