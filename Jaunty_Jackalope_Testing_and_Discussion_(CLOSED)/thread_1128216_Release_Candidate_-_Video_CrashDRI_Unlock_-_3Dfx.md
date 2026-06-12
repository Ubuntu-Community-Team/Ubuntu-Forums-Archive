---
title: "Release Candidate - Video Crash/DRI Unlock - 3Dfx"
date: 2009-04-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by secdroid on 2009-04-17
Installed Jaunty i386 RC with command line install from alternate install CD.  After installing base system, updated/upgraded,  installed Xorg, LXDE, and Firefox.  Same system runs Intrepid/LXDE, Arch, SliTaz and other distros fine.

Symptom: Full screen apps (Firefox and Leafpad) crash easily and quickly, bouncing user out to GDM login screen.  Xterm shells and vi sessions seem more stable; no crashes in limited testing.  No /var/crash.

I'd appreciate any suggestions on how to troubleshoot this.  (Other than get newer hardware!)  ;)

From lspci -
01:00.0 VGA compatible controller: 3Dfx Interactive, Inc. Voodoo Banshee (rev 03)

Note _possibly_ related error -- _[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-tdfx/+bug/214439](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-tdfx/+bug/214439)_

Excerpt from Xorg.0.log -- 
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(==) Matched tdfx for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) Loading /usr/lib/xorg/modules/drivers//tdfx_drv.so
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 5.0
(II) TDFX: Driver for 3dfx Banshee/Voodoo3 chipsets: 3dfx Banshee,
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
	ABI class: X.Org Video Driver, version 5.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
	Driver provided NonTEGlyphRenderer replacement
(II) TDFX(0): [DRI] installation complete
(II) AIGLX: Screen 0 is not DRI2 capable
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: node name is /dev/dri/card0
(II) AIGLX: Loaded and initialized /usr/lib/dri/tdfx_dri.so
(II) GLX: Initialized DRI GL provider for screen 0
**(EE) TDFX(0): DRIUnlock called when not locked.**
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0

---

### Post by secdroid on 2009-04-17
I copied the Ubuntu Jaunty/LXDE xorg.conf that I had created (resolution issues) from Jaunty to Arch Linux 2009.02/LXDE and started X on the same hardware, using the Jaunty xorg.conf.  No problems with fullscreen apps.  This is being posted from Midori in Arch.  Extremely stable, something Midori was _not_ under Ubuntu Intrepid.

Note: Arch has the same (EE) X error that Ubutu had -- **(EE) TDFX(0): DRIUnlock called when not locked.**  The (EE) DRIUnlock error is apparently not important in Ubuntu Jaunty stability problem.

This would appear to rule out most Xorg configuration issues.  Therefore, it would appear that there is a 3Dfx driver issue in the Ubuntu Jaunty Xorg that is not present in the Arch 2009.02 Xorg or the many other distros that work well on this box, including Intrepid/LXDE/Firefox.

My impression is that Ubuntu is not the distro to use for old or unusual hardware.  Ubuntu provides lots of new features, particularly Gnome applets like notification.  Hardware support/detection, particularly for older hardware, is not an Ubuntu strength.

---

