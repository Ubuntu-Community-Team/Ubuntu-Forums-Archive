---
title: "gutsy cant run anything requiring direct rendering with ATI."
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by sdowney717 on 2007-10-18
ok, It used to have direct rendering yes.
I did upgrade to gutsy and I tried both envy and just selecting the restricted drivers.

So, do I need a new video card?


scott@scott-desktop:~$ glxinfo 
name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 1.2 (2.0.6747 (8.40.4))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon
scott@scott-desktop:~$

---

### Post by Antman on 2007-10-18
I have an ATI X1300 on my laptop and direct rendering works fine in Gutsy. I don't use Envy just the restricted driver module built into Gutsy.

---

### Post by sdowney717 on 2007-10-18
well then, I suppose my ATI 9600 card is to old for gutsy.

Since I did not do anything special to my system, then everyone else who has an ATI 9600 card must be experiencing the same problem.

---

### Post by BorjaRRR on 2007-10-19
I have an ati mobility x1600 and the same problem (no direct rendering) with the restricted driver module

---

### Post by beefbowel on 2007-10-20
every time i upgrade i find myself spending two to three days trying to get direct rendering.  i have r200 9100 and it worked fine in feisty.  now, i can't even scroll down web pages without it being a pita.

---

### Post by kozmoracer on 2007-10-21
I'm having the same problem too.

I'm running gusty on a radeon x1600pro.

 installed the drivers using envy today and direct rendering works - to my amazement.
However, when I tried to turn on desktop effects I was told that the composite extension was missing. I was able to fix that in the xorg config file but then I was simply told that desktop effects can not be loaded.

So... back to the xserver installation and of course - I also receive:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

At least desktop effects are working for me... I thought the x1xxx's were unsupported.

Ideas.. anyone

---

### Post by bluedragon436 on 2007-10-21
I have a Dell D610 with an ATI Radeon 300 and have had some issue with the rendering as well.. my desktop eye candy and stuff works just fine.  I have tried with the restricted drivers both running and not running and no difference.  Another problem I am having is my screensaver does not work, when it comes time for it to kick in the screen just flickers and goes back to the normal dekstop screen.

---

### Post by wpshooter on 2007-10-21
> **sdowney717 said:**
> well then, I suppose my ATI 9600 card is to old for gutsy.

Since I did not do anything special to my system, then everyone else who has an ATI 9600 card must be experiencing the same problem.

Same here.  No direct rendering with my ATI Radeon 9600.  Tried both Ubuntu restricted driver install and also ENVY and no dice.  FPS is a snails pace compared to what I got under Feisty.

