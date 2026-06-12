---
title: "upgraded to 17.04 and NFS does not connect"
date: 2017-04-21
forum: Installation &amp; Upgrades
---

### Post by likemagic-g on 2017-04-21
In boot process hung at unable to mount NFS drive. Selecting S to skip did not help as the text on the screen scrolled up on line and hung

rpc-statd.service - NFS status monitor for NFSv2/3 locking.
   Loaded: loaded (/lib/systemd/system/rpc-statd.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2017-04-21 22:59:02 NZST; 9min ago
  Process: 2213 ExecStart=/sbin/rpc.statd --no-notify $STATDARGS (code=exited, status=1/FAILURE)

Apr 21 22:59:01 betelgeuse systemd[1]: Starting NFS status monitor for NFSv2/3 locking....
Apr 21 22:59:02 betelgeuse rpc.statd[2214]: Version 1.2.8 starting
Apr 21 22:59:02 betelgeuse rpc.statd[2214]: Flags: TI-RPC
Apr 21 22:59:02 betelgeuse rpc.statd[2214]: Failed to read /var/lib/nfs/state: Success
Apr 21 22:59:02 betelgeuse rpc.statd[2214]: Initializing NSM state
Apr 21 22:59:02 betelgeuse systemd[1]: rpc-statd.service: Control process exited, code=exited status=1
Apr 21 22:59:02 betelgeuse systemd[1]: Failed to start NFS status monitor for NFSv2/3 locking..
Apr 21 22:59:02 betelgeuse systemd[1]: rpc-statd.service: Unit entered failed state.
Apr 21 22:59:02 betelgeuse systemd[1]: rpc-statd.service: Failed with result 'exit-code'.

---

