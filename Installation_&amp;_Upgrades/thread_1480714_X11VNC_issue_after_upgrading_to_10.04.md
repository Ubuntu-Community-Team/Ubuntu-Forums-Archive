---
title: "X11VNC issue after upgrading to 10.04"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by APoCZ on 2010-05-11
[B][FONT=Verdana]Hello,
     I am very illiterate when it comes to Linux in all it's forms, so be gentle. I run Ubuntu for my webserver and for TS3. My server is a headless setup which I use putty to open an SSH tunnel and then X11VNC for the GUI. I have had no issues with this method until I upgraded to Ubuntu 10.04 from 9.10. When I now try to start the X11VNC with -display :0 or -find it is unable to resolve an xdisplay, or so it tells me. Now if I plug a monitor into the server and boot up I can open a X11VNC session with no problems.
     I'll post the errors I get with both -display :0 and -find with a headless setup followed by my graphics information. Also I did have some issues during the upgrade process where it would time out and I had to restart it two more times before it finally finished. Not sure if that would have any purtenance or not. Any help here would be greatly appreciated, thank you all in advance. :)[/FONT][/B]
[B][FONT=Verdana]
-----------------------------------------------------------------------

server@server:~$ x11vnc -usepw -display :0 -xkb -rfbport 5956
11/05/2010 20:33:12 passing arg to libvncserver: -rfbport
11/05/2010 20:33:12 passing arg to libvncserver: 5956
11/05/2010 20:33:12 -usepw: found /home/server/.vnc/passwd
11/05/2010 20:33:12 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1684
11/05/2010 20:33:12 XOpenDisplay(":0") failed.
11/05/2010 20:33:12 Trying again with XAUTHLOCALHOSTNAME=localhost ...

11/05/2010 20:33:12 ***************************************
11/05/2010 20:33:12 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).

** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

** Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

See also: [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)

-----------------------------------------------------------------------

server@server:~$ x11vnc -usepw -find -xkb -rfbport 5956
11/05/2010 20:36:04 passing arg to libvncserver: -rfbport
11/05/2010 20:36:04 passing arg to libvncserver: 5956
11/05/2010 20:36:04 -usepw: found /home/server/.vnc/passwd
11/05/2010 20:36:04 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1685
11/05/2010 20:36:04
11/05/2010 20:36:04 wait_for_client: WAIT:cmd=FINDDISPLAY
11/05/2010 20:36:04
11/05/2010 20:36:04 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
11/05/2010 20:36:04
11/05/2010 20:36:04 Listening for VNC connections on TCP port 5956
11/05/2010 20:36:04

The VNC desktop is:      server:56
PORT=5956
11/05/2010 20:36:10 Got connection from client 192.168.1.21
11/05/2010 20:36:10   other clients:
11/05/2010 20:36:10 incr accepted_client=1 for 192.168.1.21:56261  sock=4
11/05/2010 20:36:10 wait_for_client: got client
11/05/2010 20:36:10 Client Protocol Version 3.8
11/05/2010 20:36:10 Protocol version sent 3.8, using 3.8
11/05/2010 20:36:10 client progressed=1 in 3/6 0.002260 s
11/05/2010 20:36:15 client_set_net: 192.168.1.21  5.0062
11/05/2010 20:36:15 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.sBcS4y
xauth:  /home/server/.Xauthority not writable, changes will be ignored
11/05/2010 20:36:15 wait_for_client: find display cmd failed.
11/05/2010 20:36:15 wait_for_client: bad reply '
'

-----------------------------------------------------------------------

server@server:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 10)
[/FONT][/B]

---

### Post by krunge on 2010-05-11
Are you sure the Xorg X server is even running when you take the monitor off?  Maybe the X server crashes w/o a monitor (this happens often.)  If the X server is not running then x11vnc cannot connect to it (and you get output like that you pasted in.)

