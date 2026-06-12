---
title: "Xrdp - unable to log on since upgrade from 18.04 LTS to 20.04 LTS"
date: 2020-09-09
forum: Installation &amp; Upgrades
---

### Post by doubletop12 on 2020-09-09
I've just upgraded from 18.04 to 20.04 and now can't log on remotely with Xrdp from Win10. Prior to the upgrade it worked fine, I could log on with Xrdp and have an SSH terminal session running concurrently from the same PC.   An SSH terminal log on from Win10 still works, but using Windows RDP I get the Xrdp window and enter my details and the Xrdp window then just closes. The behaviour is similar to that when already logged on locally, which is as expected, you can't do both. 

A "who" check in terminal confirms I'm the only person logged on, remotely not local. 

 I've done "sudo adduser xrdp ssl-cert" and restarted Xrdp, just in case that was a problem.  

I've just found the log /var/log/xrdp-sesman.log

```

[20200909-21:13:37] [INFO ] A connection received from ::1 port 42860
[20200909-21:13:37] [INFO ] ++ created session (access granted): username pete, ip ::ffff:192.168.xx.xx:10230 - socket: 12
[20200909-21:13:37] [INFO ] starting Xorg session...
[20200909-21:13:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 5910)
[20200909-21:13:37] [ERROR]** g_tcp_bind(9, 6010) failed bind IPv6 (errno=98) and IPv4 (errno=22).**
[20200909-21:13:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 0)
[20200909-21:13:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 5911)
[20200909-21:13:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 6011)
[20200909-21:13:37] [DEBUG] Closed socket 9 (AF_INET6 :: port 6211)
[20200909-21:13:37] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20200909-21:13:37] [INFO ] calling auth_start_session from pid 3022
[20200909-21:13:37] [DEBUG] Closed socket 7 (AF_INET6 ::1 port 3350)
[20200909-21:13:37] [DEBUG] Closed socket 8 (AF_INET6 ::1 port 3350)
[20200909-21:13:37] [INFO ] /usr/lib/xorg/Xorg :11 -auth .Xauthority -config xrdp/xorg.conf -noreset -nolisten tcp -logfile .xorgxrdp>
[20200909-21:13:37] [CORE ] waiting for window manager (pid 3030) to exit
[20200909-21:13:38] [CORE ] window manager (pid 3030) did exit, cleaning up session
[20200909-21:13:38] [INFO ] calling auth_stop_session and auth_end from pid 3022
[20200909-21:13:38] [DEBUG] cleanup_sockets:
[20200909-21:13:38] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdp_chansrv_audio_out_socket_11
[20200909-21:13:38] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdp_chansrv_audio_in_socket_11
[20200909-21:13:38] [DEBUG] cleanup_sockets: deleting /run/xrdp/sockdir/xrdpapi_11
[20200909-21:13:38] [INFO ] ++ terminated session:  username pete, display :11.0, session_pid 3022, ip ::ffff:192.168.xx.xx:10230 - so
``` 

Pete

---

### Post by doubletop12 on 2020-09-09
Has this problem returned?

[https://github.com/neutrinolabs/xrdp/issues/714](https://github.com/neutrinolabs/xrdp/issues/714)

Pete

---

### Post by doubletop12 on 2020-09-09
Fixed it - it appears to have been a result of an error in the Gnome  install. Discovered on investigating missing icons and doing

```
 sudo apt dist-upgrade
```

Pete

---

