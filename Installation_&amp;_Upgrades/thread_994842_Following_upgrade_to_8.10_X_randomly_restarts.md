---
title: "Following upgrade to 8.10 X randomly restarts"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by budgemook on 2008-11-27
Hi,

I recently upgraded to Ubuntu 8.10

I use a Dell Latitude D600, my architecture type is i686

My lspci:
> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)

My problem is since upgrading, I am experiencing random X server restarts. Everything just stops and I am brought back to the login screen.

I use Gnome but I have some KDE apps installed and use them almost all the time. These apps are konsole and yakuake. I have removed pretty much every other KDE app from my machine while trying to fix this problem but I need these apps for my work.

I replaced my xorg.conf file with a clean one i recieved from my sys admin and restarted but still having the same problem.

Has anyone else experienced this? Here are some logs from /var/log/syslog:
> 
Nov 27 12:03:21 gordon kernel: [10101.192000] ppdev0: registered pardevice
Nov 27 12:03:21 gordon hp: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 27 12:03:21 gordon kernel: [10101.240000] ppdev0: unregistered pardevice
Nov 27 12:03:22 gordon kernel: [10102.376000] ppdev0: registered pardevice
Nov 27 12:03:23 gordon kernel: [10102.420000] ppdev0: unregistered pardevice
Nov 27 12:03:23 gordon kernel: [10102.696000] ppdev0: registered pardevice
Nov 27 12:03:23 gordon python: io/hpmud/pp.c 627: unable to read device-id ret=-1
Nov 27 12:03:23 gordon kernel: [10102.744000] ppdev0: unregistered pardevice
Nov 27 12:03:36 gordon gdm[18309]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Nov 27 12:03:36 gordon kernel: [10116.376000] mtrr: no MTRR for e8000000,2000000 found
Nov 27 12:03:36 gordon console-kit-daemon[5210]: GLib-GObject-CRITICAL: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nov 27 12:03:37 gordon acpid: client connected from 18720[0:0]
Nov 27 12:03:38 gordon kernel: [10117.672000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 27 12:03:38 gordon kernel: [10117.672000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 27 12:03:38 gordon kernel: [10117.672000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 27 12:03:38 gordon kernel: [10117.880000] [drm] Setting GART location based on new memory map
Nov 27 12:03:38 gordon kernel: [10117.880000] [drm] Loading R200 Microcode
Nov 27 12:03:38 gordon kernel: [10117.880000] [drm] writeback test succeeded in 1 usecs
Nov 27 12:03:45 gordon pulseaudio[18813]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 27 12:03:45 gordon pulseaudio[18815]: pid.c: Stale PID file, overwriting.
Nov 27 12:03:45 gordon pulseaudio[18815]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 27 12:03:45 gordon pulseaudio[18815]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 27 12:03:45 gordon gnome-session[18746]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type'
Nov 27 12:03:45 gordon gnome-session[18746]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop
Nov 27 12:03:45 gordon gnome-session[18746]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Nov 27 12:03:47 gordon pulseaudio[18815]: module-x11-xsmp.c: X11 session manager not running.
Nov 27 12:03:47 gordon pulseaudio[18815]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 27 12:03:50 gordon python: hp-systray(init)[18887]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

If somebody could help with this I would really appreciate it. I can't think of anything else to do except backup my files and do a fresh install.

I would be very thankful for any help.

Cheers,

Adrian

---

### Post by rvickers on 2008-11-27
Not that it's any help but my Toshiba laptop does the same thing. I noticed one time that I had a brief message about checking battery status:confused:

---

### Post by budgemook on 2008-11-27
I have some more logs captured from /var/log/syslog:

Running Firefox and Thunderbird - No KDE apps

> Nov 27 12:50:01 gordon /USR/SBIN/CRON[20143]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Nov 27 12:51:50 gordon gdm[18710]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Nov 27 12:51:51 gordon acpid: client connected from 20272[0:0]
Nov 27 12:51:51 gordon kernel: [13010.840000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 27 12:51:51 gordon kernel: [13010.840000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 27 12:51:51 gordon kernel: [13010.840000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 27 12:51:51 gordon kernel: [13011.044000] [drm] Setting GART location based on new memory map
Nov 27 12:51:51 gordon kernel: [13011.044000] [drm] Loading R200 Microcode
Nov 27 12:51:51 gordon kernel: [13011.044000] [drm] writeback test succeeded in 1 usecs
Nov 27 12:51:58 gordon pulseaudio[20364]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 27 12:51:58 gordon pulseaudio[20366]: pid.c: Stale PID file, overwriting.
Nov 27 12:51:58 gordon pulseaudio[20366]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 27 12:51:58 gordon pulseaudio[20366]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 27 12:51:59 gordon gnome-session[20300]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type'
Nov 27 12:51:59 gordon gnome-session[20300]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop
Nov 27 12:51:59 gordon gnome-session[20300]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Nov 27 12:52:00 gordon pulseaudio[20366]: module-x11-xsmp.c: X11 session manager not running.
Nov 27 12:52:00 gordon pulseaudio[20366]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 27 12:52:03 gordon python: hp-systray(init)[20438]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

Running Yakuake and Konsole - No Mozilla apps

> Nov 27 14:28:12 gordon gdm[20265]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Nov 27 14:28:14 gordon acpid: client connected from 22814[0:0]
Nov 27 14:28:15 gordon kernel: [18794.548000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 27 14:28:15 gordon kernel: [18794.548000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 27 14:28:15 gordon kernel: [18794.548000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 27 14:28:15 gordon kernel: [18794.752000] [drm] Setting GART location based on new memory map
Nov 27 14:28:15 gordon kernel: [18794.752000] [drm] Loading R200 Microcode
Nov 27 14:28:15 gordon kernel: [18794.752000] [drm] writeback test succeeded in 2 usecs
Nov 27 14:28:20 gordon bonobo-activation-server (aennis-22826): could not associate with desktop session: Failed to connect to socket /tmp/dbus-BAoWa7uT2k: Connection refused
Nov 27 14:28:26 gordon pulseaudio[22914]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 27 14:28:26 gordon pulseaudio[22916]: pid.c: Stale PID file, overwriting.
Nov 27 14:28:26 gordon pulseaudio[22916]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 27 14:28:26 gordon pulseaudio[22916]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 27 14:28:29 gordon gnome-session[22850]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type'
Nov 27 14:28:29 gordon gnome-session[22850]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop
Nov 27 14:28:29 gordon gnome-session[22850]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Nov 27 14:28:31 gordon pulseaudio[22916]: module-x11-xsmp.c: X11 session manager not running.
Nov 27 14:28:31 gordon pulseaudio[22916]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 27 14:28:35 gordon python: hp-systray(init)[22977]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.

Not running any mozilla or kde apps - running opera and evolution

> Nov 27 14:34:11 gordon gdm[23404]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Nov 27 14:34:12 gordon acpid: client connected from 23821[0:0]
Nov 27 14:34:12 gordon kernel: [19152.392000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Nov 27 14:34:12 gordon kernel: [19152.392000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Nov 27 14:34:12 gordon kernel: [19152.392000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Nov 27 14:34:13 gordon kernel: [19152.596000] [drm] Setting GART location based on new memory map
Nov 27 14:34:13 gordon kernel: [19152.596000] [drm] Loading R200 Microcode
Nov 27 14:34:13 gordon kernel: [19152.596000] [drm] writeback test succeeded in 2 usecs
Nov 27 14:34:16 gordon bonobo-activation-server (aennis-23837): could not associate with desktop session: Failed to connect to socket /tmp/dbus-vD6nLuVEI4: Connection refused
Nov 27 14:34:19 gordon pulseaudio[23921]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov 27 14:34:19 gordon pulseaudio[23923]: pid.c: Stale PID file, overwriting.
Nov 27 14:34:19 gordon pulseaudio[23923]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov 27 14:34:19 gordon pulseaudio[23923]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov 27 14:34:20 gordon gnome-session[23855]: WARNING: Could not parse desktop file /etc/xdg/autostart/update-notifier-kde.desktop: Key file does not have key 'Type'
Nov 27 14:34:20 gordon gnome-session[23855]: WARNING: could not read /etc/xdg/autostart/update-notifier-kde.desktop
Nov 27 14:34:20 gordon gnome-session[23855]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Nov 27 14:34:21 gordon pulseaudio[23923]: module-x11-xsmp.c: X11 session manager not running.
Nov 27 14:34:21 gordon pulseaudio[23923]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Nov 27 14:34:23 gordon python: hp-systray(init)[24006]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.


It's happening very often now. I guess i will have to reinstall

---

### Post by 0xD4 on 2008-11-27
I have had the same problem, with a Toshiba Satellite pro.
It would only happen when I had the external monitor configured as extra screen space (i.e. not clone).
[INDENT](However, as Ubuntu, like most Linux distros, only uses ~3G, I have several small partitions on which I install a different version when I feel like it.
So I had a spare Ubuntu 8.04 kernel, 2.6.24-21-generic, somewhere.)[/INDENT]
So I though this could be due to the kernel and copied the lower version kernel to the Ubuntu 8.10 partition and then X worked fine.

Note: I had so many other issues with Kubuntu 8.10 that I have now downgraded back to Kubuntu 8.04.

I hope this helps.

---

### Post by Xnyper on 2009-03-03
I never had this problem before, after installing Jaunty Alpha 5 I'm getting random x restarts too.

I installed the proprietary nVidia drivers (downloaded the installer from nvidia.com)  and have two monitors going via xinerama, one rotated 90 degrees via XrandR.

It only happens to me while doing command line stuff (not any particular commands... just while working in gnome-terminal) or using vim.  Then again, I spend 90% of my time using vim in a gnome-terminal, so it could be a coincidence.

If I discover anything I'll report back here.  If not I may end up downgrading to the earlier kernel.

---

### Post by anudeglory on 2009-03-10
> **Xnyper said:**
> I never had this problem before, after installing Jaunty Alpha 5 I'm getting random x restarts too.

I installed the proprietary nVidia drivers (downloaded the installer from nvidia.com)  and have two monitors going via xinerama, one rotated 90 degrees via XrandR.

It only happens to me while doing command line stuff (not any particular commands... just while working in gnome-terminal) or using vim.  Then again, I spend 90% of my time using vim in a gnome-terminal, so it could be a coincidence.

If I discover anything I'll report back here.  If not I may end up downgrading to the earlier kernel.


This happens to me also! I too have two screens with Xinerama enabled but with driver version 173.14.16 on Jaunty Alpha 5 and with all updates applied as of posting.

It seems to happen to me if I use the arrow keys or the backspace key but not all of the time and not just in command line either.

It's getting rather annoying hehe.

---

### Post by frodon on 2009-03-11
Maybe post your input in this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337116](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/337116)

---

### Post by tomthumb99 on 2009-03-15
I get this same error, running Nvidia 7600 with dual screens (same as above) Using the nvidia 177.82 driver from their site on an HP a1610n Pavilion (64x dual core amd). But, I am missing the 'Stale PID file' line in log file.  I need to re-boot 2-3x before getting a clean a X win session to come up.  Any ans out there???   I have been living with this for 2 months now.

---