Run the command:
```
ps wwaux
```
to see if the "Xorg" or "X" process is listed (i.e. running.)  I don't have access to an ubuntu machine at the moment so I can't tell you what the name would be exactly (i.e. "Xorg" or "X" or perhaps something else.)  Just look through all of the above ps command output looking for a command with "X" in the name.

If you don't see it, it probably crashed. Consult the files /var/log/Xorg.0.log and /var/log/Xorg.0.log.old looking for error messages.

---

### Post by APoCZ on 2010-05-12
[B]Thank you very much for your reply, I checked my running processes the way you described and did not see anything that pertained to Xorg. I have listed the results below. Also I checked the log files and I can see that it gives me an error but I have not the slightest clue as to why. That information is also listed below.

----------------------------------------------------------------------------------[/B] [B]

server@server:~$ ps wwaux[/B] [B]
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23820  2000 ?        Ss   20:10   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    20:10   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    20:10   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    20:10   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    20:10   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    20:10   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    20:10   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    20:10   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    20:10   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    20:10   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    20:10   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    20:10   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    20:10   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    20:10   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    20:10   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    20:10   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    20:10   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    20:10   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    20:10   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    20:10   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    20:10   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    20:10   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    20:10   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    20:10   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    20:10   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    20:10   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    20:10   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    20:10   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    20:10   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    20:10   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    20:10   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    20:10   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    20:10   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   20:10   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    20:10   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    20:10   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    20:10   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    20:10   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    20:10   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    20:10   0:00 [scsi_eh_0]
root        46  0.0  0.0      0     0 ?        S    20:10   0:00 [scsi_eh_1]
root        49  0.0  0.0      0     0 ?        S    20:10   0:00 [kstriped]
root        50  0.0  0.0      0     0 ?        S    20:10   0:00 [kmpathd/0]
root        51  0.0  0.0      0     0 ?        S    20:10   0:00 [kmpathd/1]
root        52  0.0  0.0      0     0 ?        S    20:10   0:00 [kmpath_handlerd]
root        53  0.0  0.0      0     0 ?        S    20:10   0:00 [ksnapd]
root        54  0.0  0.0      0     0 ?        S    20:10   0:00 [kondemand/0]
root        55  0.0  0.0      0     0 ?        S    20:10   0:00 [kondemand/1]
root        56  0.0  0.0      0     0 ?        S    20:10   0:00 [kconservative/0]
root        57  0.0  0.0      0     0 ?        S    20:10   0:00 [kconservative/1]
root       273  0.0  0.0      0     0 ?        S    20:10   0:00 [jbd2/sda1-8]
root       274  0.0  0.0      0     0 ?        S    20:10   0:00 [ext4-dio-unwrit]
root       275  0.0  0.0      0     0 ?        S    20:10   0:00 [ext4-dio-unwrit]
root       335  0.0  0.0  16896   896 ?        S    20:10   0:00 upstart-udev-bridge --daemon
root       338  0.0  0.0  17348  1164 ?        S<s  20:10   0:00 udevd --daemon
root       462  0.0  0.0  17344  1140 ?        S<   20:10   0:00 udevd --daemon
root       487  0.0  0.0  17344  1132 ?        S<   20:10   0:00 udevd --daemon
root       620  0.0  0.0      0     0 ?        S    20:10   0:00 [i915]
root       672  0.0  0.0      0     0 ?        S    20:10   0:00 [hd-audio0]
root       696  0.0  0.1  94284  4528 ?        Ss   20:10   0:00 smbd -F
mysql      703  0.0  0.6 179296 25480 ?        Ssl  20:10   0:01 /usr/sbin/mysqld
syslog     720  0.0  0.0 126076  1720 ?        Sl   20:10   0:00 rsyslogd -c4
root       725  0.0  0.0  49252  1084 ?        Ss   20:10   0:00 /usr/sbin/sshd
root       732  0.0  0.0  94284  1348 ?        S    20:10   0:00 smbd -F
102        735  0.0  0.0  23680  1168 ?        Ss   20:10   0:00 dbus-daemon --system --fork
root       755  0.0  0.0  77344  4024 ?        Ss   20:10   0:00 NetworkManager
avahi      762  0.0  0.0  34044  1640 ?        S    20:10   0:00 avahi-daemon: running [server-2.local]
root       763  0.0  0.0  57856  2516 ?        S    20:10   0:00 /usr/sbin/modem-manager
avahi      764  0.0  0.0  33920   576 ?        Ss   20:10   0:00 avahi-daemon: chroot helper
root       785  0.0  0.0  28344  2100 ?        S    20:10   0:00 /sbin/wpa_supplicant -u -s
root       787  0.0  0.0 122660  3696 ?        Sl   20:10   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       884  0.0  0.0   6072   652 tty4     Ss+  20:10   0:00 /sbin/getty -8 38400 tty4
root       898  0.0  0.0   6072   652 tty5     Ss+  20:10   0:00 /sbin/getty -8 38400 tty5
root       903  0.0  0.0   6072   652 tty2     Ss+  20:10   0:00 /sbin/getty -8 38400 tty2
root       904  0.0  0.0   6072   648 tty3     Ss+  20:10   0:00 /sbin/getty -8 38400 tty3
root       906  0.0  0.0   6072   652 tty6     Ss+  20:10   0:00 /sbin/getty -8 38400 tty6
root       907  0.0  0.0   4420  1124 ?        Ss   20:10   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
root       913  0.0  0.0  21068  1024 ?        Ss   20:10   0:00 cron
daemon     914  0.0  0.0  18876   456 ?        Ss   20:10   0:00 atd
root       966  0.0  0.0  75152  2748 ?        Ss   20:10   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1026  0.0  0.2 197668  9772 ?        Ss   20:10   0:00 /usr/sbin/apache2 -k start
www-data  1034  0.0  0.1 198016  6316 ?        S    20:10   0:00 /usr/sbin/apache2 -k start
www-data  1036  0.0  0.1 197668  5544 ?        S    20:10   0:00 /usr/sbin/apache2 -k start
www-data  1037  0.0  0.1 197668  5544 ?        S    20:10   0:00 /usr/sbin/apache2 -k start
www-data  1038  0.0  0.1 197668  5544 ?        S    20:10   0:00 /usr/sbin/apache2 -k start
www-data  1040  0.0  0.1 197668  6100 ?        S    20:10   0:00 /usr/sbin/apache2 -k start
root      1120  0.0  0.0   6072   648 tty1     Ss+  20:10   0:00 /sbin/getty -8 38400 tty1
root      1328  0.0  0.0  60504  1744 ?        Ss   20:10   0:00 nmbd -D
www-data  1792  0.0  0.1 197668  5544 ?        S    22:24   0:00 /usr/sbin/apache2 -k start
root      1804  0.0  0.1 118536  5252 ?        Ss   23:01   0:00 sshd: server [priv]
server    1869  0.0  0.0 118536  2120 ?        S    23:01   0:00 sshd: server@pts/0
server    1870  0.0  0.0  20980  3792 pts/0    Ss   23:01   0:00 -bash
root      1894  0.0  0.0      0     0 ?        S    23:07   0:00 [flush-8:0]
server    1904  0.0  0.0  15248  1204 pts/0    R+   23:15   0:00 ps wwaux

