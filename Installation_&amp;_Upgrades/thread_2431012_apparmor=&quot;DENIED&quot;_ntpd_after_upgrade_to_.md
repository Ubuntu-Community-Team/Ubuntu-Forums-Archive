---
title: "apparmor=&quot;DENIED&quot; ntpd after upgrade to 19.10"
date: 2019-11-10
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2019-11-10
I've just upgraded from (64bit) 19.04 Desktop to 19.10

One of the things that stopped working is ntp after a boot.
 I can start the service manually, but the log shows thew follwoing after a boot

```
Nov 11 20:33:33 LeosHomePc1 systemd[1]: Starting Network Time Service...
Nov 11 20:33:33 LeosHomePc1 ntpd[3837]: ntpd 4.2.8p12@1.3728-o (1): Starting
Nov 11 20:33:33 LeosHomePc1 ntpd[3837]: Command line: /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 129:135
Nov 11 20:33:33 LeosHomePc1 systemd[1]: Started Network Time Service.
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: proto: precision = 0.081 usec (-23)
Nov 11 20:33:33 LeosHomePc1 kernel: [  615.356527] kauditd_printk_skb: 42 callbacks suppressed
Nov 11 20:33:33 LeosHomePc1 kernel: [  615.356529] audit: type=1400 audit(1573464813.175:54): apparmor="DENIED" operation="open" profile="/usr/sbin/ntpd" name="/snap/bin/" pid=3837 comm="ntpd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: leapsecond file ('/usr/share/zoneinfo/leap-seconds.list'): good hash signature
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: leapsecond file ('/usr/share/zoneinfo/leap-seconds.list'): loaded, expire=2020-06-28T00:00:00Z last=2017-01-01T00:00:00Z ofs=37
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen and drop on 0 v6wildcard [::]:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen and drop on 1 v4wildcard 0.0.0.0:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen normally on 2 lo 127.0.0.1:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen normally on 3 enp9s0 192.168.1.10:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen normally on 4 lo [::1]:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listen normally on 5 enp9s0 [fe80::16da:e9ff:fec8:c682%2]:123
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: Listening on routing socket on fd #22 for interface updates
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized
Nov 11 20:33:33 LeosHomePc1 kernel: [  615.397899] audit: type=1107 audit(1573464813.215:55): pid=1433 uid=103 auid=4294967295 ses=4294967295 msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/systemd1" interface="org.freedesktop.systemd1.Manager" member="GetDynamicUsers" mask="send" name="org.freedesktop.systemd1" pid=3840 label="/usr/sbin/ntpd" peer_pid=1 peer_label="unconfined"
Nov 11 20:33:33 LeosHomePc1 kernel: [  615.397899]  exe="/usr/bin/dbus-daemon" sauid=103 hostname=? addr=? terminal=?'
Nov 11 20:33:33 LeosHomePc1 kernel: [  615.619262] [UFW BLOCK] IN=enp9s0 OUT= MAC=01:00:5e:00:00:01:34:e8:94:7b:10:c0:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2
Nov 11 20:33:33 LeosHomePc1 ntpd[3840]: kernel reports TIME_ERROR: 0x41: Clock Unsynchronized
Nov 11 20:33:34 LeosHomePc1 ntpd[3840]: Soliciting pool server 129.250.35.251
```

Thanks

---

