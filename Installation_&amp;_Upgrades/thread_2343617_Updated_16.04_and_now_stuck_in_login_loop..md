---
title: "Updated 16.04 and now stuck in login loop."
date: 2016-11-17
forum: Installation &amp; Upgrades
---

### Post by spot1984 on 2016-11-17
Hi, I'm new here (long time lurker, first time poster),

I've been using Ubuntu (and other Linux flavors) for many years and usually I can wiggle out of these problems but I am at the end of my rope.  I've been trying to fix this for days...

I had a working Ubuntu 16.04 machine (HP Pavilion, Nvidia 7800GT) , I ran many updates from the desktop and when it restarted I was stuck in the graphical login screen loop:  The machine used to boot to the desktop and now it boots to the login screen.  When I enter credentials or log in as guest an uninformative system error dialog flashes on the screen (I had to video it with my phone to see it) and I get booted back to the login screen.  I can log in through TTY ALT-F1 [F2,F3...]

I've tried the usual stuff:
```
rename/delete .Xauthority file
rename/delete /etc/X11/.xorg.conf

```

At first I thought it was the NVIDIA drivers, this machine has a GeForce 7800 GT, it requires the nvidia-304 legacy driver.

I removed the nvidia drivers```
sudo apt-get purge nvidia-*

```
```
sudo apt-get purge nvidia*

```

