---
title: "Upgraded to Jaunty Jackalope and Samba crashes at start"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pean on 2009-02-27
Just upgrade to Jaunty Jackalope and everything seems to work fine except Samba. I've tried to uninstall, reinstall, reconfigure over and over again, but still get the same crash when I try to start it.

Here it goes:
```
[2009/02/27 17:14:11,  0] smbd/server.c:main(1260)
  smbd version 3.3.0 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/02/27 17:14:11,  0] lib/fault.c:fault_report(40)
  ===============================================================
[2009/02/27 17:14:11,  0] lib/fault.c:fault_report(41)
  INTERNAL ERROR: Signal 11 in pid 17382 (3.3.0)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2009/02/27 17:14:11,  0] lib/fault.c:fault_report(43)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2009/02/27 17:14:11,  0] lib/fault.c:fault_report(44)
  ===============================================================
[2009/02/27 17:14:11,  0] lib/util.c:smb_panic(1673)
  PANIC (pid 17382): internal error
[2009/02/27 17:14:11,  0] lib/util.c:log_stack_trace(1777)
  BACKTRACE: 13 stack frames:
   #0 /usr/sbin/smbd(log_stack_trace+0x1c) [0x7f7710d4e5cd]
   #1 /usr/sbin/smbd(smb_panic+0x5b) [0x7f7710d4e6db]
   #2 /usr/sbin/smbd [0x7f7710d3bdad]
   #3 /lib/libpthread.so.0 [0x7f770f31c080]
   #4 /lib/libc.so.6(strlen+0x30) [0x7f770d8f0c60]
   #5 /lib/libc.so.6(_IO_vfprintf+0x3dbe) [0x7f770d8b975e]
   #6 /lib/libc.so.6(__vasprintf_chk+0xd0) [0x7f770d96ed80]
   #7 /lib/libc.so.6(__asprintf_chk+0x83) [0x7f770d96eca3]
   #8 /usr/sbin/smbd(get_print_db_byname+0x508) [0x7f7710d7b343]
   #9 /usr/sbin/smbd(print_backend_init+0x7d) [0x7f7710d67fec]
   #10 /usr/sbin/smbd(main+0xa25) [0x7f7710c322d1]
   #11 /lib/libc.so.6(__libc_start_main+0xe6) [0x7f770d88e5a6]
   #12 /usr/sbin/smbd [0x7f7710c30d89]
[2009/02/27 17:14:11,  0] lib/util.c:smb_panic(1678)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 17382]
[2009/02/27 17:14:11,  0] lib/util.c:smb_panic(1686)
  smb_panic(): action returned status 0
[2009/02/27 17:14:11,  0] lib/fault.c:dump_core(218)
  Can not dump core: corepath not set up
```


Even tried to upgrade to Samba4 but that was still the same.

I'd appreciate any help, I am kind of dependent on samba working properly...

---

### Post by pean on 2009-03-02
Got and update today with aptitude and everything works fine now.

---

