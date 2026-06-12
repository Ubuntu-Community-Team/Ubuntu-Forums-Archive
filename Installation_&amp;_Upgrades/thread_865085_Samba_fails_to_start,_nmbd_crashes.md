---
title: "Samba fails to start, nmbd crashes"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by fowie on 2008-07-20
HP Netserver running Dapper (Linux 2.6.15-51-686 #1 SMP PREEMPT Tue Feb 12 16:59:15 UTC 2008 i686 GNU/Linux).

Trying to start Samba I get the following error:
```

/etc/init.d/samba: line 25: 28622 Aborted                 start-stop-daemon --start --quiet --oknodo --exec /usr/sbin/nmbd -- -D

```
my /var/log/samba/log.nmbd looks like:
```

[2008/07/20 08:45:19, 0] nmbd/nmbd.c:main(727)
  Netbios nameserver version 3.0.22 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2006
[2008/07/20 08:45:19, 0] lib/fault.c:fault_report(36)
  ===============================================================
[2008/07/20 08:45:19, 0] lib/fault.c:fault_report(37)
  INTERNAL ERROR: Signal 11 in pid 28743 (3.0.22)
  Please read the Trouble-Shooting section of the Samba3-HOWTO
[2008/07/20 08:45:19, 0] lib/fault.c:fault_report(39)
  
  From: http://www.samba.org/samba/docs/Samba3-HOWTO.pdf
[2008/07/20 08:45:19, 0] lib/fault.c:fault_report(40)
  ===============================================================
[2008/07/20 08:45:19, 0] lib/util.c:smb_panic2(1544)
  smb_panic(): calling panic action [/usr/share/samba/panic-action 28743]
[2008/07/20 08:45:19, 0] lib/util.c:smb_panic2(1552)
  smb_panic(): action returned status 0
[2008/07/20 08:45:19, 0] lib/util.c:smb_panic2(1554)
  PANIC: internal error
[2008/07/20 08:45:19, 0] lib/util.c:smb_panic2(1562)
  BACKTRACE: 17 stack frames:
   #0 /usr/sbin/nmbd(smb_panic2+0x78) [0x80cc448]
   #1 /usr/sbin/nmbd(smb_panic+0x19) [0x80cc645]
   #2 /usr/sbin/nmbd [0x80ba445]
   #3 [0xffffe420]
   #4 /lib/tls/i686/cmov/libc.so.6 [0xb7c467e7]
   #5 /lib/tls/i686/cmov/libc.so.6(iconv+0x6a) [0xb7c45e3a]
   #6 /usr/sbin/nmbd [0x80d9236]
   #7 /usr/sbin/nmbd(smb_iconv+0x42) [0x80d92c9]
   #8 /usr/sbin/nmbd [0x80b774d]
   #9 /usr/sbin/nmbd(convert_string+0x1bf) [0x80b7c61]
   #10 /usr/sbin/nmbd(init_doschar_table+0x69) [0x80c7d6f]
   #11 /usr/sbin/nmbd(init_iconv+0xce) [0x80b7448]
   #12 /usr/sbin/nmbd(lp_load+0xcb1) [0x80820de]
   #13 /usr/sbin/nmbd [0x8062342]
   #14 /usr/sbin/nmbd(main+0x1fa) [0x806288b]
   #15 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7c44ebc]
   #16 /usr/sbin/nmbd [0x80614a1]

```

any suggestions?

---