and installed (or tried to install, I'm not sure, it may be blacklisted) Neuveau drivers three times, each time the screen was corrupted, I had to boot to safe mode, and reinstall the nvidia drivers.

This morning I removed the nvidia drivers AND the video card, now I'm just using the intel chip on the motherboard and I still can't login to a desktop.

Here are some of the operations I've performed, some more than once, and not necessarily in this order...
```
sudo apt-get update
sudo apt-get autoremove
sudo apt-get upgrade

sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
sudo apt-get install nvidia-304
sudo apt-get install ubuntu-desktop
sudo apt-get install lightdm
sudo apt-get install nvidia-common
...

```

and lots of other things, but I've avoided editing configuration files in /etc/... willy nilly.

I had to setup and FTP to get logs off the machine.  Here are some highlights:

end of /var/log/lightdm/lightdm.log:
```
Nov 17 13:44:52 SOLIDServer1 systemd[1]: Starting Daemon for power management...
Nov 17 13:44:52 SOLIDServer1 nmbd[1306]:  * Starting NetBIOS name server nmbd
Nov 17 13:44:52 SOLIDServer1 gnome-session[1559]: gnome-session-is-accelerated: No hardware 3D support.
Nov 17 13:44:52 SOLIDServer1 gnome-session[1559]: gnome-session-check-accelerated: Helper exited with code 256
Nov 17 13:44:52 SOLIDServer1 gnome-session[1559]: gnome-session-binary[1559]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 17 13:44:52 SOLIDServer1 gnome-session-binary[1559]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 17 13:44:52 SOLIDServer1 systemd[1]: Started LSB: start Samba NetBIOS nameserver (nmbd).
Nov 17 13:44:52 SOLIDServer1 nmbd[1306]:    ...done.
Nov 17 13:44:52 SOLIDServer1 systemd[1]: Starting LSB: start Samba SMB/CIFS daemon (smbd)...
Nov 17 13:44:53 SOLIDServer1 dbus[743]: [system] Successfully activated service 'org.freedesktop.UPower'
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Started Daemon for power management.
Nov 17 13:44:53 SOLIDServer1 smbd[1618]:  * Starting SMB/CIFS daemon smbd
Nov 17 13:44:53 SOLIDServer1 smbd[1618]:    ...done.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Started LSB: start Samba SMB/CIFS daemon (smbd).
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Reached target Multi-User System.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Reached target Graphical Interface.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Started Stop ureadahead data collection 45s after completed startup.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Starting Notify bootloader that boot was successful...
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Starting Update UTMP about System Runlevel Changes...
Nov 17 13:44:53 SOLIDServer1 snap[1658]: Ignoring 'booted' on classic
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Started Notify bootloader that boot was successful.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Started Update UTMP about System Runlevel Changes.
Nov 17 13:44:53 SOLIDServer1 systemd[1]: Startup finished in 5.400s (kernel) + 30.360s (userspace) = 35.760s.
Nov 17 13:44:53 SOLIDServer1 ntpdate[1165]: adjust time server 91.189.91.157 offset 0.256509 sec
Nov 17 13:44:58 SOLIDServer1 lightdm[899]: ** (lightdm:899): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Reached target Shutdown.
Nov 17 13:44:58 SOLIDServer1 systemd[1]: Stopping User Manager for UID 1000...
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Starting Exit the Session...
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Stopped target Default.
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Stopped target Basic System.
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Stopped target Paths.
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Stopped target Sockets.
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Stopped target Timers.
Nov 17 13:44:58 SOLIDServer1 systemd[1288]: Received SIGRTMIN+24 from PID 1690 (kill).
Nov 17 13:44:58 SOLIDServer1 systemd[1]: Stopped User Manager for UID 1000.
Nov 17 13:44:58 SOLIDServer1 systemd[1]: Removed slice User Slice of scott.
Nov 17 13:44:58 SOLIDServer1 acpid: client 991[0:0] has disconnected
Nov 17 13:44:58 SOLIDServer1 acpid: client connected from 1696[0:0]
Nov 17 13:44:58 SOLIDServer1 acpid: 1 client rule loaded

```

no errors in /var/log/lightdm/x-0.log, lots of entries that look like this:
```
X.Org X Server 1.18.4
Release Date: 2016-07-19
X Protocol Version 11, Revision 0
Build Operating System: Linux 3.13.0-95-generic i686 Ubuntu
Current Operating System: Linux SOLIDServer1 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:59 UTC 2016 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-47-generic root=UUID=c57f202f-a490-44dc-8a79-c213e8288414 ro quiet splash vt.handoff=7
Build Date: 14 September 2016  03:34:12PM
xorg-server 2:1.18.4-0ubuntu0.1 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.33.6
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov 17 13:44:46 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(II) Server terminated successfully (0). Closing log file.

```

In /var/log/auth.log it looks like I'm getting authentication errors because it can't fine library pam_kwallet.so:
```
Nov 17 13:44:47 SOLIDServer1 lightdm: pam_unix(lightdm-autologin:session): session opened for user scott by (uid=0)
Nov 17 13:44:47 SOLIDServer1 systemd: pam_unix(systemd-user:session): session opened for user scott by (uid=0)
Nov 17 13:44:47 SOLIDServer1 systemd-logind[728]: New session c1 of user scott.
Nov 17 13:44:47 SOLIDServer1 lightdm: pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0
Nov 17 13:44:50 SOLIDServer1 gnome-keyring-daemon[1483]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
Nov 17 13:44:50 SOLIDServer1 gnome-keyring-daemon[1482]: couldn't access control socket: /run/user/1000/keyring/control: No such file or directory
Nov 17 13:44:57 SOLIDServer1 lightdm: pam_unix(lightdm-autologin:session): session closed for user scott
Nov 17 13:44:58 SOLIDServer1 systemd-logind[728]: Removed session c1.
Nov 17 13:44:58 SOLIDServer1 systemd: pam_unix(systemd-user:session): session closed for user scott
Nov 17 13:44:58 SOLIDServer1 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Nov 17 13:44:58 SOLIDServer1 lightdm: PAM adding faulty module: pam_kwallet.so
Nov 17 13:44:58 SOLIDServer1 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Nov 17 13:44:58 SOLIDServer1 lightdm: PAM adding faulty module: pam_kwallet5.so
Nov 17 13:44:58 SOLIDServer1 lightdm: pam_unix(lightdm-greeter:session): session opened for user lightdm by (uid=0)
Nov 17 13:44:58 SOLIDServer1 systemd-logind[728]: New session c2 of user lightdm.
Nov 17 13:44:58 SOLIDServer1 systemd: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Nov 17 13:44:58 SOLIDServer1 lightdm: pam_ck_connector(lightdm-greeter:session): nox11 mode, ignoring PAM_TTY :0
Nov 17 13:44:59 SOLIDServer1 lightdm: PAM unable to dlopen(pam_kwallet.so): /lib/security/pam_kwallet.so: cannot open shared object file: No such file or directory
Nov 17 13:44:59 SOLIDServer1 lightdm: PAM adding faulty module: pam_kwallet.so
Nov 17 13:44:59 SOLIDServer1 lightdm: PAM unable to dlopen(pam_kwallet5.so): /lib/security/pam_kwallet5.so: cannot open shared object file: No such file or directory
Nov 17 13:44:59 SOLIDServer1 lightdm: PAM adding faulty module: pam_kwallet5.so
Nov 17 13:44:59 SOLIDServer1 lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "scott"
Nov 17 13:45:10 SOLIDServer1 login[1345]: pam_unix(login:session): session opened for user scott by LOGIN(uid=0)
Nov 17 13:45:10 SOLIDServer1 systemd: pam_unix(systemd-user:session): session opened for user scott by (uid=0)
Nov 17 13:45:10 SOLIDServer1 systemd-logind[728]: New session 1 of user scott.
Nov 17 13:45:22 SOLIDServer1 sudo:    scott : TTY=tty1 ; PWD=/home/scott ; USER=root ; COMMAND=/usr/sbin/service lightdm stop
Nov 17 13:45:23 SOLIDServer1 sudo: pam_unix(sudo:session): session opened for user root by scott(uid=0)
Nov 17 13:45:23 SOLIDServer1 lightdm: pam_unix(lightdm-greeter:session): session closed for user lightdm
Nov 17 13:45:23 SOLIDServer1 sudo: pam_unix(sudo:session): session closed for user root
Nov 17 13:45:24 SOLIDServer1 dbus[743]: [system] Failed to activate service 'org.bluez': timed out
Nov 17 13:55:29 SOLIDServer1 sudo:    scott : TTY=tty1 ; PWD=/home/scott ; USER=root ; COMMAND=/bin/tar -zcvf logs.tar.gz /var/log/lightdm /var/log/auth.log /var/log/syslog /var/log/dpkg.log /var/log/lastlog /var/log/Xorg.0.log
Nov 17 13:55:29 SOLIDServer1 sudo: pam_unix(sudo:session): session opened for user root by scott(uid=0)

```


In this excerpt from /var/log/Xorg.0.log I see it is failing to load nvidia glx drivers which is not surprising because nvidia has been purged, but is surprising because it should not be looking for these drivers when using the intel chipset on the motherboard:
```
[    40.682] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[    40.683] (II) xfree86: Adding drm device (/dev/dri/card0)
[    40.684] (--) PCI:*(0:0:2:0) 8086:29c2:103c:2a6f rev 2, Mem @ 0xfea00000/524288, 0xd0000000/268435456, 0xfe900000/1048576, I/O @ 0x0000c080/8
[    40.684] (II) LoadModule: "glx"
[    40.684] (II) Loading /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so
[    40.685] (EE) Failed to load /usr/lib/i386-linux-gnu/xorg/extra-modules/libglx.so: libnvidia-tls.so.304.131: cannot open shared object file: No such file or directory
[    40.685] (II) UnloadModule: "glx"
[    40.685] (II) Unloading glx
[    40.685] (EE) Failed to load module "glx" (loader failed, 7)
[    40.685] (==) Matched intel as autoconfigured driver 0
[    40.685] (==) Matched intel as autoconfigured driver 1
[    40.685] (==) Matched modesetting as autoconfigured driver 2
[    40.685] (==) Matched fbdev as autoconfigured driver 3
[    40.685] (==) Matched vesa as autoconfigured driver 4
[    40.685] (==) Assigned the driver to the xf86ConfigLayout
[    40.685] (II) LoadModule: "intel"
[    40.685] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    40.685] (II) Module intel: vendor="X.Org Foundation"
[    40.685]     compiled for 1.18.3, module version = 2.99.917
[    40.685]     Module class: X.Org Video Driver
[    40.685]     ABI class: X.Org Video Driver, version 20.0
[    40.685] (II) LoadModule: "modesetting"
[    40.686] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    40.686] (II) Module modesetting: vendor="X.Org Foundation"
[    40.686]     compiled for 1.18.4, module version = 1.18.4
[    40.686]     Module class: X.Org Video Driver
[    40.686]     ABI class: X.Org Video Driver, version 20.0
[    40.686] (II) LoadModule: "fbdev"
[    40.686] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    40.686] (II) Module fbdev: vendor="X.Org Foundation"
[    40.686]     compiled for 1.18.1, module version = 0.4.4
[    40.686]     Module class: X.Org Video Driver
[    40.686]     ABI class: X.Org Video Driver, version 20.0
[    40.686] (II) LoadModule: "vesa"
[    40.686] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    40.686] (II) Module vesa: vendor="X.Org Foundation"
[    40.686]     compiled for 1.18.1, module version = 2.3.4
[    40.686]     Module class: X.Org Video Driver
[    40.686]     ABI class: X.Org Video Driver, version 20.0
[    40.686] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    40.687] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    40.687] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    40.687] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    40.687] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    40.687] (II) FBDEV: driver for framebuffer: fbdev
[    40.687] (II) VESA: driver for VESA chipsets: vesa
[    40.687] (II) intel(0): Using Kernel Mode Setting driver: i915, version 1.6.0 20151010
[    40.687] (II) intel(0): SNA compiled: xserver-xorg-video-intel 2:2.99.917+git20160325-1ubuntu1.1 (Timo Aaltonen <tjaalton@debian.org>)
[    40.687] (II) intel(0): SNA compiled for use with valgrind
[    40.687] (WW) Falling back to old probe method for modesetting
[    40.687] (WW) Falling back to old probe method for fbdev
[    40.687] (II) Loading sub module "fbdevhw"

```


I'm out of ideas, out of my depth (I may have multiple problems to deal with at this point), and I cannot find additional information on the web and in these forums.  I can provide more logs and files if needed.  Any help you can provide would be GREATLY appreciated.  

~ Scott

---

### Post by ubfan1 on 2016-11-17
Did you try the "nomodeset" on the grub line starting with linux (replace the words "quiet splash" to see more errors.  Which nvidia driver gets selected from the Software Updater/settings/additional drivers?  maybe a more current one might work.  There is the "tested" version of the driver and maybe an update, which again might or might not work better. Usually once the nvidia drivers are installed, you don't need the nomodeset any more.  Check the /etc/modprobe.d blacklists for any leftovers  for nouveau or nvidia. Have you tried an older kernel (with its working nvidia module) to see if that still works?

---

### Post by spot1984 on 2016-11-19
Thanks ubfan1,


[LIST]
[*]Tried **nomodeset **and **quiet splash**.  They worked fine but I still get the login screen and cannot log in from graphic interface - I get a flash of a system error message and get kicked back to the graphical login screen.
[*]Checked all blacklists, no mention of nvidia or neuveau.
[*]Booted from a few kernels in my grub list, same result.  I have 11 of them, I tried the latest of course 4.4.0-47-generic, 4.4.0-31-generic the oldest 4.4.0 kernel I have, and 3.19.0-30 generic, the oldest 3.19.0 kernel I have.  I've also recovery mode and upstart versions, all with the same issue.
[*]I can always CTRL-F1 and login fine, so I don't think it is an authorization issue.
[/LIST]
 
Can anyone make sense of what I posted in the logs?  Am I overlooking a log, or something in the logs?  

~Scott

P.S. *MAN!* ~ I really wish the logs were standardized so you could **grep **or ** find** standardized error/warning/debug messages.  For now I'm looking for "(EE)", or "failure",  or "error", or "the fail whale"...

---

### Post by ubfan1 on 2016-11-19
My auth.log has the same errors, so that's probably not causing the problem.  Oddly, in the Xorg.0.log, the path [FONT=lucida console][SIZE=1][COLOR=#b22222]/usr/lib/i386-linux-gnu/xorg/extra-modules/[/COLOR][/SIZE][/FONT] is different on my 64 bit  16.04, it's /usr/lib/i386-linux-gnu/xorg/x11-extra-modules (but it's empty).  I have an Nvidia Quattro 1000M, running the 367 driver. Take a look at .xsession-errors in your home directory.  Have you tried starting X manually and using another window manager ?

---

### Post by spot1984 on 2016-11-19
Thanks re. the auth.log errors. 

I just put the NVidia 7800 GT back in the system and reinstalled the drivers.

```
sudo apt-get update
sudo apt-get install nvidia-304
sudo apt-get insrall nvidia-current (did nothing, was up to date)
sudo nvidia-settings  (create generic /etc/X11/xorg.conf)
```

x-0.log, Xorg.0.log, look benign

```
~/.xsession-errors:[INDENT]X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  155 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  34
  Current serial number in output stream:  35
openConnection: connect: No such file or directory
cannot connect to brltty at :0
upstart: gnome-session (Unity) main process (2239) terminated with status 1
upstart: unity-settings-daemon main process (2230) killed by TERM signal
upstart: logrotate main process (2070) killed by TERM signal
upstart: update-notifier-crash (/var/crash/_sbin_upstart.112.crash) main process (2132) killed by TERM signal
upstart: bamfdaemon main process (2157) killed by TERM signal
upstart: hud main process (2228) killed by TERM signal
upstart: unity-panel-service main process (2243) killed by TERM signal
upstart: Disconnected from notified D-Bus bus
upstart: unity7 pre-start process (2233) terminated with status 143
```

Here is the tail of my syslog now
```
Nov 19 18:43:58 SOLIDServer1 systemd[1]: Started User Manager for UID 1000.
Nov 19 18:43:59 SOLIDServer1 org.ayatana.bamf[2081]: bamfdaemon start/running, process 2157
 Nov 19 18:43:59 SOLIDServer1 org.a11y.Bus[2081]: ** (process:2180): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nov 19 18:43:59 SOLIDServer1 org.a11y.Bus[2081]: Activating service name='org.a11y.atspi.Registry'
Nov 19 18:43:59 SOLIDServer1 org.a11y.Bus[2081]: Successfully activated service 'org.a11y.atspi.Registry'
Nov 19 18:43:59 SOLIDServer1 org.a11y.atspi.Registry[2193]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
 Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: X Error of failed request:  BadValue (integer parameter out of range for operation)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Major opcode of failed request:  155 (GLX)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Minor opcode of failed request:  3 (X_GLXCreateContext)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Value in failed request:  0x0
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Serial number of failed request:  26
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Current serial number in output stream:  27
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: gnome-session-check-accelerated: Helper exited with code 256
Nov 19 18:44:00 SOLIDServer1 gnome-session-binary[2239]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: gnome-session-binary[2239]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 19 18:44:01 SOLIDServer1 lightdm[994]: ** (lightdm:994): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed
Nov 19 18:44:01 SOLIDServer1 systemd[1]: Stopping User Manager for UID 1000...
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Stopped target Default.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Stopped target Basic System.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Stopped target Paths.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Stopped target Timers.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Reached target Shutdown.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Starting Exit the Session...
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Stopped target Sockets.
Nov 19 18:44:01 SOLIDServer1 systemd[1911]: Received SIGRTMIN+24 from PID 2282 (kill).
Nov 19 18:44:01 SOLIDServer1 systemd[1]: Stopped User Manager for UID 1000.
Nov 19 18:44:01 SOLIDServer1 systemd[1]: Removed slice User Slice of scott.
Nov 19 18:44:01 SOLIDServer1 acpid: client 1648[0:0] has disconnected
Nov 19 18:44:01 SOLIDServer1 acpid: client connected from 2288[0:0]
Nov 19 18:44:01 SOLIDServer1 acpid: 1 client rule loaded
Nov 19 18:44:01 SOLIDServer1 systemd[1]: Started Session c4 of user lightdm.
Nov 19 18:44:02 SOLIDServer1 org.a11y.atspi.Registry[2314]: SpiRegistry daemon is running with well-known name - org.a11y.atspi.Registry
Nov 19 18:44:02 SOLIDServer1 org.gnome.ScreenSaver[2306]: ** (gnome-screensaver:2396): WARNING **: Couldn't get presence status: No such interface 'org.freedesktop.DBus.Properties' on object at path /org/gnome/SessionManager/Presence
Nov 19 18:44:02 SOLIDServer1 org.gnome.ScreenSaver[2306]: ** (gnome-screensaver:2396): WARNING **: screensaver already running in this session
Nov 19 18:44:06 SOLIDServer1 pulseaudio[1834]: [pulseaudio] bluez5-util.c: GetManagedObjects() failed: org.freedesktop.DBus.Error.TimedOut: Failed to activate service 'org.bluez': timed out
Nov 19 18:44:08 SOLIDServer1 acpid: client 2288[0:0] has disconnected
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Created slice User Slice of scott.
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Starting User Manager for UID 1000...
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Started Session 1 of user scott.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Reached target Paths.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Reached target Sockets.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Reached target Timers.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Reached target Basic System.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Reached target Default.
Nov 19 18:44:17 SOLIDServer1 systemd[2472]: Startup finished in 65ms.
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Started User Manager for UID 1000.
Nov 19 18:44:17 SOLIDServer1 dbus[723]: [system] Activating via systemd: service name='org.freedesktop.ConsoleKit' unit='console-kit-daemon.service'
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Starting Console Manager...
 Nov 19 18:44:17 SOLIDServer1 console-kit-daemon[2480]: (process:2544): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Nov 19 18:44:17 SOLIDServer1 console-kit-daemon[2480]: missing action
Nov 19 18:44:17 SOLIDServer1 dbus[723]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Nov 19 18:44:17 SOLIDServer1 systemd[1]: Started Console Manager.
 Nov 19 18:44:17 SOLIDServer1 console-kit-daemon[2480]: (process:2556): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
Nov 19 18:44:26 SOLIDServer1 systemd[1]: Starting Stop ureadahead data collection...
Nov 19 18:44:26 SOLIDServer1 systemd[1]: Stopped Read required files in advance.
Nov 19 18:44:26 SOLIDServer1 systemd[1]: Started Stop ureadahead data collection.
```
Interestingly in /var/logs/lightdm/seat0-greeter.log:

```

** (process:2309): WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Activating service name='org.a11y.atspi.Registry'
[+0.00s] DEBUG: unity-greeter.vala:502: Starting unity-greeter 16.04.2 UID=112 LANG=en_US.UTF-8
[+0.00s] DEBUG: unity-greeter.vala:505: Setting cursor
[+0.00s] DEBUG: unity-greeter.vala:519: Loading command line options
[+0.00s] DEBUG: unity-greeter.vala:547: Setting GTK+ settings
Successfully activated service 'org.a11y.atspi.Registry'
[+0.09s] DEBUG: unity-greeter.vala:570: Creating Unity Greeter
[+0.09s] DEBUG: unity-greeter.vala:57: Creating background surface
[+0.09s] DEBUG: Connecting to display manager...
[+0.09s] DEBUG: Wrote 22 bytes to daemon
[+0.09s] DEBUG: Read 8 bytes from daemon
[+0.09s] DEBUG: Read 150 bytes from daemon
[+0.09s] DEBUG: Connected version=1.18.3 default-session=ubuntu show-manual-login=false hide-users=false has-guest-account=true show-remote-login=true
[+0.13s] DEBUG: menubar.vala:335: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.14s] DEBUG: menubar.vala:367: LANG=en_US.UTF-8 LANGUAGE=(null)
[+0.14s] DEBUG: Loading users from org.freedesktop.Accounts
[+0.14s] DEBUG: User /org/freedesktop/Accounts/User1000 added
[+0.15s] DEBUG: user-list.vala:1030: Adding/updating user scott (scott)
[+0.15s] DEBUG: Loading sessions from org.freedesktop.DisplayManager
[+0.15s] DEBUG: user-list.vala:1012: Adding guest account entry
[+0.25s] DEBUG: Loaded session /usr/share/xsessions/ubuntu.desktop (Ubuntu, This session logs you into Ubuntu)
[+0.25s] DEBUG: Starting authentication for user scott...
[+0.25s] DEBUG: Wrote 21 bytes to daemon
[+0.26s] DEBUG: main-window.vala:185: Screen is 1680x1050 pixels
[+0.26s] DEBUG: main-window.vala:193: Monitor 0 is 1680x1050 pixels at 0,0
[+0.26s] DEBUG: unity-greeter.vala:573: Showing greeter
[+0.26s] DEBUG: unity-greeter.vala:257: Showing main window
[+0.26s] DEBUG: background.vala:483: Regenerating backgrounds
[+0.26s] DEBUG: background.vala:68: Making background /usr/share/backgrounds/warty-final-ubuntu.png at 1680x1050
[+0.32s] DEBUG: unity-greeter.vala:616: Starting main loop
[+0.32s] DEBUG: Read 8 bytes from daemon
[+0.32s] DEBUG: Read 35 bytes from daemon
[+0.32s] DEBUG: Prompt user with 1 message(s)
[+0.49s] DEBUG: background.vala:68: Making background /home/scott/Pictures/20150927_204844.jpg at 1680x1050
[+0.50s] DEBUG: User /org/freedesktop/Accounts/User112 added
[+0.50s] DEBUG: background.vala:159: Error loading background: Failed to open file '/home/scott/Pictures/20150927_204844.jpg': Permission denied
[+0.52s] DEBUG: settings-daemon.vala:75: Acquired org.gnome.SessionManager
[+0.52s] DEBUG: settings-daemon.vala:102: Acquired org.gnome.ScreenSaver
[+0.52s] DEBUG: settings-daemon.vala:159: All bus names acquired, starting unity-settings-daemon
[+0.60s] DEBUG: Connected to Application Indicator Service.
[+0.69s] DEBUG: menubar.vala:537: Adding indicator object 0x8a1318c at position 0
[+0.70s] DEBUG: menubar.vala:537: Adding indicator object 0x8a1324c at position 1
[+0.71s] DEBUG: menubar.vala:537: Adding indicator object 0x8a133cc at position 2
[+0.75s] DEBUG: menubar.vala:537: Adding indicator object 0x8a130cc at position 3
[+0.75s] DEBUG: Request current apps
[+0.85s] DEBUG: unity-greeter.vala:240: starting system-ready sound
[+0.93s] DEBUG: background.vala:121: Render of background /home/scott/Pictures/20150927_204844.jpg complete
[+0.93s] DEBUG: background.vala:138: images[0] was null for /home/scott/Pictures/20150927_204844.jpg
(nm-applet:2347): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkWidget'

(nm-applet:2347): Gtk-CRITICAL **: gtk_widget_show: assertion 'GTK_IS_WIDGET (widget)' failed

** (unity-settings-daemon:2408): WARNING **: Unable to register client: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: No such method 'RegisterClient'
[+1.30s] DEBUG: Building new application entry: :1.17  with icon: nm-device-wired at position 0
[+1.30s] DEBUG: menubar.vala:537: Adding indicator object 0x8aa7a70 at position 4
[+1.33s] DEBUG: background.vala:121: Render of background /usr/share/backgrounds/warty-final-ubuntu.png complete
[+15.69s] DEBUG: user-list.vala:1030: Adding/updating user scott (scott)

```

Ignore the Permission denied, I just fixed that and all I got was by desktop background displaying on the login screen. ;-)

I also: 
```
sudo chmod 655 ~/.Xauthority 
sudo chmod 666 /etc/X11/xorg.conf
```


Changing permissions didn't look like it had any effect, and I didn't see any indication in the logs that it was a cause, It looks now like all I have is the GLX error to deal with using nvidia-304. What is that? 

HELP!  :p

~Scott

---

### Post by klm3030 on 2016-11-19
This problem, not able to login to 16.04 after upgrade if you have  nvidia graphics is showing up by the gazillions, I certainly hope that the right people are working it because it is very very serious.

---

### Post by ubfan1 on 2016-11-20
Can you run the "try Ubuntu" on the install media?  Does the guest session still have the problem too? (If not, the problem is in your other dot files, like .cache or .config.  Backup your files, installed packages, and configs now, just in case.  Is this 16,04 a result of upgrading an earlier release?  If so, maybe best to backup, reinstall a fresh copy, get the Nvidia drivers installed, then restore your files.  Ever run a disk check -- the smartmontools package and then run sudo smartctl -a /dev/sda to get a report.  HP/Nvidia got a bad reputation for insufficient cooling resulting in cracking of the solder pads on the Nvidia chip, which as well as video, controlled the hard disk, USB, and wireless.  You problems seem to be software, but...

---

### Post by spot1984 on 2016-11-20
Another friend suggested I try booting fresh from USB, I'll try that or burning a DVD today (downloading now).

The same login loop occurs with the guest session too, and is present when booting from any of the 11 kernel version available from Grub boot loader.

Thanks for the hardware tip, I'll add that to my troubleshooting list.

~Scott

---

### Post by spot1984 on 2016-11-20
klm3030,

Where are you seeing these reports show up?

This looks like when gnome suddenly required 3D acceleration in 14.x a few years ago (spoiler alert, the desktop does not actually REQUIRE 3D acceleration).
I hope we get a driver update and this goes away ;-)

~ Scott

---

### Post by spot1984 on 2016-11-20
This post looks like the same thing, 9 pages and still no resolution.
[https://ubuntuforums.org/showthread.php?t=2342858](https://ubuntuforums.org/showthread.php?t=2342858)

:-/

~Scott

---

### Post by spot1984 on 2016-11-20
I tried the latest 32 bit live disk (DVD).

The first time I tried it I saw graphics during the boot but never got to a desktop - there was blocky graphical corruption and the machine hung: I could not get to a terminal, and power button did not cause shutdown.  This is what happened when I purged the NVidia drivers and tried to use Nouveau several times previously.

I removed the NVidia card and was able to boot the machine to Try Ubuntu desktop using the onboard Intel chipset.  

I cannot however get past the logon screen on my installation, still getting the flash of "System Problem Detected, would you like to report?).  It really smells like libraries or configuration to me but I don't know what to do next.

~ Scott

---

### Post by anonymousplayer on 2016-11-22
If you have intel integrated graphics, try boot into recovery or upstart and run```
sudo prime-select intel
```
then start desktop to see if it works```
sudo service lightdm start
```
I had a different problem related to nvidia and I worked around it this way.

---

### Post by ubfan1 on 2016-11-22
Did you ever check your BIOS settings for anything relating to video?  Some machines will switch back and forth between internal (Intel) graphics and discrete (Nvidia) automatically under some settings.  Pick one or the other, and see if the appropriate driver will work.  There may be a way (bumblebee,...?) to work with such graphics switching, but start simple and select one.

---

### Post by jackfan00 on 2016-12-08
I encounter the same problem as yours.
my machine is also 16.04 and stuck in login loop

I really expect someone can solve it

---

### Post by spot1984 on 2016-12-20
Update...
I've purged lightdm and ubuntu-desktop and reinstalled them.  No difference.
```

sudo service lightdm stop
sudo apt-get purge lightdm
sudo apt-get purge ubuntu-desktop
sudo shutdown -r now
(reboots, no graphical interface Alt-F1 t get terminal and log in)
sudo apt-get install ubuntu-desktop
sudo apt-get install lightdm
sudo shutdown -r now
(reboots to graphical login screen which still shows my background, shouldn't purge have cleared settings?  Still have login loop)

```

I think it all comes back to Gnome desktop expecting acceleration support, still getting this (excerpt from old log) in syslog:
```

Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: X Error of failed request:  BadValue (integer parameter out of range for operation)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Major opcode of failed request:  155 (GLX)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Minor opcode of failed request:  3 (X_GLXCreateContext)
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Value in failed request:  0x0
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Serial number of failed request:  26
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]:   Current serial number in output stream:  27
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: gnome-session-check-accelerated: Helper exited with code 256
Nov 19 18:44:00 SOLIDServer1 gnome-session-binary[2239]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 19 18:44:00 SOLIDServer1 gnome-session[2239]: gnome-session-binary[2239]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Nov 19 18:44:01 SOLIDServer1 lightdm[994]: ** (lightdm:994): CRITICAL **: session_get_login1_session_id: assertion 'session != NULL' failed

```

Can I configure gnome from the command line?
Can I configure it not to require acceleration?
Can I uninstall and reinstall gnome?  how?

The Linux installation is nicely configured and does what is supposed to be doing, I just don't have a usable desktop, and I don't want to reinstall Linux and have to install and re-configure software. (I shouldn't have to!)

If you know are able, please help.

~Scott

---

### Post by trimmer on 2016-12-21
I was stuck in a loop like this after upgrading to 16.04 LTS but it wasn't a graphics issue.

It was an ecryptfs issue. My home was failing to decrypt and it was fixed easily...

```
tmpfs /dev/shm tmpfs defaults,ro 0 0
```

in my /etc/fstab needed to be changed to

```
tmpfs /dev/shm tmpfs defaults,noexec,nosuid 0 0
```

I'm not sure if this will help you or not but it BUGGED me that something so simple could
be overlooked during the upgrade process.

Hope it's this simple for you.

---

### Post by spot1984 on 2016-12-21
trimmer,

How were you able to tell that was the problem? (what entries in what log?)

I don't have a tempfs entry in fstab.

Scott

---

