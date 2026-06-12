---
title: "[SOLVED] Multiple Crashes"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2008-10-16
I am experiencing multiple crashes of the system - this has been going of for around 48 hours or so...I am up to date as regards all the latest downloads I think...

Oct 16 17:03:29 PJ kernel: [  124.104322] type=1503 audit(1224129809.412:5): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=0 name="/proc/4988/net/" pid=4988 profile="/usr/sbin/cupsd"
Oct 16 17:04:34 PJ kernel: [  189.673183] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
Oct 16 17:05:12 PJ kernel: [  227.042595] type=1503 audit(1224129912.348:6): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6437/net/" pid=6437 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.150725] type=1503 audit(1224129913.456:7): operation="inode_permission" requested_mask="r::" denied_mask="r::" fsuid=7 name="/proc/6442/net/" pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.155597] type=1503 audit(1224129913.460:8): operation="socket_create" family="ax25" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.159171] type=1503 audit(1224129913.464:9): operation="socket_create" family="netrom" sock_type="seqpacket" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.164408] type=1503 audit(1224129913.472:10): operation="socket_create" family="rose" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.164433] type=1503 audit(1224129913.472:11): operation="socket_create" family="ipx" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.164450] type=1503 audit(1224129913.472:12): operation="socket_create" family="appletalk" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.164466] type=1503 audit(1224129913.472:13): operation="socket_create" family="econet" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:05:13 PJ kernel: [  228.164482] type=1503 audit(1224129913.472:14): operation="socket_create" family="ash" sock_type="dgram" protocol=0 pid=6442 profile="/usr/sbin/cupsd"
Oct 16 17:08:58 PJ syslogd 1.5.0#2ubuntu6: restart.

---

