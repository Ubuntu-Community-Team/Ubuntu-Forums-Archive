---
title: "Gdm/Xorg Crash After 10.10 Web Upgrade"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by Githlar on 2010-10-30
I've been using Ubuntu since Feisty Fawn, so I've been around the block when it comes to upgrades. From 9.10 to 10.04 I did a clean install, but I decided to try my luck with a web upgrade to 10.10. Well, so far it looks like that was a bad idea.

I can't stay in gdm for more than about 1.5 mins before it crashes and drops me back to the greeter. Honestly, I'm not sure exactly what's crashing, but I'll append what logs I think will give some info.

My system specs:

Dell Inspiron 1525 Laptop
Graphics Card: Intel GM965
(I don't think any more info's really needed here)

And, for the logs (luckily I kept EXT3 and I dual-boot Windows with an EXT driver - though I still hate having to boot into Windows, but Lynx failed me...):

/var/log/Xorg.log
```
[   117.935] 
X.Org X Server 1.9.0
Release Date: 2010-08-20
[   117.936] X Protocol Version 11, Revision 0
[   117.936] Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
[   117.936] Current Operating System: Linux room 2.6.35-23-generic #36-Ubuntu SMP Tue Oct 26 17:03:18 UTC 2010 i686
[   117.936] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-23-generic root=UUID=fc3fdc72-868f-4572-89b6-ace518b01d8e ro splash vga=795 quiet splash
[   117.936] Build Date: 16 September 2010  05:39:22PM
[   117.936] xorg-server 2:1.9.0-0ubuntu7 (For technical support please see http://www.ubuntu.com/support) 
[   117.936] Current version of pixman: 0.18.4
[   117.936] 	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
[   117.936] Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   117.936] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct 30 00:47:23 2010
[   117.936] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   117.936] (==) No Layout section.  Using the first Screen section.
[   117.936] (==) No screen section available. Using defaults.
[   117.936] (**) |-->Screen "Default Screen Section" (0)
[   117.936] (**) |   |-->Monitor "<default monitor>"
[   117.936] (==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.
[   117.936] (==) Automatically adding devices
[   117.937] (==) Automatically enabling devices
[   117.937] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   117.937] 	Entry deleted from font path.
[   117.937] (==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
	built-ins
[   117.937] (==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   117.937] (II) The server relies on udev to provide the list of input devices.
	If no devices become available, reconfigure udev or disable AutoAddDevices.
[   117.937] (II) Loader magic: 0x81f8e00
[   117.937] (II) Module ABI versions:
[   117.937] 	X.Org ANSI C Emulation: 0.4
[   117.937] 	X.Org Video Driver: 8.0
[   117.937] 	X.Org XInput driver : 11.0
[   117.937] 	X.Org Server Extension : 4.0
[   117.939] (--) PCI:*(0:0:2:0) 8086:2a02:1028:022f rev 12, Mem @ 0xfea00000/1048576, 0xe0000000/268435456, I/O @ 0x0000eff8/8
[   117.939] (--) PCI: (0:0:2:1) 8086:2a03:1028:022f rev 12, Mem @ 0xfeb00000/1048576
[   117.939] (II) Open ACPI successful (/var/run/acpid.socket)
[   117.939] (II) LoadModule: "extmod"
[   117.940] (II) Loading /usr/lib/xorg/modules/extensions/libextmod.so
[   117.940] (II) Module extmod: vendor="X.Org Foundation"
[   117.940] 	compiled for 1.9.0, module version = 1.0.0
[   117.940] 	Module class: X.Org Server Extension
[   117.940] 	ABI class: X.Org Server Extension, version 4.0
[   117.940] (II) Loading extension MIT-SCREEN-SAVER
[   117.940] (II) Loading extension XFree86-VidModeExtension
[   117.940] (II) Loading extension XFree86-DGA
[   117.940] (II) Loading extension DPMS
[   117.940] (II) Loading extension XVideo
[   117.940] (II) Loading extension XVideo-MotionCompensation
[   117.940] (II) Loading extension X-Resource
[   117.940] (II) LoadModule: "dbe"
[   117.940] (II) Loading /usr/lib/xorg/modules/extensions/libdbe.so
[   117.940] (II) Module dbe: vendor="X.Org Foundation"
[   117.940] 	compiled for 1.9.0, module version = 1.0.0
[   117.940] 	Module class: X.Org Server Extension
[   117.940] 	ABI class: X.Org Server Extension, version 4.0
[   117.940] (II) Loading extension DOUBLE-BUFFER
[   117.940] (II) LoadModule: "glx"
[   117.941] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   117.941] (II) Module glx: vendor="X.Org Foundation"
[   117.941] 	compiled for 1.9.0, module version = 1.0.0
[   117.941] 	ABI class: X.Org Server Extension, version 4.0
[   117.941] (==) AIGLX enabled
[   117.941] (II) Loading extension GLX
[   117.941] (II) LoadModule: "record"
[   117.941] (II) Loading /usr/lib/xorg/modules/extensions/librecord.so
[   117.941] (II) Module record: vendor="X.Org Foundation"
[   117.941] 	compiled for 1.9.0, module version = 1.13.0
[   117.941] 	Module class: X.Org Server Extension
[   117.941] 	ABI class: X.Org Server Extension, version 4.0
[   117.941] (II) Loading extension RECORD
[   117.941] (II) LoadModule: "dri"
[   117.941] (II) Loading /usr/lib/xorg/modules/extensions/libdri.so
[   117.942] (II) Module dri: vendor="X.Org Foundation"
[   117.942] 	compiled for 1.9.0, module version = 1.0.0
[   117.942] 	ABI class: X.Org Server Extension, version 4.0
[   117.942] (II) Loading extension XFree86-DRI
[   117.942] (II) LoadModule: "dri2"
[   117.942] (II) Loading /usr/lib/xorg/modules/extensions/libdri2.so
[   117.942] (II) Module dri2: vendor="X.Org Foundation"
[   117.942] 	compiled for 1.9.0, module version = 1.2.0
[   117.942] 	ABI class: X.Org Server Extension, version 4.0
[   117.942] (II) Loading extension DRI2
[   117.942] (==) Matched intel as autoconfigured driver 0
[   117.942] (==) Matched vesa as autoconfigured driver 1
[   117.942] (==) Matched fbdev as autoconfigured driver 2
[   117.942] (==) Assigned the driver to the xf86ConfigLayout
[   117.942] (II) LoadModule: "intel"
[   117.942] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   117.943] (II) Module intel: vendor="X.Org Foundation"
[   117.943] 	compiled for 1.9.0, module version = 2.12.0
[   117.943] 	Module class: X.Org Video Driver
[   117.943] 	ABI class: X.Org Video Driver, version 8.0
[   117.943] (II) LoadModule: "vesa"
[   117.943] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   117.943] (II) Module vesa: vendor="X.Org Foundation"
[   117.943] 	compiled for 1.8.99.905, module version = 2.3.0
[   117.943] 	Module class: X.Org Video Driver
[   117.943] 	ABI class: X.Org Video Driver, version 8.0
[   117.943] (II) LoadModule: "fbdev"
[   117.943] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   117.943] (II) Module fbdev: vendor="X.Org Foundation"
[   117.943] 	compiled for 1.8.99.905, module version = 0.4.2
[   117.943] 	ABI class: X.Org Video Driver, version 8.0
[   117.943] (II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
	E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM, Pineview G,
	965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33, GM45,
	4 Series, G45/G43, Q45/Q43, G41, B43, B43, Clarkdale, Arrandale,
	Sandybridge, Sandybridge, Sandybridge, Sandybridge, Sandybridge,
	Sandybridge, Sandybridge
[   117.944] (II) VESA: driver for VESA chipsets: vesa
[   117.944] (II) FBDEV: driver for framebuffer: fbdev
[   117.944] (--) using VT number 8

[   117.949] (WW) Falling back to old probe method for vesa
[   117.949] (WW) Falling back to old probe method for fbdev
[   117.949] (II) Loading sub module "fbdevhw"
[   117.949] (II) LoadModule: "fbdevhw"
[   117.949] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   117.949] (II) Module fbdevhw: vendor="X.Org Foundation"
[   117.949] 	compiled for 1.9.0, module version = 0.0.2
[   117.949] 	ABI class: X.Org Video Driver, version 8.0
[   117.951] drmOpenDevice: node name is /dev/dri/card0
[   117.957] drmOpenDevice: open result is 9, (OK)
[   118.057] drmOpenByBusid: Searching for BusID pci:0000:00:02.0
[   118.057] drmOpenDevice: node name is /dev/dri/card0
[   118.057] drmOpenDevice: open result is 9, (OK)
[   118.057] drmOpenByBusid: drmOpenMinor returns 9
[   118.057] drmOpenByBusid: drmGetBusid reports pci:0000:00:02.0
[   118.057] (II) intel(0): Creating default Display subsection in Screen section
	"Default Screen Section" for depth/fbbpp 24/32
[   118.057] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[   118.057] (==) intel(0): RGB weight 888
[   118.057] (==) intel(0): Default visual is TrueColor
[   118.058] (II) intel(0): Integrated Graphics Chipset: Intel(R) 965GM
[   118.058] (--) intel(0): Chipset: "965GM"
[   118.058] (==) intel(0): video overlay key set to 0x101fe
[   118.076] (II) intel(0): Output VGA1 has no monitor section
[   118.076] (II) intel(0): Output LVDS1 has no monitor section
[   118.076] (II) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[   118.206] (II) intel(0): Output DVI1 has no monitor section

```

