---
title: "ati / radeon driver not working with Desktop Effects"
date: 2008-06-30
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eeclark on 2008-06-30
```

edward@smallville:~$ lsmod | grep radeon
radeon                136352  2 
drm                    84264  3 radeon
edward@smallville:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
edward@smallville:~$ glxinfo | grep direct
direct rendering: Yes
edward@smallville:~$ 

```
Card is ATI 9600.

Any ideas?

---

### Post by cantas on 2008-06-30
My computer, with a RS480 and the new DRM/DRI and radeon OSS, hangs when enabling Desktop Effects. It used to work on Hardy and Intrepid until three weeks ago.
Now I can not use compiz anymore.

Ste

---

### Post by eeclark on 2008-07-01
> **cantas said:**
> My computer, with a RS480 and the new DRM/DRI and radeon OSS, hangs when enabling Desktop Effects. It used to work on Hardy and Intrepid until three weeks ago.
Now I can not use compiz anymore.

Ste

I have been trying for days to get compiz working again.
I have not had any success.

Does anyone know what log to look at to see what is going on when setting Desktop Effects fails from within Gnome?

I also followed the information at [http://wiki.compiz-fusion.org/Setup#head-e3decc7a7a2602bf60667249efa94b7c01a5eee7](http://wiki.compiz-fusion.org/Setup#head-e3decc7a7a2602bf60667249efa94b7c01a5eee7) 

I checked the Xorg.0.log file:
```

edward@smallville:~$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): LVDS Info:
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(WW) RADEON(0): Failed to determine num pipes from DRM, falling back to manual look-up!
(WW) RADEON(0): Option "XAANoOffscreenPixmaps" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
edward@smallville:~$ 

```

Thanks

---

### Post by olskar on 2008-07-01
> **eeclark said:**
> I have been trying for days to get compiz working again.
I have not had any success.

Does anyone know what log to look at to see what is going on when setting Desktop Effects fails from within Gnome?

I also followed the information at [http://wiki.compiz-fusion.org/Setup#head-e3decc7a7a2602bf60667249efa94b7c01a5eee7](http://wiki.compiz-fusion.org/Setup#head-e3decc7a7a2602bf60667249efa94b7c01a5eee7) 

I checked the Xorg.0.log file:
```

edward@smallville:~$ cat /var/log/Xorg.0.log | grep WW
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) RADEON(0): LCD DDC Info Table found!
(WW) RADEON(0): LVDS Info:
(WW) RADEON(0): DRI init changed memory map, adjusting ...
(WW) RADEON(0):   MC_FB_LOCATION  was: 0xd7ffd000 is: 0xd7ffd000
(WW) RADEON(0):   MC_AGP_LOCATION was: 0xffffffc0 is: 0xe07fe000
(WW) RADEON(0): Failed to determine num pipes from DRM, falling back to manual look-up!
(WW) RADEON(0): Option "XAANoOffscreenPixmaps" is not used
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
edward@smallville:~$ 

```

Thanks

What is output from running "compiz --replace" in terminal? (Same as activating desktop effects)

---

### Post by eeclark on 2008-07-01
> **olskar said:**
> What is output from running "compiz --replace" in terminal? (Same as activating desktop effects)

```

edward@smallville:~$ compiz --replace
Checking for Xgl: not present. 
Found laptop using ati driver. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by RAOF on 2008-07-01
Well, that seems fairly self-explainatory.  Has compiz *ever* worked on this system?  If so, when?

If it worked in Hardy but fails with that message in Intrepid (and you *aren't* using a laptop) it would seem that the laptop-detect code has been broken.

Compiz is blacklisted on laptop ATI cards because of hard to pin down driver bugs.  That may be revisited with new drivers.

You can bypass the blacklist with instructions [here](http://ubuntuforums.org/showthread.php?t=765875).  If it breaks/freezes/causes your laptop to combust you get to keep any pieces not on fire.

---

### Post by eeclark on 2008-07-01
> **RAOF said:**
> Well, that seems fairly self-explainatory.  Has compiz *ever* worked on this system?  If so, when?

If it worked in Hardy but fails with that message in Intrepid (and you *aren't* using a laptop) it would seem that the laptop-detect code has been broken.

Compiz is blacklisted on laptop ATI cards because of hard to pin down driver bugs.  That may be revisited with new drivers.

You can bypass the blacklist with instructions [here](http://ubuntuforums.org/showthread.php?t=765875).  If it breaks/freezes/causes your laptop to combust you get to keep any pieces not on fire.

Yes it has been working up until a few days ago.
Stopped after a dist-upgrade.

Worked with fglrx and with ati driver.

Will try blacklist...never had to in the past though.

EDIT:  That worked
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```

Thanks

---

### Post by RAOF on 2008-07-01
And is this a laptop?  The blacklist was only for the ati, not fglrx, driver on laptops.

---

### Post by eeclark on 2008-07-02
> **RAOF said:**
> And is this a laptop?  The blacklist was only for the ati, not fglrx, driver on laptops.


Yes this is a laptop.
No, not running fglrx.  Running the opensource ATI driver.
Thanks again.
Runs great by-the-way.

---

### Post by eeclark on 2008-07-06
It was working up until a few days ago.
Now I get the white screen.

---

### Post by spamzilla on 2008-07-06
Desktop Effects worked fine for me until a few days ago too and now I get the white screen on bootup. Disabling compiz in failsafe solved the problem...just gotta wait for compiz/drivers to be fixed. (intel x3100 965 chipset)

[http://ubuntuforums.org/showthread.php?t=850142](http://ubuntuforums.org/showthread.php?t=850142)

---

### Post by eeclark on 2008-07-06
Looks like a new version of xserver-xorg-core is coming soon (built on July 4).

```

Format: 1.8
Date: Fri, 04 Jul 2008 13:39:34 +0300
Source: xorg-server
Binary: xserver-xorg-core xserver-xorg-dev xdmx xdmx-tools xnest xvfb xserver-xephyr xserver-xfbdev xserver-xorg-core-dbg
Architecture: i386
Version: 2:1.4.99.905-0ubuntu1
Distribution: intrepid
Urgency: low
Maintainer: Ubuntu/i386 Build Daemon <buildd@vernadsky.buildd>
Changed-By: Timo Aaltonen <tepsipakki@ubuntu.com>
Description: 
 xdmx       - distributed multihead X server
 xdmx-tools - Distributed Multihead X tools
 xnest      - Nested X server
 xserver-xephyr - nested X server
 xserver-xfbdev - Linux framebuffer device tiny X server
 xserver-xorg-core - Xorg X server - core server
 xserver-xorg-core-dbg - Xorg - the X.Org X server (debugging symbols)
 xserver-xorg-dev - Xorg X server - development files
 xvfb       - Virtual Framebuffer 'fake' X server
Changes: 
 xorg-server (2:1.4.99.905-0ubuntu1) intrepid; urgency=low
 .
   * Merge with Debian experimental, remaining changes:
   * debian/control:
     - Change maintainer address.
     - xvfb Depends on xauth, xfonts-base.
   * debian/patches:
     - 100_xserver_exa_force_greedy.patch
       Provide a mechanism for drivers to force greedy mode on.
     - 101_fedora_xserver-1.3.0-document-fontpath-correctly.patch
       Fixes document fontpaths shown in the man page.
     - 102_ubuntu_sharevts_load_cpu.patch
       Close console fd only when using --sharevts.
     - 104_psb_auto.patch
       Add automatic detection of Poulsbo hardware when running without a
       Device definition.
     - 107_fedora_dont_backfill_bg_none.patch
       Disable backfilling of windows created with bg=none, which
       would otherwise force a framebuffer readback.
     - 110_fedora_no_move_damage.patch
       Disable damage notifications on move for manually redirected windows.
     - 120_fedora_xserver-xaa-evict-pixmaps.patch
       A hack to evict XAA pixmaps and disable the pixmap cache when the first
       texture is bound.
     - 121_only_switch_vt_when_active.diff
       Add a check to prevent the X server from changing the VT when
       killing GDM from the console.
     - 123_no_composite_for_xvfb_run.patch
       Use "-extension Composite" to fix xvfb-run crashing.
   * Cleaned up patches:
     - upstream, either directly or otherwise implemented:
       103_fedora_openchrome.patch, 105_reduce_wakeups_from_smart_scheduler.diff
       108_fedora_honor_displaysize.patch, 109_glx_fail_if_no_texture_bound.diff
       144_fedora_xserver-1.3.0-xnest-exposures.patch,
       146_X86EMU-added-blacklist-for-I-O-port-in-0-0xFF-range.patch,
       147_X86EMU-pass-the-correct-bus-dev-fn-tag-to-pci-emula.patch,
       148_dix_touchscreen_fixes.diff,
       149_add_quirks_for_physical_screen_size_issues.patch,
       150_edid_quirk_lp154w01.patch, 151_x86emu_handle_cpuid.patch,
       153_exa_skip_empty_glyphs.diff, 154_fix_rotation_for_multimon.diff,
       155_exa_fix_off-by-one.diff, 156_resize_composite_overlay.diff,
       157_fix_exa_pixmap_width.diff, 158_xkb_wrapping.diff,
       159_xkb_default_to_null.diff, 160_default_to_intel.diff,
       161_fix_big_endian_cursor.diff, 162_cve-2007-6429.diff,
       163_fix_untrusted_access.diff, 164_fix_context_sharing.diff,
       165_fedora_xserver-1.5.0-xaa-option-inversion.patch,
       166_fix_lpl_monitors.diff, 167_xf86AutoConfig_geode_addition.diff,
       168_closedir.patch,
       170_xorg-xserver-1.4-cve-2008-1377.diff,
       171_xorg-xserver-1.4-cve-2008-1379.diff,
       172_xorg-xserver-1.4-cve-2008-2360.diff,
       173_xorg-xserver-1.4-cve-2008-2361.diff,
       174_xorg-xserver-1.4-cve-2008-2362.diff
     - obsolete:
       101_fedora-apm-typedefs.patch
       104_fedora_init_origins_fix.patch
       142_fedora_xserver-1.3.0-no-pseudocolor-composite.patch
       169_xf86AutoConfig_choose_default_driver_if_no_pci.patch
     - unnecessary:
       106_ubuntu_fpic_libxf86config.patch (the lib is not shipped)


```

---

### Post by eeclark on 2008-07-07
new xserver-xorg-core is out, but need to wait for xorg to be updated before we can upgrade core.

---

### Post by psyke83 on 2008-07-08
> **eeclark said:**
> new xserver-xorg-core is out, but need to wait for xorg to be updated before we can upgrade core.

A quick heads-up for anyone still interested in this topic. Today most of the xserver packages/drivers etc have been uploaded, but Desktop Effects still won't work correctly after you upgrade - you'll see a white screen.

Open a terminal and run the following:
```
$ LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

Compiz should work correctly using that method. This issue will probably get fixed in Mesa soon, so don't worry. Since it's a Mesa issue, it probably affects all Xorg drivers; I'm using an Intel 855GM.

---

### Post by eeclark on 2008-07-08
It is working for me.
Had to do the following:
```

mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

```

---

### Post by illi11 on 2008-07-08
i also have gotten some weird stuff happening as of a day or 2 ago. i have to use none for visual effects if i dont i cannot visably see the bottom 1/10th of the screen no matter what resolution i put it on. the buttons are there and everything i just cannot see them and it irks me.

---

### Post by Rocket2DMn on 2008-07-08
I am also getting the white screen using the SKIP_CHECKS=yes.  Update-Manager won't download the newest xorg drivers or core yet.
"LIBGL_ALWAYS_INDIRECT=1 compiz --replace" did not work either.

---

### Post by Mazza558 on 2008-07-08
Do the newest Xorg drivers have a changelog yet? What new stuff have they got?

---

### Post by BwackNinja on 2008-07-08
With the white screen issue, enable intrepid-proposed and go to synaptic, select all updates at once (you have to do it all at once or it'll complain) and mark to upgrade. That's how I got mine to work.

I don't quite see any point in not having intrepid-proposed enabled, considering the fact that you are using an OS that you should know isn't exactly stable anyway.

---

### Post by Amaranth on 2008-07-08
You know there aren't actually any packages in intrepid-proposed, right? That is used for testing SRU packages after release.

---

### Post by BwackNinja on 2008-07-08
I just enabled every update repo and was able to do everything then. I just assummed it would have been intrepid-proposed that did that. Either way, it worked for me at least.

---

