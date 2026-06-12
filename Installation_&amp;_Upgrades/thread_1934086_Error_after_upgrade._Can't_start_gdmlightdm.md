---
title: "Error after upgrade. Can't start gdm/lightdm"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by mightycoco on 2012-03-01
I just made a apt-get update. After a reboot of the box, i did see the login-screen for some milli-seconds and then i was back on the startup-log showing "* Checking battery state" - after 1-2 seconds again the login screen. It's looping.

I can remote login to the box via SSH and see this in the dmesg log:

[   20.012649] init: udev-fallback-graphics main process (986) terminated with status 1
[   20.384841] audit_printk_skb: 24 callbacks suppressed
[   20.384844] type=1400 audit(1330627787.706:20): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1010 comm="apparmor_parser"
[   20.390755] type=1400 audit(1330627787.710:21): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1010 comm="apparmor_parser"
[   20.421153] init: kdm main process (1002) killed by TERM signal
[   20.588706] init: lightdm main process (999) killed by TERM signal
[   24.200240] eth0: no IPv6 routers present
[   24.498536] Bluetooth: Core ver 2.16
[   24.498573] NET: Registered protocol family 31
[   24.498575] Bluetooth: HCI device and connection manager initialized
[   24.498577] Bluetooth: HCI socket layer initialized
[   24.498578] Bluetooth: L2CAP socket layer initialized
[   24.504770] Bluetooth: SCO socket layer initialized
[   24.568241] Bluetooth: RFCOMM TTY layer initialized
[   24.568248] Bluetooth: RFCOMM socket layer initialized
[   24.568250] Bluetooth: RFCOMM ver 1.11
[   24.580828] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.580832] Bluetooth: BNEP filters: protocol multicast
[   26.289811] gdm-simple-slav[1029]: segfault at 0 ip 004af80e sp bfa16820 error 4 in libnss_compat-2.13.so[4ac000+8000]
[   29.954354] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   30.685977] init: plymouth-stop pre-start process (1378) terminated with status 1
[   38.867690] type=1400 audit(1330627825.597:22): apparmor="DENIED" operation="capable" parent=1757 profile="/usr/sbin/cupsd" pid=1765 comm="serial" capability=21  capname="sys_admin"
[   53.884614] parport0: lp tried to release parport when not owner
[   77.308622] gnome-settings-[1847]: segfault at 4d0 ip 00c83ec5 sp bfca3340 error 4 in libX11.so.6.3.0[c6c000+131000]
[   77.475775] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   79.210918] unity-greeter[1832]: segfault at 4d0 ip 00506ec5 sp bfcb3640 error 4 in libX11.so.6.3.0[4ef000+131000]
[   83.799392] gnome-settings-[2002]: segfault at 4d0 ip 00cc2ec5 sp bf947e80 error 4 in libX11.so.6.3.0[cab000+131000]
[   84.232176] unity-greeter[1986]: segfault at 4d0 ip 00f76ec5 sp bf939b50 error 4 in libX11.so.6.3.0[f5f000+131000]
[   89.490382] gnome-settings-[2182]: segfault at 4d0 ip 00ec8ec5 sp bfdacdd0 error 4 in libX11.so.6.3.0[eb1000+131000]
[   89.874937] unity-greeter[2167]: segfault at 4d0 ip 00ed4ec5 sp bf90bbb0 error 4 in libX11.so.6.3.0[ebd000+131000]
[   93.622229] gnome-settings-[2260]: segfault at 4d0 ip 00887ec5 sp bf87add0 error 4 in libX11.so.6.3.0[870000+131000]
[   94.010361] unity-greeter[2244]: segfault at 4d0 ip 00cd9ec5 sp bfa21480 error 4 in libX11.so.6.3.0[cc2000+131000]
[   97.866652] gnome-settings-[2333]: segfault at 4d0 ip 008afec5 sp bffb8190 error 4 in libX11.so.6.3.0[898000+131000]
[   98.262701] unity-greeter[2319]: segfault at 4d0 ip 00d81ec5 sp bfb9f810 error 4 in libX11.so.6.3.0[d6a000+131000]


Any ideas, why gdm is failing? The same happens if i start 
# lightdm start

#uname -a
Linux ******* 3.0.0-16-generic #28-Ubuntu SMP Fri Jan 27 17:50:54 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by ab1999com on 2012-03-19
I have the same problem,
sometimes gnome-session cause the libX11.so.6.3.0 segfault.
sometimes gnome-setting-daemon also will cause libX11.so.6.3.0 segfault.

---