---------------------------------------------------------------------------------[/B] [B]

server@server:~$ more /var/log/Xorg.0.log[/B] [B]

X.Org X Server 1.7.6[/B] [B]
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux server 2.6.32-22-generic #33-Ubuntu SMP Wed Apr
28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=b2d3b2
b7-712b-416f-9d00-0341b8bff8fa ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue May 11 20:10:30 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevic
es.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:29c2:1458:d000 Intel Corporation 82G33/G31 Express Inte[/B] [B]
grated Graphics Controller rev 16, Mem @ 0xfdf00000/524288, 0xd0000000/268435456
, 0xfdc00000/1048576, I/O @ 0x0000ff00/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(==) Matched intel as autoconfigured driver 0
(==) Matched vesa as autoconfigured driver 1
(==) Matched fbdev as autoconfigured driver 2
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.9.1
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) LoadModule: "fbdev"
(II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
(II) Module fbdev: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.4.1
        ABI class: X.Org Video Driver, version 6.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
        i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
        E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
        965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
        4 Series, G45/G43, Q45/Q43, G41, B43, Clarkdale, Arrandale
(II) VESA: driver for VESA chipsets: vesa
(II) FBDEV: driver for framebuffer: fbdev
(II) Primary Device is: PCI 00@00:02:0
(WW) Falling back to old probe method for vesa
(WW) Falling back to old probe method for fbdev
(II) Loading sub module "fbdevhw"
(II) LoadModule: "fbdevhw"
(II) Loading /usr/lib/xorg/modules/linux/libfbdevhw.so
(II) Module fbdevhw: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 0.0.2
        ABI class: X.Org Video Driver, version 6.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:00:02.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
(II) intel(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:[/B] [B]
no screens found

Please consult the The X.Org Foundation support[/B] [B]
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

 ddxSigGiveUp: Closing log[/B]

---

### Post by krunge on 2010-05-12
> 
(II) intel(0): Integrated Graphics Chipset: Intel(R) G33
(--) intel(0): Chipset: "G33"
(II) intel(0): Output VGA1 has no monitor section
(II) intel(0): EDID for output VGA1
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): No outputs definitely connected, trying again...
(II) intel(0): Output VGA1 disconnected
(WW) intel(0): Unable to find initial modes
(==) intel(0): video overlay key set to 0x101fe
(EE) intel(0): No modes.
(II) UnloadModule: "intel"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found


Yes. See how it is somewhat desperately looking for a monitor (it wants to know the refresh modes it supports) and then giving up? You may want to report this to your distro.

We were able to cook up our own /etc/X11/xorg.conf X server config file with a "fake" monitor:
[INDENT][http://ubuntuforums.org/showthread.php?t=1388613](http://ubuntuforums.org/showthread.php?t=1388613)[/INDENT]
[INDENT][http://ubuntuforums.org/showthread.php?t=1473888](http://ubuntuforums.org/showthread.php?t=1473888)[/INDENT]
and then it worked.

BTW, since you are running it headless, I recommend specifying the "vesa" driver and not the "intel" one that I see in your logfile.  Headless access will be faster with the "vesa" driver.

---

### Post by APoCZ on 2010-05-12
[B]Well once again I appreciate your reply. I had to create a xorg.conf file and copy pasted exactly what was in the link you sent my to. The only problem is I still get the exact same problem as before. I'm not sure what I may have done wrong so I'll post again what I get upon starting x11vnc and my current xorg.conf file.
     I have also tried removing and then reinstalling x11vnc and it's the same outcome. Lastly I apologize for these very long posts, I'm unsure of how to embed pastes into a scrollable format like I have seen others do. Thank you for any help you can give!

------------------------------------------------------------------------

server@server:~$ sudo nano /etc/X11/xorg.conf
[sudo] password for server:
  GNU nano 2.2.2           File: /etc/X11/xorg.conf

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection

------------------------------------------------------------------------

server@server:~$ x11vnc -usepw -display :0 -xkb -rfbport 5956
12/05/2010 11:12:20 passing arg to libvncserver: -rfbport
12/05/2010 11:12:20 passing arg to libvncserver: 5956
12/05/2010 11:12:20 -usepw: found /home/server/.vnc/passwd
12/05/2010 11:12:20 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1488
12/05/2010 11:12:20 XOpenDisplay(":0") failed.
12/05/2010 11:12:20 Trying again with XAUTHLOCALHOSTNAME=localhost ...

12/05/2010 11:12:20 ***************************************
12/05/2010 11:12:20 *** XOpenDisplay failed (:0)

*** x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

** An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the -create
   option if that is what you really want).

** You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

** Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicitly indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

** If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
              -auth /var/lib/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
              -auth /var/run/xauth/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Sometimes the command "ps wwwwaux | grep auth" can reveal the file location.

   Only root will have read permission for the file, and so x11vnc must be run
   as root (or copy it).  The random characters in the filenames will of course
   change and the directory the cookie file resides in is system dependent.

See also: [http://www.karlrunge.com/x11vnc/faq.html](http://www.karlrunge.com/x11vnc/faq.html)

------------------------------------------------------------------------

server@server:~$ x11vnc -usepw -find -xkb -rfbport 5956
12/05/2010 11:13:28 passing arg to libvncserver: -rfbport
12/05/2010 11:13:28 passing arg to libvncserver: 5956
12/05/2010 11:13:28 -usepw: found /home/server/.vnc/passwd
12/05/2010 11:13:28 x11vnc version: 0.9.9 lastmod: 2009-12-21  pid: 1489
12/05/2010 11:13:28
12/05/2010 11:13:28 wait_for_client: WAIT:cmd=FINDDISPLAY
12/05/2010 11:13:28
12/05/2010 11:13:28 initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
12/05/2010 11:13:28
12/05/2010 11:13:28 Listening for VNC connections on TCP port 5956
12/05/2010 11:13:28

The VNC desktop is:      server:56
PORT=5956
12/05/2010 11:13:31 Got connection from client 192.168.1.21
12/05/2010 11:13:31   other clients:
12/05/2010 11:13:31 incr accepted_client=1 for 192.168.1.21:59455  sock=4
12/05/2010 11:13:31 wait_for_client: got client
12/05/2010 11:13:31 Client Protocol Version 3.8
12/05/2010 11:13:31 Protocol version sent 3.8, using 3.8
12/05/2010 11:13:31 client progressed=1 in 0/3 0.000197 s
12/05/2010 11:13:36 client_set_net: 192.168.1.21  5.0060
12/05/2010 11:13:36 wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.1hvePS
xauth:  error in locking authority file /home/server/.Xauthority
12/05/2010 11:13:36 wait_for_client: find display cmd failed.
12/05/2010 11:13:36 wait_for_client: bad reply '
'

------------------------------------------------------------------------

server@server:~$ ps wwaux
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  23820  1996 ?        Ss   11:02   0:00 /sbin/init
root         2  0.0  0.0      0     0 ?        S    11:02   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    11:02   0:00 [migration/0]
root         4  0.0  0.0      0     0 ?        S    11:02   0:00 [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S    11:02   0:00 [watchdog/0]
root         6  0.0  0.0      0     0 ?        S    11:02   0:00 [migration/1]
root         7  0.0  0.0      0     0 ?        S    11:02   0:00 [ksoftirqd/1]
root         8  0.0  0.0      0     0 ?        S    11:02   0:00 [watchdog/1]
root         9  0.0  0.0      0     0 ?        S    11:02   0:00 [events/0]
root        10  0.0  0.0      0     0 ?        S    11:02   0:00 [events/1]
root        11  0.0  0.0      0     0 ?        S    11:02   0:00 [cpuset]
root        12  0.0  0.0      0     0 ?        S    11:02   0:00 [khelper]
root        13  0.0  0.0      0     0 ?        S    11:02   0:00 [netns]
root        14  0.0  0.0      0     0 ?        S    11:02   0:00 [async/mgr]
root        15  0.0  0.0      0     0 ?        S    11:02   0:00 [pm]
root        17  0.0  0.0      0     0 ?        S    11:02   0:00 [sync_supers]
root        18  0.0  0.0      0     0 ?        S    11:02   0:00 [bdi-default]
root        19  0.0  0.0      0     0 ?        S    11:02   0:00 [kintegrityd/0]
root        20  0.0  0.0      0     0 ?        S    11:02   0:00 [kintegrityd/1]
root        21  0.0  0.0      0     0 ?        S    11:02   0:00 [kblockd/0]
root        22  0.0  0.0      0     0 ?        S    11:02   0:00 [kblockd/1]
root        23  0.0  0.0      0     0 ?        S    11:02   0:00 [kacpid]
root        24  0.0  0.0      0     0 ?        S    11:02   0:00 [kacpi_notify]
root        25  0.0  0.0      0     0 ?        S    11:02   0:00 [kacpi_hotplug]
root        26  0.0  0.0      0     0 ?        S    11:02   0:00 [ata/0]
root        27  0.0  0.0      0     0 ?        S    11:02   0:00 [ata/1]
root        28  0.0  0.0      0     0 ?        S    11:02   0:00 [ata_aux]
root        29  0.0  0.0      0     0 ?        S    11:02   0:00 [ksuspend_usbd]
root        30  0.0  0.0      0     0 ?        S    11:02   0:00 [khubd]
root        31  0.0  0.0      0     0 ?        S    11:02   0:00 [kseriod]
root        32  0.0  0.0      0     0 ?        S    11:02   0:00 [kmmcd]
root        35  0.0  0.0      0     0 ?        S    11:02   0:00 [khungtaskd]
root        36  0.0  0.0      0     0 ?        S    11:02   0:00 [kswapd0]
root        37  0.0  0.0      0     0 ?        SN   11:02   0:00 [ksmd]
root        38  0.0  0.0      0     0 ?        S    11:02   0:00 [aio/0]
root        39  0.0  0.0      0     0 ?        S    11:02   0:00 [aio/1]
root        40  0.0  0.0      0     0 ?        S    11:02   0:00 [ecryptfs-kthrea]
root        41  0.0  0.0      0     0 ?        S    11:02   0:00 [crypto/0]
root        42  0.0  0.0      0     0 ?        S    11:02   0:00 [crypto/1]
root        45  0.0  0.0      0     0 ?        S    11:02   0:00 [scsi_eh_0]
root        46  0.0  0.0      0     0 ?        S    11:02   0:00 [scsi_eh_1]
root        49  0.0  0.0      0     0 ?        S    11:02   0:00 [kstriped]
root        50  0.0  0.0      0     0 ?        S    11:02   0:00 [kmpathd/0]
root        51  0.0  0.0      0     0 ?        S    11:02   0:00 [kmpathd/1]
root        52  0.0  0.0      0     0 ?        S    11:02   0:00 [kmpath_handlerd]
root        53  0.0  0.0      0     0 ?        S    11:02   0:00 [ksnapd]
root        54  0.0  0.0      0     0 ?        S    11:02   0:00 [kondemand/0]
root        55  0.0  0.0      0     0 ?        S    11:02   0:00 [kondemand/1]
root        56  0.0  0.0      0     0 ?        S    11:02   0:00 [kconservative/0]
root        57  0.0  0.0      0     0 ?        S    11:02   0:00 [kconservative/1]
root       274  0.0  0.0      0     0 ?        S    11:02   0:00 [jbd2/sda1-8]
root       275  0.0  0.0      0     0 ?        S    11:02   0:00 [ext4-dio-unwrit]
root       276  0.0  0.0      0     0 ?        S    11:02   0:00 [ext4-dio-unwrit]
root       310  0.0  0.0      0     0 ?        S    11:03   0:00 [flush-8:0]
root       336  0.0  0.0  17028   948 ?        S    11:03   0:00 upstart-udev-bridge --daemon
root       339  0.0  0.0  17340  1120 ?        S<s  11:03   0:00 udevd --daemon
root       461  0.0  0.0  17336  1100 ?        S<   11:03   0:00 udevd --daemon
root       462  0.0  0.0  17336  1100 ?        S<   11:03   0:00 udevd --daemon
root       647  0.0  0.0      0     0 ?        S    11:03   0:00 [i915]
root       662  0.0  0.1  94284  4528 ?        Ss   11:03   0:00 smbd -F
mysql      669  0.0  0.6 179296 25484 ?        Ssl  11:03   0:00 /usr/sbin/mysqld
syslog     675  0.0  0.0 126080  2036 ?        Sl   11:03   0:00 rsyslogd -c4
root       680  0.0  0.0  49252  1076 ?        Ss   11:03   0:00 /usr/sbin/sshd
102        688  0.0  0.0  23680  1156 ?        Ss   11:03   0:00 dbus-daemon --system --fork
root       691  0.0  0.0  94284  1348 ?        S    11:03   0:00 smbd -F
root       700  0.0  0.0  77344  4024 ?        Ss   11:03   0:00 NetworkManager
avahi      705  0.0  0.0  34044  1640 ?        S    11:03   0:00 avahi-daemon: running [server-2.local]
root       706  0.0  0.0  57856  2516 ?        S    11:03   0:00 /usr/sbin/modem-manager
avahi      708  0.0  0.0  33920   576 ?        Ss   11:03   0:00 avahi-daemon: chroot helper
root       742  0.0  0.0      0     0 ?        S    11:03   0:00 [hd-audio0]
root       749  0.0  0.0 122660  3672 ?        Sl   11:03   0:00 /usr/sbin/console-kit-daemon --no-daemon
root       762  0.0  0.0  28344  2104 ?        S    11:03   0:00 /sbin/wpa_supplicant -u -s
root       863  0.0  0.0   6072   652 tty4     Ss+  11:03   0:00 /sbin/getty -8 38400 tty4
root       867  0.0  0.0   6072   648 tty5     Ss+  11:03   0:00 /sbin/getty -8 38400 tty5
root       875  0.0  0.0   6072   648 tty2     Ss+  11:03   0:00 /sbin/getty -8 38400 tty2
root       877  0.0  0.0   6072   648 tty3     Ss+  11:03   0:00 /sbin/getty -8 38400 tty3
root       881  0.0  0.0   6072   652 tty6     Ss+  11:03   0:00 /sbin/getty -8 38400 tty6
root       884  0.0  0.0   4420  1116 ?        Ss   11:03   0:00 acpid -c /etc/acpi/events -s /var/run/acpid.socket
daemon     910  0.0  0.0  18876   460 ?        Ss   11:03   0:00 atd
root       911  0.0  0.0  21068  1024 ?        Ss   11:03   0:00 cron
root       932  0.0  0.0  75152  2748 ?        Ss   11:03   0:00 /usr/sbin/cupsd -C /etc/cups/cupsd.conf
root      1002  0.0  0.2 197668  9784 ?        Ss   11:03   0:00 /usr/sbin/apache2 -k start
www-data  1027  0.0  0.1 197668  5556 ?        S    11:03   0:00 /usr/sbin/apache2 -k start
www-data  1028  0.0  0.1 197668  5556 ?        S    11:03   0:00 /usr/sbin/apache2 -k start
www-data  1030  0.0  0.1 197668  5556 ?        S    11:03   0:00 /usr/sbin/apache2 -k start
www-data  1032  0.0  0.1 197668  5556 ?        S    11:03   0:00 /usr/sbin/apache2 -k start
www-data  1033  0.0  0.1 197668  5556 ?        S    11:03   0:00 /usr/sbin/apache2 -k start
root      1074  0.0  0.0   6072   648 tty1     Ss+  11:03   0:00 /sbin/getty -8 38400 tty1
root      1310  0.0  0.0  60504  1744 ?        Ss   11:03   0:00 nmbd -D
root      1339  0.0  0.1 118536  5248 ?        Ss   11:05   0:00 sshd: server [priv]
server    1404  0.0  0.0 118536  2116 ?        S    11:06   0:00 sshd: server@pts/0
server    1405  0.0  0.0  20980  3800 pts/0    Ss   11:06   0:00 -bash
server    1541  0.0  0.0  15248  1204 pts/0    R+   11:14   0:00 ps wwaux

-------------------------------------------------------------------------

server@server:~$ more /var/log/Xorg.0.log

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux server 2.6.32-22-generic #33-Ubuntu SMP Wed Apr
28 13:28:05 UTC 2010 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-22-generic root=UUID=b2d3b2
b7-712b-416f-9d00-0341b8bff8fa ro quiet splash
Build Date: 23 April 2010  05:11:46PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>)
Current version of pixman: 0.16.4
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 12 11:03:09 2010
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "VNC Screen" (0)
(**) |   |-->Monitor "VNC Monitor"
(**) |   |-->Device "VNC Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevic
es.
(II) Loader magic: 0x7ca300
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 6.0
        X.Org XInput driver : 7.0
        X.Org Server Extension : 2.0
(++) using VT number 7

(--) PCI:*(0:0:2:0) 8086:29c2:1458:d000 Intel Corporation 82G33/G31 Express Inte
grated Graphics Controller rev 16, Mem @ 0xfdf00000/524288, 0xd0000000/268435456
, 0xfdc00000/1048576, I/O @ 0x0000ff00/8
(II) Open ACPI successful (/var/run/acpid.socket)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/extra-modules/libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.0
        Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Fri Mar 12 01:17:05 PST 2010
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions/librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions/libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.0.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 1.1.0
        ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) LoadModule: "vesa"
(II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
(II) Module vesa: vendor="X.Org Foundation"
        compiled for 1.7.6, module version = 2.3.0
        Module class: X.Org Video Driver
        ABI class: X.Org Video Driver, version 6.0
(II) VESA: driver for VESA chipsets: vesa
(II) Primary Device is: PCI 00@00:02:0
(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

 ddxSigGiveUp: Closing log

[/B]

---

### Post by krunge on 2010-05-12
After you modified xorg.conf did you restart the X server?  If you don't know how to restart the X server (I believe it will be /etc/init.d/gdm for you), then just reboot the computer.

Then look for the X server process in the ps wwaux output.  There is no point in trying to run x11vnc until the X server is running.

Edit: Oh wait, I see now you did restart it since I see the "VNC" stuff in the Xorg.0.log.  I was confused by the "NVIDIA" strings in there. So now the problem is:
```

(EE) VESA: Kernel modesetting driver in use, refusing to load
(WW) Falling back to old probe method for vesa
(EE) No devices detected.

```
I guess try your "intel" driver instead of "vesa"...  I don't like that "NVIDIA GLX Module" in there.  It looks like something is messed up. Did you install nvidia proprietary drivers on the system?

---

### Post by APoCZ on 2010-05-15
[FONT=Verdana]**Well I tried the intel driver as well with no luck. I tried a reinstall of x11vnc with no luck as well. I'm confused because I have my other server that I upgraded at the same time and it works perfectly. I even tried copying the xorg.conf from the working server and pasting it on the server I'm having issues with. I really have no clue what to do at this point. I have managed to make the server functional again but still have no access to the gui with vnc.**[/FONT]

---

### Post by krunge on 2010-05-15
> Well I tried the intel driver as well with no luck.
That's too bad. I don't know what to suggest to get your X server working.
> I tried a reinstall of x11vnc with no luck as well.
This wouldn't make a difference.  If there is no X server running, x11vnc has nothing to attach to and, of course, will fail.  You need to first get the X server running somehow... (is there a command line X configure tool you can run?)

---

### Post by APoCZ on 2010-05-16
[B]Well I am happy to report that I have found a solution to this issue. It appears that KMS is the culprit and was preventing vesa from loading. I found the information from this thread:

[/B]                                  **Re: x11vnc unable to open xdisplay**    
         
                                                                This thread has  a solution: [_**[COLOR=DarkRed]http://ubuntuforums.org/showthread.php?t=1412565&highlight=monitor&page=2[/COLOR]**_]("http://ubuntuforums.org/showthread.php?t=1412565&highlight=monitor&page=2")

     Code:
     open the terminal and type
gksudo gedit /etc/default/grub

change the line 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash **nomodeset**"

save file 
close
and then
sudo update-grub 

**I just wanted to say thanks for all your help though, I have learned a lot over the last week!**

---

### Post by krunge on 2010-05-16
> I just wanted to say thanks for all your help though, I have learned a lot over the last week!
Thanks, I learned something too: I didn't know KMS (kernel modesetting) existed, and now I know how to disable it when it causes problems.

---

