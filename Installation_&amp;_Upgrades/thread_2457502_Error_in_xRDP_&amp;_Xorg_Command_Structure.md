---
title: "Error in xRDP &amp; Xorg Command Structure?"
date: 2021-02-03
forum: Installation &amp; Upgrades
---

### Post by w-kym-wittal on 2021-02-03
I recently upgraded from 16.04 LTS to 18.04 LTS and I am having some issues with xRDP.  It partially connects then stops/fails.

From xrdp-sesman.log, I have the following:

  ```

  [20210203-11:13:22] [INFO ] A connection received from ::1 port 55676
  [20210203-11:13:23] [INFO ] ++ created session (access granted): username kym, ip ::ffff:192.168.0.100:27900 - socket: 12
  [20210203-11:13:23] [INFO ] starting Xorg session...
  [20210203-11:13:23] [DEBUG] Closed socket 8 (AF_INET6 :: port 5910)
  [20210203-11:13:23] [DEBUG] Closed socket 8 (AF_INET6 :: port 6010)
  [20210203-11:13:23] [DEBUG] Closed socket 8 (AF_INET6 :: port 6210)
  [20210203-11:13:23] [DEBUG] Closed socket 7 (AF_INET6 ::1 port 3350)
  [20210203-11:13:23] [INFO ] calling auth_start_session from pid 23236
  [20210203-11:13:23] [DEBUG] Closed socket 6 (AF_INET6 ::1 port 3350)
  [20210203-11:13:23] [DEBUG] Closed socket 7 (AF_INET6 ::1 port 3350)
  [20210203-11:13:23] [INFO ] Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -norest -nolisten tcp
  [20210203-11:13:33] [ERROR] X server for display 10 startup timeout
  [20210203-11:13:33] [CORE ] waiting for window manager (pid 23237) to exit
  [20210203-11:13:33] [ERROR] X server for display 10 startup timeout
  [20210203-11:13:33] [ERROR] another Xserver might already be active on display 10 - see log
  [20210203-11:13:33] [DEBUG] aborting connection...
  [20210203-11:13:33] [CORE ] window manager (pid 23237) did exit, cleaning up session
  [20210203-11:13:33] [INFO ] calling auth_stop_session and auth_end from pid 23236
  [20210203-11:13:33] [DEBUG] cleanup_sockets:
  [20210203-11:13:33] [DEBUG] cleanup_sockets: deleting /var/run/xrdp/sockdir/xrdp_chansrv_socket_10
  [20210203-11:13:33] [DEBUG] cleanup_sockets: deleting /var/run/xrdp/sockdir/xrdpapi_10
  [20210203-11:13:33] [DEBUG] cleanup_sockets: failed to delete /var/run/xrdp/sockdir/xrdpapi_10
  [20210203-11:13:33] [INFO ] ++ terminated session:  username kym, display :10.0, session_pid 23236, ip ::ffff:192.168.0.100:27900 - socket: 12

```

Note above the first ERROR, the line:

```
[20210203-11:13:23] [INFO ] Xorg :10 -auth .Xauthority -config xrdp/xorg.conf -norest -nolisten tcp
```

I believe the option -norest should be -noreset.  When I change this line to -noreset and run it from terminal, it appears to work.
I have been trying to find the location of the file/script that generates this line so I can fix it, no luck.

Does anyone know how the line gets generated and how I can fix it?

Thanks, Kym.

---

### Post by w-kym-wittal on 2021-02-04
/etc/xrdp/sesman.ini did not contain parameters for Xorg.  Updated and when connecting via xRDP, works and logs no longer show ERROR -norest, now correct -noreset.

---