/var/log/gdm/:0-greeter.log
```
** (process:2274): DEBUG: Greeter session pid=2274 display=:0.0 xauthority=/var/run/gdm/auth-for-gdm-L2SRqJ/database
gdm-simple-greeter[2274]: Gtk-WARNING: /build/buildd/gtk+2.0-2.22.0/gtk/gtkwidget.c:5684: widget not within a GtkWindow
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.
Window manager warning: Buggy client sent a _NET_ACTIVE_WINDOW message with a timestamp of 0 for 0x1c00034 (Login Wind)
Window manager warning: meta_window_activate called by a pager with a 0 timestamp; the pager needs to be fixed.

(gnome-power-manager:2275): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Window manager warning: CurrentTime used to choose focus window; focus window may not be correct.
Window manager warning: Got a request to focus the no_focus_window with a timestamp of 0.  This shouldn't happen!

** (gnome-settings-daemon:2176): WARNING **: Failed to send buffer
```

The :0-greeter.log looks pretty ominous, but I'm not quite sure what to make of it.

Also I get an error mentioning something similar to FBIOPUTCMAP on VTerm 1 (Ctrl+Alt+F1)

I think I read somewhere that disabling compositing may fix it (but this was for Kubuntu and a different Intel chipset), however I can't remember how to do that - but why should I have to if it worked fine in Lucid? I tried using `metacity --replace` at startup, but a crash still occurred, so It's not necessarily a Compiz-specific issue.

