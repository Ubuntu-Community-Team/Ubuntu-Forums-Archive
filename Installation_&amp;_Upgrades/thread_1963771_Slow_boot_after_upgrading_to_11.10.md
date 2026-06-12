---
title: "Slow boot after upgrading to 11.10"
date: 2012-04-22
forum: Installation &amp; Upgrades
---

### Post by mightyguava on 2012-04-22
I just upgrade an Ubuntu 10.04 Server to 11.10. I ran into dbus not being able to start and fixed it with the symlinking solution floating around the forum. But I'm still running into a slow boot problem.

During boot, I see:
fsck from uti-linux 2.19.1
/dev/sdc1: clean, 111105/525200 files, 920242/2098482 blocks
 * Starting AppArmor profiles   [OK]
 * Settings sensor limits       [OK]
.... more stuff

The problem is, after the "/dev/sdc1: clean", there's about a 2 minute pause before "Starting AppArmor profiles". Smooth sailing after that.

During the pause, the hard drive doesn't seem to be spinning, the computer doesn't seem to be doing anything. Switching to other ttys with Ctrl-Alt-1..6 just show a blinking cursor. Can't ssh in either.

In dmesg, I see
...
[   10.239592] EXT4-fs (md0): recovery complete[   10.240073] EXT4-fs (md0): mounted filesystem with ordered data mode. Opts: (null)[   10.309107] EXT4-fs (md1): warning: maximal mount count reached, running e2fsck is recommended[   10.563934] EXT4-fs (md1): recovery complete[   10.563939] EXT4-fs (md1): mounted filesystem with ordered data mode. Opts: (null)[   11.777126] r8169 0000:04:00.0: eth0: link up[   11.777375] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.278522] init: plymouth-upstart-bridge main process (881) killed by TERM signal
[   12.416128] init: uxlaunch main process (884) terminated with status 2
[   22.528930] eth0: no IPv6 routers present
[   23.981287] init: ssh main process (863) terminated with status 255
[  131.480694] type=1400 audit(1335145529.898:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1749 comm="apparmor_parser"
[  131.480954] type=1400 audit(1335145529.898:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1749 comm="apparmor_parser"
[  131.481113] type=1400 audit(1335145529.898:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1749 comm="apparmor_parser"
[  131.504614] type=1400 audit(1335145529.922:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1750 comm="apparmor_parser"[  131.759874] init: apport pre-start process (1788) terminated with status 1
[  131.761787] init: apport post-stop process (1818) terminated with status 1
...

Has anyone seen a similar issue or know how to fix this?

---

