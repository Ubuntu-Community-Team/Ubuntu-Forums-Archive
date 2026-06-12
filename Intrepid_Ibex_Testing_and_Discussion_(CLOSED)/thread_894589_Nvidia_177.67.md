---
title: "Nvidia 177.67"
date: 2008-08-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pferraro on 2008-08-19
New NVIDIA beta was released today and promises significant fixes.
[http://www.nvidia.com/object/linux_display_amd64_177.67.html]("http://www.nvidia.com/object/linux_display_amd64_177.67.html")

Release Date: August 19, 2008
Release Highlights
    * Added support for the following new GPUs:
          o GeForce GTX 260
          o GeForce GTX 280
    * Improved support for RENDER masks, as well as RENDER repeating modes and transformations, for video memory pixmaps.
    * Added accelerated support for RENDER convolution filters for video memory pixmaps on GeForce 8, 9 and GTX GPUs.
    * Added an 'AllowSHMPixmaps' X configuration option, which can be used to prevent applications from using shared memory pixmaps; the latter may cause some optimizations in the NVIDIA X driver to be disabled.
    * Added support for DisplayPort display devices (including 30-bit devices).
    * Resolved various stability problems on GeForce 8, 9 and GTX GPUs, as well as some GeForce 6 and 7 PCI-E GPUs.
    * Fixed a bug that resulted in GPU errors when changing the TwinView display configuration while using Compiz.
    * Further improved the error recovery paths taken in case of GPU command stream corruption.
    * Removed an old workaround that caused incorrect fake Xinerama information to be reported after enabling a second TwinView display.
    * Fixed the subpicture component order reported by the NVIDIA X driver's XvMC implementation.
    * Fixed a problem that could result in IRQs being disabled on some multi-GPU SMP configurations.
    * Worked around cache flushing problems (on some Linux kernels) that caused corruption and stability problems.
    * Added experimental support for PCI-E MSI.
    * Improved compatibility with recent Linux 2.6 kernels.

---

### Post by plun on 2008-08-19
Phoronix article

[http://www.phoronix.com/scan.php?page=article&item=nvidia_17767&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17767&num=1)

------
This one is maybe also important

**If you have a performance problem, PLEASE read this first**

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

------

The RGBA challenge seems nearly to be fixed...just minor errors.

---

### Post by Nullack on 2008-08-19
Yes Im pleased to say when I spoke with tseliot he's working away on the necessary development for us to test :)

---

### Post by Cimi86 on 2008-08-20
> **plun said:**
> Phoronix article

[http://www.phoronix.com/scan.php?page=article&item=nvidia_17767&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_17767&num=1)

------
This one is maybe also important

**If you have a performance problem, PLEASE read this first**

[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

------

The RGBA challenge seems nearly to be fixed...just minor errors.
I haven't tested with my murrine yet... are the glitches fixed?

---

### Post by plun on 2008-08-20
> **Cimi86 said:**
> I haven't tested with my murrine yet... are the glitches fixed?

Yup...but...

This thread is important
[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

With my 7600GS card it become a little "sluggish" and I am only using
this for the moment

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 
```

[URL="http://ubuntuforums.org/showthread.php?t=833633"]
Amaranths patch[/URL] still works but hopefully this driver soon will be available for Intrepid.

Tested with Screenlets-manager and CCSM, also with the sphere and the wallpaper plugin with Nautilus desktop off (gconf-editor)...

---

### Post by Cimi86 on 2008-08-20
> **plun said:**
> Yup...but...

This thread is important
[http://www.nvnews.net/vbulletin/showthread.php?t=118088](http://www.nvnews.net/vbulletin/showthread.php?t=118088)

With my 7600GS card it become a little "sluggish" and I am only using
this for the moment

```
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1 
```

[URL="http://ubuntuforums.org/showthread.php?t=833633"]
Amaranths patch[/URL] still works but hopefully this driver soon will be available for Intrepid.

Tested with Screenlets-manager and CCSM, also with the sphere and the wallpaper plugin with Nautilus desktop off (gconf-editor)...

Not fixed yet with RGBA, thunar is still bugged, unless you enable initialpixmapplacement, which fixes the problem

---

### Post by plun on 2008-08-21
177.68 is out.... bug fixes

[http://www.nvnews.net/vbulletin/showthread.php?t=118244](http://www.nvnews.net/vbulletin/showthread.php?t=118244)

ping Alberto ?  :)

---

### Post by Cimi86 on 2008-08-21
I'm creating the debs

EDIT: [http://www.cimitan.com/ubuntu](http://www.cimitan.com/ubuntu)

---

### Post by temcat on 2008-08-22
Does anybody know if this release fixes the problems with the inability to set display brightness with laptop keys as for example seen on Samsung Q70?

---

### Post by plun on 2008-08-22
> **Cimi86 said:**
> I'm creating the debs

EDIT: [http://www.cimitan.com/ubuntu](http://www.cimitan.com/ubuntu)

You are also coding again....:grin:

Rev 38....

BluProfondo is magic now....!

Thanks !

---

### Post by RIchard James13 on 2008-08-22
I noticed that 177.68 is now in the repository.

---

### Post by Wild-Storm on 2008-08-23
still no gtx 260 support? (doesnt work here - ubuntu 64bit)

edit:// sorry, had to reboot. works now

---

### Post by plun on 2008-08-28
ver 177.70 is out...

[http://www.nvnews.net/vbulletin/showthread.php?t=118602](http://www.nvnews.net/vbulletin/showthread.php?t=118602)

>     *  Added support for the following new GPUs:
          o GeForce 9800 GTX+
          o GeForce 9800 GT
          o GeForce 8100P
          o nForce 780a SLI
          o nForce 750a SLI
          o Quadro FX 770M
          o Quadro NVS 160M
          o Quadro NVS 150M
    * Improved support for RENDER operations with the same source
      and destination; this should enhance performance in
      some situations, e.g. when dragging Plasma applets in KDE4.
    * Fixed a text rendering performance regression that affected
      GeForce 6 and 7 series GPUs.
    * Fixed a regression that caused text to be missing or
      corrupt on GeForce 6 and 7 series GPUs.
    * Fixed a regression responsible for false negatives during
      SLI video bridge detection attempts after X server
      restarts.
    * Fixed a bug that resulted in AGP FW/SBA settings and overrides
      being applied incorrectly when using the Linux kernel's
      AGP GART driver.
    * Fixed a bug that caused initialization of the builtin AGP
      GART driver (NvAGP) to fail.


RGBA seems to be fixed again...  ver 68 trashed icons and text.

---

### Post by Cimi86 on 2008-08-28
Uploading 177.70 debs for hardy in the same place...
These drivers are working great, just a minor bug with compiz

---

### Post by plun on 2008-08-28
> **Cimi86 said:**
> 
These drivers are working great, just a minor bug with compiz

Yup...  OT maybe...

What is the plan for the murrine-configurator  ?   :)

Checked Launchpad... O:) The Murrine svn engine is working great, Thanks !

---

### Post by Technoviking on 2008-08-28
Anyone else experience weird re-draw issues in gnome-terminal with the 177.x drivers. Also major slowness using cairo-dock or google gadgets.

---

### Post by Technoviking on 2008-08-28
> **Cimi86 said:**
> I'm creating the debs

EDIT: [http://www.cimitan.com/ubuntu](http://www.cimitan.com/ubuntu)
How do you use your debs with envy?

---

### Post by plun on 2008-08-28
> **Mike said:**
> Anyone else experience weird re-draw issues in gnome-terminal with the 177.x drivers. Also major slowness using cairo-dock or google gadgets.

Version 177.68 was terrible, especially with RGBA enabled. 

Alberto M is working with ver 177.70 which is probably coming tomorrow as I understands it. (or download driver from nVidia)

---

