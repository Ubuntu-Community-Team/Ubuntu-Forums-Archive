---
title: "Xubuntu Minimal 24.04 issues with App Armor on install? (Chromebook)"
date: 2024-07-22
forum: Installation &amp; Upgrades
---

### Post by delanthear on 2024-07-22
Straight from install I seem to have having App Armor issues on a Chromebook with Xubuntu Minimal 24.04.  After install I've used snap to install Firebox, Mousam, and Clementine.   All three are generating quite a few DENIED messages and Mousam is completely unable to write out it's config data due to the App Armor policies.

Is it typical to see AppArmor deny's like this for Firefox on straight after install on a fresh Xubunu Install?
```

2024-07-18T13:29:50.207149+01:00 kelly-Swanky kernel: audit: type=1107 audit(1721305790.201:41): pid=492 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.71" pid=1712 label="snap.firefox.firefox" peer_pid=1839 peer_label="unconfined"
2024-07-18T13:29:50.231507+01:00 kelly-Swanky kernel: audit: type=1107 audit(1721305790.230:42): pid=492 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.71" pid=1712 label="snap.firefox.firefox" peer_pid=1839 peer_label="unconfined"
2024-07-18T13:34:10.361495+01:00 kelly-Swanky kernel: audit: type=1107 audit(1721306050.359:43): pid=492 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.90" pid=1712 label="snap.firefox.firefox" peer_pid=2599 peer_label="unconfined"
2024-07-18T13:44:57.680247+01:00 kelly-Swanky kernel: audit: type=1400 audit(1721306697.678:38): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21759/usr/lib/snapd/snap-confine" pid=1692 comm="snap-confine" capability=12  capname="net_admin"
2024-07-18T13:44:57.681219+01:00 kelly-Swanky kernel: audit: type=1400 audit(1721306697.679:39): apparmor="DENIED" operation="capable" class="cap" profile="/snap/snapd/21759/usr/lib/snapd/snap-confine" pid=1692 comm="snap-confine" capability=38  capname="perfmon"
2024-07-18T13:44:58.478316+01:00 kelly-Swanky kernel: audit: type=1400 audit(1721306698.476:40): apparmor="DENIED" operation="open" class="file" profile="snap-update-ns.firefox" name="/usr/local/share/" pid=1718 comm="5" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
2024-07-18T13:45:01.637919+01:00 kelly-Swanky kernel: audit: type=1107 audit(1721306701.635:41): pid=561 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.18" pid=1692 label="snap.firefox.firefox" peer_pid=1017 peer_label="unconfined"
2024-07-18T13:49:41.455382+01:00 kelly-Swanky kernel: audit: type=1107 audit(1721306981.454:42): pid=561 uid=101 auid=4294967295 ses=4294967295 subj=unconfined msg='apparmor="DENIED" operation="dbus_method_call"  bus="system" path="/org/freedesktop/timedate1" interface="org.freedesktop.DBus.Properties" member="GetAll" mask="send" name=":1.99" pid=1692 label="snap.firefox.firefox" peer_pid=2798 peer_label="unconfined"

```

---

### Post by #&amp;thj^% on 2024-07-22
Typical for snap installs, my deb version of firefox:
```
sudo dmesg|grep -e audit -e firefox
[sudo] password for me: 
[    0.230677] audit: initializing netlink subsys (disabled)
[    0.230691] audit: type=2000 audit(1721664257.155:1): state=initialized audit_enabled=0 res=1
[   15.635686] systemd-journald[859]: Collecting audit messages is disabled.
[   20.441530] audit: type=1400 audit(1721664278.228:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="Discord" pid=1556 comm="apparmor_parser"
[   20.441575] audit: type=1400 audit(1721664278.228:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="1password" pid=1555 comm="apparmor_parser"
[   20.441622] audit: type=1400 audit(1721664278.228:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="ch-checkns" pid=1566 comm="apparmor_parser"
[   20.441655] audit: type=1400 audit(1721664278.228:5): apparmor="STATUS" operation="profile_load" profile="unconfined" name="buildah" pid=1562 comm="apparmor_parser"
[   20.441700] audit: type=1400 audit(1721664278.228:6): apparmor="STATUS" operation="profile_load" profile="unconfined" name="brave" pid=1561 comm="apparmor_parser"
[   20.441967] audit: type=1400 audit(1721664278.228:7): apparmor="STATUS" operation="profile_load" profile="unconfined" name="busybox" pid=1563 comm="apparmor_parser"
[   20.441972] audit: type=1400 audit(1721664278.228:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="balena-etcher" pid=1559 comm="apparmor_parser"
[   20.441975] audit: type=1400 audit(1721664278.228:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name=4D6F6E676F444220436F6D70617373 pid=1557 comm="apparmor_parser"
[   20.441977] audit: type=1400 audit(1721664278.228:10): apparmor="STATUS" operation="profile_load" profile="unconfined" name="cam" pid=1565 comm="apparmor_parser"
[   20.441997] audit: type=1400 audit(1721664278.228:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="QtWebEngineProcess" pid=1558 comm="apparmor_parser"

```

What kernel are you running?
```
uname -r
```

---

### Post by delanthear on 2024-07-22
Thanks for answering!

kelly@kelly-Swanky:~$ uname -r
6.8.0-38-generic

---