---

### Post by Githlar on 2010-10-30
Can nobody help me with this issue?

---

### Post by Githlar on 2010-10-30
I managed to fix this HUGE annoyance - after crashing dpkg and some other difficulties.

Here's how (Note: if you are experiencing this problem, do this from a Virtual Console [e.g. Ctrl+Alt+F1] - you don't have to be logged in to Gnome Desktop Manager - to avoid pains that I suffered as mentioned above):

```
sudo apt-get purge ubuntu-desktop gdm gdm-guest-session xorg xserver-xorg-video-intel xserver-xorg-video-all
```
```
sudo apt-get install ubuntu-desktop gdm gdm-guest-session xorg xserver-xorg-video-intel xserver-xorg-video-all
```

It seems to be working fine so far - it hasn't crashed in about 20 mins, so I think I'm good.

---

### Post by lemoirl on 2010-11-09
The steps described above fixed the problem for me but I later discovered what the actual problem was. After the purge/reinstall, the x11vnc instance that I run right at the end of /etc/gdm/Init/Default was gone so I put it back in. Bingo! gdm started crashing again.

So, x11vnc running from the gdm init might be the real problem, at least for some people. I then found this thread:

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1612704&page=2](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1612704&page=2)

In summary, adding -noxrecord to x11vnc options seems to solve the problem. It disables a speedup option.

---

