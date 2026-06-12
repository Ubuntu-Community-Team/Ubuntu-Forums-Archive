---
title: "Can't remove or install &lt;package&gt;"
date: 2018-10-04
forum: Installation &amp; Upgrades
---

### Post by Artnect on 2018-10-04
Hi.

i had installed " kerio-control-vpnclient " in a lower version since i downloaded and tried to upgrade to a newer version ( 9.0 to 9.2 ) i got into this trouble . 
this is output of sudo dpkg --configure kerio-control-vpnclient
```

Setting up kerio-control-vpnclient (9.2.7.2921-1) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Failed to start kerio-kvc.service: Unit kerio-kvc.service is not loaded properly: Exec format error.
See system logs and 'systemctl status kerio-kvc.service' for details.
invoke-rc.d: initscript kerio-kvc, action "start" failed.
&#9679; kerio-kvc.service - Kerio Control VPN Client
   Loaded: error (Reason: Exec format error)
   Active: inactive (dead)

Oct 04 22:03:24 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:33 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:33 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:33 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:53 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:53 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:03:53 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:05:54 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:05:54 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
Oct 04 22:05:54 agha-Satellite-P755 systemd[1]: /lib/systemd/system/kerio-kvc.service:13: Executable path is not absolute: pkill -SIGHUP kvpncsvc
dpkg: error processing package kerio-control-vpnclient (--configure):
 installed kerio-control-vpnclient package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 kerio-control-vpnclient



```
i can neither install or remove it now !

this is output of apt-get install -f

```

E: The package kerio-control-vpnclient needs to be reinstalled, but I can't find an archive for it.

```

---