What in the blue blazes does this mean (couldn't they be a bit more cryptic) ?

**direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**

Thanks.

---

### Post by [eXr] on 2007-10-22
Same problem with ATI Radeon M6 Mobility, with ati & radeon xorg drivers.

direct rendering: No (...

---

### Post by kozmoracer on 2007-10-25
Ok... Here is what I have learnt...
There is currently no point in using Envy to install your drivers if you want to get desktop effects working (On ATI cards)!
Why you ask?
Envy installs the AIGLX drivers, which do not currently support running desktop effects/compiz. They do however turn direct rendering ON (on my x1600 atleast).
From the little knowledge I have -  I believe that there is a new release of the AIGLX driver every month (providing the developers stay on schedule). Apparently the next release of the driver WILL support compiz/desktop effects.

So there a two options if you want desktop effects - wait for the next release of the AIGLX driver or use the XGL drivers.

I am currently using the XGL drivers and don't have direct rendering. Compiz seems to work.. okishly.

Now, XGL turns my direct rendering off, and why? Sorry, I dont have the answer to that yet - but I'm searching.

Please don't draw any conclusions from what I have written in the above text until some one who is experienced enough can verify if what I've said is correct or incorrect.

sdowney717, what I suggest you do if you want direct rendering is use envy to install the drivers again, and then we can do some trouble shooting from there.
OR
If you want your eye candy - install the XGL drivers.

Here's a few handy commands...

To install XGL: ```
sudo apt-get install xserver-xgl
```

To check if you have direct rendering:```
glxinfo | grep "direct rendering"
```
(My result is currently:
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
:confused:

And if you change a setting you shouldn't have and need reconfigure XGL:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Callius on 2007-10-26
I'm experiencing this error as well.  I've tried *multiple* different ATI drivers, but none of them seem to allow Direct Rendering with my 9600.

Is there ANYONE out there that has a 9600 that is working correctly?  If so, would you mind posting your xorg.conf and some information about how you got it working?

---

### Post by enchesss on 2007-10-26
I have both types of radeon ati

An agp 9600pro

and a pcie HD 2600pro

the agp works with 7.04 after installing drivers using internal vga then plugin in the card - huge mission but it worked about 6 months ago after last release and still work (see below).

my new computer with the pcie HD 9600 pro is another story of woes however.

no drivers have been able to work using any installation method.

now the agp 9600 pro locks up at the login screen with gutsy. I can still boot to 2nd HD using 7.04 though.

have tried to edit menu.lst  with every type of alternate boot edit but nothing works.

Does anyone know how to change the kernel to use previous drivers that worked with 7.04?

Just can not get gutsy to work on either card though the fresh installation seems to go much better until first boot when both cards and both computers lock up.

the pcie HD 2600 pro locks up about 2 bars into splash with gutsy with caps and scroll lock lights flashing (and reboots itself with fiesty at this point).

the agp 9600 pro locks up at the login of gutsy with the mouse (usb corless) still working but unable to open options or enter a cursor into login text box.

windows still works - have done a fresh installation after unsuccessful gutsy. why does windows work? - it is just not fair!!

- i want ubuntu back on my computer - please help

---

### Post by stueyboy on 2007-10-26
I've got a radeon 9600 and for the brief period I was running gutsy on my system, the built in restricted driver thing worked OK. I've now gone back to 7.04 for multiple reasons but basically wanted a stable system.

enchess - can you not just boot into safe mode and edit your xorg.conf to use the standard "ati" driver? I have done that in the past and it got my ssytem back up.

Also, I have noticed with the Envy script that when it auto configures xorg.conf it does a terrible job at guessing my refresh rate and Vsynch values for my LCD monitor and when I sort that out the drivers work much better.

Hope some of that helps

---

### Post by enchesss on 2007-10-26
Woo hoo

Have just down loaded the 64 bit iso for amd and installed on agp 9600 pro

installation and everything went smooth as possible - could not be happier seriously.

guess i have to count my lucky stars!!

i have even been able to run envy after rebooting and updating and i now have restricted drivers working.

hope this is stable becuase i am able to use my system pretty well now.


considering all the problems the HD 2600 still has anyway - it does not like this iso at all - it reboots itself on both live and safe mode..

the alternate disk gets the installation going much better on the hd 2600 but it still locks up on boot.


on to the hd 2600 now

i think i will hassle ati because apparently ubuntu are not able to use the restricted drivers.

maybe this is why windoze works. becuase they are able to use restricted drivers for installation.??

thanks for your help.

---

### Post by sdowney717 on 2007-10-26
I use an ATI 9600 with 64mb and it works well.

[http://ubuntuforums.org/showthread.php?t=589637](http://ubuntuforums.org/showthread.php?t=589637)

follow this guide for the new ATI driver that does do rendering with compiz and no xgl installed.

It is worth it to get this going. This driver I think will get even better.
The catalyst control center is a pain.

---

### Post by TheBigBentley on 2007-10-27
I have this same problem with my ATI 9800 Pro. Arent upgrades supposed to fix things not break them? How could they manage to cut off an entire group of users in one foul swoop? Im gonna wait a while before i go trying to reinstall any new video drivers again.

---

### Post by Creazine on 2007-10-28
> **wpshooter said:**
> Same here.  No direct rendering with my ATI Radeon 9600.  Tried both Ubuntu restricted driver install and also ENVY and no dice.  FPS is a snails pace compared to what I got under Feisty.

What in the blue blazes does this mean (couldn't they be a bit more cryptic) ?

**direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)**

Thanks.

> sudo apt-get remove xserver-xgl
It helps you.

---

### Post by Doomguy0505 on 2007-10-29
Thank you! After removing xserver-xgl, the hardware acceleration worked without blacking out gdm.

---

### Post by Agroth on 2008-02-07
hi all,

I have the exact same problem but I managed to get it working when I removed the xserver-xgl.
I have had compiz working fine previously but that stopped working now, the good thing is that I finally get a corrupt outpot from the fglrxinfo command;
```

$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.0.6473 (8.37.6)

```
Here is my xorg.conf if anyone is interested in it, took me quite some time to get it working hehe...

```


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"se"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Radeon Mobility 9600"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-67
	VertRefresh	50-75
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Radeon Mobility 9600"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection


```

---

