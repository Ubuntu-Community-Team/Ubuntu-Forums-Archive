---
title: "mesa haunting me"
date: 2005-03-30
forum: Installation &amp; Upgrades
---

### Post by teumima on 2005-03-30
E: /var/cache/apt/archives/xlibmesa-gl_6.8.2-8_i386.deb:  trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0

How do I stop that? i dont' want mesa to overwrite my fglrx, but i want it to go away. I want mesa to go away :(

---

### Post by Dracontopes on 2005-03-30
Assuming you are using the drivers from ATI.com, here goes:

1. Shut down X: *sudo /etc/init.d/gdm stop*
2. Remove fglrx module: *sudo modprobe -r fglrx*
3. Remove fglrx package: *sudo apt-get remove fglrx-6-8-0*
4. Update xlibmesa-gl: *sudo apt-get install xlibmesa-gl*
5. Re-install the fglrx package: *sudo dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb*
6. Build modules: *cd /lib/modules/fglrx/build_mod* , and then, *sudo sh make.sh*
7. Build modules #2: *cd ..* (back to /lib/modules/fglrx) , and then, *sudo sh make_install.sh*

This is like, that HARD way :P Oh and there may be error here, doing this from memory.

I think xlibmesa-gl is needed by xorg, so just not installing is not an option I **think** (or you can just not do the updates)... Maybe I will write a script that will do the things above automatically...

---

### Post by teumima on 2005-03-31
[QUOTE=Dracontopes]Assuming you are using the drivers from ATI.com, here goes:

1. Shut down X: *sudo /etc/init.d/gdm stop*
2. Remove fglrx module: *sudo modprobe -r fglrx*
3. Remove fglrx package: *sudo apt-get remove fglrx-6-8-0*
4. Update xlibmesa-gl: *sudo apt-get install xlibmesa-gl*
5. Re-install the fglrx package: *sudo dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb*
6. Build modules: *cd /lib/modules/fglrx/build_mod* , and then, *sudo sh make.sh*
7. Build modules #2: *cd ..* (back to /lib/modules/fglrx) , and then, *sudo sh make_install.sh*

This is like, that HARD way :P Oh and there may be error here, doing this from memory.

I think xlibmesa-gl is needed by xorg, so just not installing is not an option I **think** (or you can just not do the updates)... Maybe I will write a script that will do the things above automatically...[/QUOTE]
 Man that is the only way? I really dont want to mess around with amy ati now that its finally working.

---

### Post by Dracontopes on 2005-03-31
Hmm well the only thing that will happen is that the fglrx module will be temporarily be removed and then reinstalled. Nothing will happen to your xorg.conf etc :)

---

### Post by teumima on 2005-03-31
[QUOTE=Dracontopes]Hmm well the only thing that will happen is that the fglrx module will be temporarily be removed and then reinstalled. Nothing will happen to your xorg.conf etc :)[/QUOTE]
 hey man

not to question ur credibility. U tried this and it worked? It took me months to sort out my ati driver and i'd really miss it.

---

### Post by alastair on 2005-03-31
I understand your reluctance to play around with the ATI setup. Anyone who's had to set up fglrx drivers knows the pain involved sometimes.

So ... alternatively, assuming you use ATI's OpenGL support, what about removing mesa?

The problem is - the lib "libGL.so.1.2" is part of mesa AND fglrx (did fglrx install involve any "force"?). So, if you remove mesa, you /might/ also remove this file. You could take a backup copy of the overlapping files (mesa vs fglrx), remove mesa and then put the files back in place (links/files).

However, as you note, still a bit uncomfortable. Live with it, or take a risk?

---

### Post by teumima on 2005-03-31
[QUOTE=alastair]I understand your reluctance to play around with the ATI setup. Anyone who's had to set up fglrx drivers knows the pain involved sometimes.

So ... alternatively, assuming you use ATI's OpenGL support, what about removing mesa?

The problem is - the lib "libGL.so.1.2" is part of mesa AND fglrx (did fglrx install involve any "force"?). So, if you remove mesa, you /might/ also remove this file. You could take a backup copy of the overlapping files (mesa vs fglrx), remove mesa and then put the files back in place (links/files).

However, as you note, still a bit uncomfortable. Live with it, or take a risk?[/QUOTE]
 hey man

i used a force. i use ati's open gl support.

i tried removing mesa once and it wanted to uninstall another 40 packages. How do i remove mesa properly? any side effects? i dont really use mesa for anything.

---

### Post by whatever on 2005-03-31
you don't have to rebuild the kernel module.

sudo dpkg -r fglrx-6-8-0
sudo apt-get install xlibmesa-gl
sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb

^ this is enough, but still anoying...

---

### Post by alastair on 2005-03-31
I'm not sure there's a clean way to deal with this. ATI fgl provides OpenGL libs, as does Mesa. But Mesa is more "official". You're only interested in the "overlap" i.e. the files like "libGL.so.1.2" that both provide. If you remove Mesa (and ignore/force dependencies like alsaplayer, xscreensaver-gl etc.), the fgl "libGL.so.1.2" will be used by the other apps. But this is all a bit unclean. Comment no. 2 is a way to sort this mesa update out .... but  It might be best to just ignore the mesa upgrades/updates.

---

### Post by teumima on 2005-04-01
Hi guys.

I did an update and just ignored xlibmesa-gl_6.8.2-8_i386.deb

If I can just keep on doing that, i'd rather. Any side effects by ignoring that?

I don't use mesa for 3D graphics.

---

### Post by teumima on 2005-04-01
Ok this is funny.

I'm playing Counterstrike then all of a sudden it freezes. I restart x (cntrl-alt + backsp) then counterstrike wont start again. All I see is a gray screen.

I type: fglrxinfo


And guess what? Mesa GL (!?!?!?) my ati was gone.

 glxgears showed 300 fpm

So I was forced to remove my ati driver update mesa and then follow Dracontopes instructions and now its back and i have the mesa updated.

I still dont get how mesa took over.

thanks for all your help guys.

BTW Dracontops instructions are 100%. I don't know about the rest of you, didn't try them.

---

### Post by teumima on 2005-04-01
[QUOTE=whatever]you don't have to rebuild the kernel module.

sudo dpkg -r fglrx-6-8-0
sudo apt-get install xlibmesa-gl
sudo dpkg -i --force-overwrite fglrx-6-8-0_8.10.19-2_i386.deb

^ this is enough, but still anoying...[/QUOTE]
 I didn't try your instructions, but it makes sense that they would work.

---

### Post by Dracontopes on 2005-04-01
[QUOTE=teumima]hey man

not to question ur credibility. U tried this and it worked? It took me months to sort out my ati driver and i'd really miss it.[/QUOTE]
 I tried this like 3 times, because xlibmesa-gl needed update 3 times :P And nothing happened to my xorg.conf, so I guess it's safe. But don't blame me if anything goes wrong, BACKUP your xorg.conf :O

---

### Post by bobmitch on 2005-04-01
[QUOTE=Dracontopes]I tried this like 3 times, because xlibmesa-gl needed update 3 times :P And nothing happened to my xorg.conf, so I guess it's safe. But don't blame me if anything goes wrong, BACKUP your xorg.conf :O[/QUOTE]

Nothing in these instructions will touch your xorg.conf file - only by running **fglrxconfig** again will this happen.

I have had to do this routine about 3 times in the last two weeks alone - it`s the price to pay for being on the bleeding edge of linux. :)

---

### Post by JGJones on 2005-04-06
PC Spec - AMD Athlon XP 2800+ with 1Gb RAM and ATI Radeon 9800 Pro

I've installed either the following two:

Via apt-get - xorg-driver-fglrx which is version 6-8-0 - the same as from ATI directly.

It use the mesa GL extensions which from my understanding is software rendered OpenGL...as I get about 300fps in glxgears (20-25fps full screen)

After reading the forums, I have downloaded the RPM package from ATI.com and used alien to convert it into a deb package.

I then did the below:

1. Shut down X: sudo /etc/init.d/gdm stop
2. Update xlibmesa-gl via apt-get
3. Used the command to install ATI driver: sudo dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb

The next two commands as suggested in here:

4. Build modules: cd /lib/modules/fglrx/build_mod , and then, sudo sh make.sh
5. Build modules #2: cd .. (back to /lib/modules/fglrx) , and then, sudo sh make_install.sh

And....

I'm still using mesa-GL and I'm tearing my hairs out...I need 3D acceralation and I don't want to purchase a nvidia card!!

How the hell do I get ATI 3D to work?

Here is a copy of my xorg.conf file for your reading pleasure:

```

Section "Module"
#Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "Extensions"
	Option 		"Composite" 		"Disable"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	Option 		"BackingStore" 		"Yes"


# If X refuses to use the screen resolution you asked for, uncomment this

#	Option "NoDDC"

	Option 		"VideoOverlay" 		"on"

# Note: When OpenGL Overlay is enabled, Video Overlay will be disabled automatically

	Option 		"OpenGLOverlay" 	"off"

# If OpenGL acceleration doesn't work, try using "yes" here and disable the kernel agpgart driver.

	Option 		"UseInternalAGPGART" 	"yes"

EndSection

Section "Monitor"
	Identifier	"iiyama"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"iiyama"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

As you can see from my xorg.conf file, I have enabled internal AGP (disabling it make no difference) and I have added the following two modules to my blacklist in hotplug:

agpgart
nvidia_agp

And I've confirmed that they are NOT loaded by checknig in lsmod.

I've heard suggestions that I shouldn't use internal AGP if I have a nForce2 motherboard?

Many thanks to anyone that can help me

---

### Post by teumima on 2005-04-06
[QUOTE=JGJones]PC Spec - AMD Athlon XP 2800+ with 1Gb RAM and ATI Radeon 9800 Pro

I've installed either the following two:

Via apt-get - xorg-driver-fglrx which is version 6-8-0 - the same as from ATI directly.

It use the mesa GL extensions which from my understanding is software rendered OpenGL...as I get about 300fps in glxgears (20-25fps full screen)

After reading the forums, I have downloaded the RPM package from ATI.com and used alien to convert it into a deb package.

I then did the below:

1. Shut down X: sudo /etc/init.d/gdm stop
2. Update xlibmesa-gl via apt-get
3. Used the command to install ATI driver: sudo dpkg -i --force-overwrite /path/to/file/fglrxpackagefile.deb

The next two commands as suggested in here:

4. Build modules: cd /lib/modules/fglrx/build_mod , and then, sudo sh make.sh
5. Build modules #2: cd .. (back to /lib/modules/fglrx) , and then, sudo sh make_install.sh

And....

I'm still using mesa-GL and I'm tearing my hairs out...I need 3D acceralation and I don't want to purchase a nvidia card!!

How the hell do I get ATI 3D to work?

Here is a copy of my xorg.conf file for your reading pleasure:

```

Section "Module"
#Load	"GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"speedo"
	Load	"type1"
	Load	"v4l"
	Load	"vbe"
	Load	"xtt"
EndSection

Section "Extensions"
	Option 		"Composite" 		"Disable"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:3:0:0"
	Option 		"BackingStore" 		"Yes"


# If X refuses to use the screen resolution you asked for, uncomment this

#	Option "NoDDC"

	Option 		"VideoOverlay" 		"on"

# Note: When OpenGL Overlay is enabled, Video Overlay will be disabled automatically

	Option 		"OpenGLOverlay" 	"off"

# If OpenGL acceleration doesn't work, try using "yes" here and disable the kernel agpgart driver.

	Option 		"UseInternalAGPGART" 	"yes"

EndSection

Section "Monitor"
	Identifier	"iiyama"
	Option		"DPMS"
	HorizSync	30-130
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"iiyama"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

As you can see from my xorg.conf file, I have enabled internal AGP (disabling it make no difference) and I have added the following two modules to my blacklist in hotplug:

agpgart
nvidia_agp

And I've confirmed that they are NOT loaded by checknig in lsmod.

I've heard suggestions that I shouldn't use internal AGP if I have a nForce2 motherboard?

Many thanks to anyone that can help me[/QUOTE]
 hey man

change this option: 
Option         "UseInternalAGPGART"     "yes"

to "no"

that is:

Option         "UseInternalAGPGART"     "no"


Keep me posted.

a.t.

---

### Post by JGJones on 2005-04-06
As I've stated, it doesn't really make any difference which is why it's so bloody annoying :)

Mind you all these problems are a wonderful way of learning how Linux works and I'm quickly getting the hang of Linux that I now use it as my main system.

---

### Post by teumima on 2005-04-06
[QUOTE=JGJones]As I've stated, it doesn't really make any difference which is why it's so bloody annoying :)

Mind you all these problems are a wonderful way of learning how Linux works and I'm quickly getting the hang of Linux that I now use it as my main system.[/QUOTE]
 It does make a difference. That option has to be "no"

once u've done that, log off "x" and then try make again.

---

### Post by JGJones on 2005-04-06
[QUOTE=teumima]It does make a difference. That option has to be "no"

once u've done that, log off "x" and then try make again.[/QUOTE]

No it doesn't. I have tried both. I've tried "No" with apggart and nvidia_agp enabled AND blacklisted - both still give me mesa GL.

I've tried "Yes" with agpgart and nvidia_agp enabled AND blacklisted - both still give me mesaGL.

Have a look at my glxinfo:

```

 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

The above is after I've changed a single line in my xorg.conf to use Option "UseInternalAGPGART" "No" and I have un-blacklisted agpgart and nvidia_agp (They are listed in lsmod).

As you can see - Direct Rendering isn't enabled and it's using mesa-gl.

However when agpgart and nvidia_agp is blacklisted (not listed in lsmod) and I have Option "UseInternalAGPGART" "No" in my xorg.conf file, it's the same result.

Like I said, no difference. But thanks for the help :) Any other ideas?

---

### Post by teumima on 2005-04-06
[QUOTE=JGJones]No it doesn't. I have tried both. I've tried "No" with apggart and nvidia_agp enabled AND blacklisted - both still give me mesa GL.

I've tried "Yes" with agpgart and nvidia_agp enabled AND blacklisted - both still give me mesaGL.

Have a look at my glxinfo:

```

 glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: No
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_EXT_import_context, GLX_OML_swap_method, GLX_SGI_make_current_read,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_ATI_pixel_format_float,
    GLX_ATI_render_texture
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context,
    GLX_ARB_multisample
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:
    GL_ARB_imaging, GL_ARB_multitexture, GL_ARB_texture_border_clamp,
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3,
    GL_ARB_transpose_matrix, GL_EXT_abgr, GL_EXT_blend_color,
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_lod_bias
glu version: 1.3
glu extensions:
    GLU_EXT_nurbs_tessellator, GLU_EXT_object_space_tess

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x23 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x24 24 tc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x25 24 tc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x27 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  0  0  0  0  0  1 0 None
0x28 24 dc  0 24  0 r  y  .  8  8  8  0  0 16  8 16 16 16  0  1 0 None
0x29 24 dc  0 32  0 r  y  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None
0x2a 24 dc  0 32  0 r  .  .  8  8  8  8  0 16  8 16 16 16 16  1 0 None

```

The above is after I've changed a single line in my xorg.conf to use Option "UseInternalAGPGART" "No" and I have un-blacklisted agpgart and nvidia_agp (They are listed in lsmod).

As you can see - Direct Rendering isn't enabled and it's using mesa-gl.

However when agpgart and nvidia_agp is blacklisted (not listed in lsmod) and I have Option "UseInternalAGPGART" "No" in my xorg.conf file, it's the same result.

Like I said, no difference. But thanks for the help :) Any other ideas?[/QUOTE]
 Ok so you're still getting mesa, that doesnt mean it doesn't make a difference.  The option has to be "no"

If you still get mesa, then the error is elsewhere. You need to cancel out the problems, so change it to "no"

Did you try sh make.sh again after choosing "no"?

Did you run the fglrx configuration? fgrlxconfig? did u choose there "yes" to using external agp?

---

### Post by JGJones on 2005-04-06
> Ok so you're still getting mesa, that doesnt mean it doesn't make a difference.  The option has to be "no"

OK I'll leave it as "No"

> If you still get mesa, then the error is elsewhere. You need to cancel out the problems, so change it to "no"

Did you try sh make.sh again after choosing "no"?

Yes I did and again after rebooting to make sure :)

> Did you run the fglrx configuration? fgrlxconfig? did u choose there "yes" to using external agp?

Not after I've changed the option in xorg.conf so I'll give that a try and let you know. Thanks.

---

### Post by JGJones on 2005-04-06
Doesn't work either. However looking at xorg.log (I forgot all about that) I notice I have this:
```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bd3000 at 0xb7db6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

My kernal is the wrong one? What's the answer to this one? I think I noticed something in the forums about this so I'll search for it.

Actually my 3D accelaration is even worse...from 300fps down to just 80 fps.

---

### Post by teumima on 2005-04-06
[QUOTE=JGJones]Doesn't work either. However looking at xorg.log (I forgot all about that) I notice I have this:
```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bd3000 at 0xb7db6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```

My kernal is the wrong one? What's the answer to this one? I think I noticed something in the forums about this so I'll search for it.

Actually my 3D accelaration is even worse...from 300fps down to just 80 fps.[/QUOTE]
 type uname -r

you have to make sure that the headers u use r the same as ur kernel

Do u have fglrx in your /etc/modules ?

---

### Post by JGJones on 2005-04-06
[QUOTE=teumima]type uname -r

you have to make sure that the headers u use r the same as ur kernel

Do u have fglrx in your /etc/modules ?[/QUOTE]

/etc/modules - yes I do have fglrx there.

uname -r give me this:

2.6.10-5-k7

So checking in Synaptic I have linux headers 2.6.10-5-k7 installed already

Also have linux-image 2.6.10-5-k7 as well as the restricted modules blah blah....

However I notice I have more "later" version of linux-images (without ubuntu flags) so I'm uninstalling them now to ensure I have all "Ubuntu certified" linux kernal version - minimise any problems :)

Could be that the make.sh etc was compiling for the later version of kernal and not the one I have? Perhaps, anyway I will run the whole installtion thingy again once I've got all ubuntu certified linux stuff installed and no later versions (without ubuntu flag) and then do a lot of praying.

I've heard that ATI drivers are harder to install than nvidia...but this is surely take the p*** too far  :roll:

---

### Post by teumima on 2005-04-07
[QUOTE=JGJones]/etc/modules - yes I do have fglrx there.

uname -r give me this:

2.6.10-5-k7

So checking in Synaptic I have linux headers 2.6.10-5-k7 installed already

Also have linux-image 2.6.10-5-k7 as well as the restricted modules blah blah....

However I notice I have more "later" version of linux-images (without ubuntu flags) so I'm uninstalling them now to ensure I have all "Ubuntu certified" linux kernal version - minimise any problems :)

Could be that the make.sh etc was compiling for the later version of kernal and not the one I have? Perhaps, anyway I will run the whole installtion thingy again once I've got all ubuntu certified linux stuff installed and no later versions (without ubuntu flag) and then do a lot of praying.

I've heard that ATI drivers are harder to install than nvidia...but this is surely take the p*** too far  :roll:[/QUOTE]
 Lol

I have exactly the same kernel as you. It should work.

However updating to stuff that is not supported by Ubuntu yet, can mess things up.

Let me know if it maded a difference.

---

### Post by JGJones on 2005-04-07
Aye....morning here now....All Ubuntu supported kernals and no later versions installed now (I dunno how the later version crept in, I never have selected them!)

I shall start the driver installation from the very beginning. Right now I'm using ATI open source driver, and the fglrx deb package is primed and ready to fire :)

---

### Post by JGJones on 2005-04-07
OK this is what I did:

Having made sure all linux versions such as image/headers/restricted modules et al are all of the same version (there are NO earlier or later versions - they are all 2.6.10-5-k7)

I then did:

sudo /etc/init.d/gdm stop

And once in terminal I then did this:

sudo modprobe -r fglrx
sudo apt-get remove fglrx-6-8-0
sudo apt-get -reinstall install xlibmesa-gl (as I already had the latest version, I wanted to reinstall to ensure all files are of xlibmesa-gl, minimise any problems)
sudo dpkg -i fglrx.deb

Of course that last command didn't work as I forgot the --force-overwrite switch so I did it again

sudo dpkg -i --force-overwrite fglrx.deb

then moving to /lib/modules/fglrx/build_mod and did sudo sh make.sh

File ran successful (although the message mentioned something about a missing file? Is this to be expected? But I did get a build succeeded result at end)

Then went back up a level to do sudo sh make_install.sh

That succeeded as well

Then I made a backup copy of xorg.conf file (sudo cp /etc/X11/xorg.con /etc/X11/xorg.conf-backup)

And I ran fglrxconfig to make a new xorg file as below:

```

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"gb"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30-130
    VertRefresh 60-120
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:3:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1600x1200"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

```

And finally, instead of starting up X, I decided to reboot instead - sudo shutdown -r -t sec now

X started successfully after reboot.

glxinfo |grep OpenGL give me this:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:

And glxgears give me about 80-100fps in a small window....thus I'm worse off

Looking at Xorg.0.log...

```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bc5000 at 0xb7db6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *

```

I have the latest kernal that IS supported by Ubuntu - 2.6.10-5-k7 - any later version are 2.6.11 and NOT supported by Ubuntu.

Xorg version is 6.8.2-10 (latest from ubuntu)

I've downloaded the driver from ATI website that is for xorg 6.8.

I'm doing everything right and yet I'm not getting 3D. I have one idea which I'll try out later on unless anyone have any suggestions here?

Do I *have* to get the linux-386 packages? Since it appears that it doesn't work and I only have the k7 packages (I have an AMD Athlon XP 2800) and I don't want to go back to a slower 386 packages!!

---

### Post by teumima on 2005-04-07
[QUOTE=JGJones]OK this is what I did:

Having made sure all linux versions such as image/headers/restricted modules et al are all of the same version (there are NO earlier or later versions - they are all 2.6.10-5-k7)

I then did:

sudo /etc/init.d/gdm stop

And once in terminal I then did this:

sudo modprobe -r fglrx
sudo apt-get remove fglrx-6-8-0
sudo apt-get -reinstall install xlibmesa-gl (as I already had the latest version, I wanted to reinstall to ensure all files are of xlibmesa-gl, minimise any problems)
sudo dpkg -i fglrx.deb

Of course that last command didn't work as I forgot the --force-overwrite switch so I did it again

sudo dpkg -i --force-overwrite fglrx.deb

then moving to /lib/modules/fglrx/build_mod and did sudo sh make.sh

File ran successful (although the message mentioned something about a missing file? Is this to be expected? But I did get a build succeeded result at end)

Then went back up a level to do sudo sh make_install.sh

That succeeded as well

Then I made a backup copy of xorg.conf file (sudo cp /etc/X11/xorg.con /etc/X11/xorg.conf-backup)

And I ran fglrxconfig to make a new xorg file as below:

```

# File: xorg.conf
# File generated by fglrxconfig (C) ATI Research, a substitute for xf86config.

# Note by ATI: the below copyright notice is there for servicing possibly
# pending third party rights on the file format and the instance of this file.
#
# Copyright (c) 1999 by The XFree86 Project, Inc.
#
# Permission is hereby granted, free of charge, to any person obtaining a
# copy of this software and associated documentation files (the "Software"),
# to deal in the Software without restriction, including without limitation
# the rights to use, copy, modify, merge, publish, distribute, sublicense,
# and/or sell copies of the Software, and to permit persons to whom the
# Software is furnished to do so, subject to the following conditions:
# 
# The above copyright notice and this permission notice shall be included in
# all copies or substantial portions of the Software.
# 
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL
# THE XFREE86 PROJECT BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY,
# WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF
# OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
# 
# Except as contained in this notice, the name of the XFree86 Project shall
# not be used in advertising or otherwise to promote the sale, use or other
# dealings in this Software without prior written authorization from the
# XFree86 Project.
#

# **********************************************************************
# Refer to the XF86Config(4/5) man page for details about the format of 
# this file.
# **********************************************************************

# **********************************************************************
# DRI Section
# **********************************************************************
Section "dri"
# Access to OpenGL ICD is allowed for all users:
    Mode 0666
# Access to OpenGL ICD is restricted to a specific user group:
#    Group 100    # users
#    Mode 0660
EndSection

# **********************************************************************
# Module section -- this  section  is used to specify
# which dynamically loadable modules to load.
# **********************************************************************
#
Section "Module"

# This loads the DBE extension module.

    Load        "dbe"  	# Double buffer extension

# This loads the miscellaneous extensions module, and disables
# initialisation of the XFree86-DGA extension within that module.
    SubSection  "extmod"
      Option    "omit xfree86-dga"   # don't initialise the DGA extension
    EndSubSection

# This loads the Type1 and FreeType font modules
    Load        "type1"
    Load        "freetype"

# This loads the GLX module
    Load        "glx"   # libglx.a
    Load        "dri"   # libdri.a

EndSection

# **********************************************************************
# Files section.  This allows default font and rgb paths to be set
# **********************************************************************

Section "Files"

# The location of the RGB database.  Note, this is the name of the
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.

    RgbPath	"/usr/X11R6/lib/X11/rgb"

# Multiple FontPath entries are allowed (which are concatenated together),
# as well as specifying multiple comma-separated entries in one FontPath
# command (or a combination of both methods)
# 
# If you don't have a floating point coprocessor and emacs, Mosaic or other
# programs take long to start up, try moving the Type1 and Speedo directory
# to the end of this list (or comment them out).
# 

#    FontPath   "/usr/X11R6/lib/X11/fonts/local/"
    FontPath   "/usr/X11R6/lib/X11/fonts/misc/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/:unscaled"
    FontPath   "/usr/X11R6/lib/X11/fonts/Type1/"
    FontPath   "/usr/X11R6/lib/X11/fonts/Speedo/"
    FontPath   "/usr/X11R6/lib/X11/fonts/75dpi/"
    FontPath   "/usr/X11R6/lib/X11/fonts/100dpi/"

# The module search path.  The default path is shown here.

#    ModulePath "/usr/X11R6/lib/modules"

EndSection

# **********************************************************************
# Server flags section.
# **********************************************************************

Section "ServerFlags"

# Uncomment this to cause a core dump at the spot where a signal is 
# received.  This may leave the console in an unusable state, but may
# provide a better stack trace in the core dump to aid in debugging

#    Option "NoTrapSignals"

# Uncomment this to disable the <Crtl><Alt><BS> server abort sequence
# This allows clients to receive this key event.

#    Option "DontZap"

# Uncomment this to disable the <Crtl><Alt><KP_+>/<KP_-> mode switching
# sequences.  This allows clients to receive these key events.

#    Option "Dont Zoom"

# Uncomment this to disable tuning with the xvidtune client. With
# it the client can still run and fetch card and monitor attributes,
# but it will not be allowed to change them. If it tries it will
# receive a protocol error.

#    Option "DisableVidModeExtension"

# Uncomment this to enable the use of a non-local xvidtune client. 

#    Option "AllowNonLocalXvidtune"

# Uncomment this to disable dynamically modifying the input device
# (mouse and keyboard) settings. 

#    Option "DisableModInDev"

# Uncomment this to enable the use of a non-local client to
# change the keyboard or mouse settings (currently only xset).

#    Option "AllowNonLocalModInDev"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
# For most OSs the protocol can be omitted (it defaults to "Standard").
# When using XQUEUE (only for SVR3 and SVR4, but not Solaris),
# uncomment the following line.

#    Option "Protocol"   "Xqueue"

    Option "AutoRepeat" "500 30"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#    Option "Xleds"      "1 2 3"

#    Option "LeftAlt"    "Meta"
#    Option "RightAlt"   "ModeShift"

# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#    Option "XkbModel"   "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#    Option "XkbModel"   "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#    Option "XkbLayout"  "de"
# or:
#    Option "XkbLayout"  "de"
#    Option "XkbVariant" "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#    Option "XkbOptions" "ctrl:swapcaps"

# These are the default XKB settings for XFree86
#    Option "XkbRules"   "xfree86"
#    Option "XkbModel"   "pc101"
#    Option "XkbLayout"  "us"
#    Option "XkbVariant" ""
#    Option "XkbOptions" ""

#    Option "XkbDisable"

    Option "XkbRules"	"xfree86"
    Option "XkbModel"	"pc105"
    Option "XkbLayout"	"gb"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver "mouse"
    Option "Protocol"   "ImPS/2"
    Option "ZAxisMapping"   "4 5"
    Option "Device"     "/dev/input/mice"

# When using XQUEUE, comment out the above two lines, and uncomment
# the following line.

#    Option "Protocol"   "Xqueue"

# Baudrate and SampleRate are only for some Logitech mice. In
# almost every case these lines should be omitted.

#    Option "BaudRate"   "9600"
#    Option "SampleRate" "150"

# Emulate3Buttons is an option for 2-button Microsoft mice
# Emulate3Timeout is the timeout in milliseconds (default is 50ms)

    Option "Emulate3Buttons"
#    Option "Emulate3Timeout"    "50"

# ChordMiddle is an option for some 3-button Logitech mice

#    Option "ChordMiddle"

EndSection


# **********************************************************************
# Other input device sections 
# this is optional and is required only if you
# are using extended input devices.  This is for example only.  Refer
# to the XF86Config man page for a description of the options.
# **********************************************************************
#
# Section "InputDevice" 
#    Identifier  "Mouse2"
#    Driver      "mouse"
#    Option      "Protocol"      "MouseMan"
#    Option      "Device"        "/dev/mouse2"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball"
#    Driver     "magellan"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "spaceball2"
#    Driver     "spaceorb"
#    Option     "Device"         "/dev/cua0"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen0"
#    Driver     "microtouch"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "1412"
#    Option     "MaxX"           "15184"
#    Option     "MinY"           "15372"
#    Option     "MaxY"           "1230"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection
#
# Section "InputDevice"
#    Identifier "touchscreen1"
#    Driver     "elo2300"
#    Option     "Device"         "/dev/ttyS0"
#    Option     "MinX"           "231"
#    Option     "MaxX"           "3868"
#    Option     "MinY"           "3858"
#    Option     "MaxY"           "272"
#    Option     "ScreenNumber"   "0"
#    Option     "ReportingMode"  "Scaled"
#    Option     "ButtonThreshold"    "17"
#    Option     "ButtonNumber"   "1"
#    Option     "SendCoreEvents"
# EndSection

# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"
    Identifier  "Monitor0"
    HorizSync   30-130
    VertRefresh 60-120
    Option "DPMS"

# === mode lines based on GTF ===
# VGA @ 100Hz
# Modeline "640x480@100" 43.163 640 680 744 848 480 481 484 509 +hsync +vsync
# SVGA @ 100Hz
# Modeline "800x600@100" 68.179 800 848 936 1072 600 601 604 636 +hsync +vsync
# XVGA @ 100Hz
# Modeline "1024x768@100" 113.309 1024 1096 1208 1392 768 769 772 814 +hsync +vsync
# 1152x864 @ 60Hz
# Modeline "1152x864@60" 81.642 1152 1216 1336 1520 864 865 868 895 +hsync +vsync
# 1152x864 @ 85Hz
# Modeline "1152x864@85" 119.651 1152 1224 1352 1552 864 865 868 907 +hsync +vsync
# 1152x864 @ 100Hz
# Modeline "1152x864@100" 143.472 1152 1232 1360 1568 864 865 868 915 +hsync +vsync
# 1280x960 @ 75Hz
# Modeline "1280x960@75" 129.859 1280 1368 1504 1728 960 961 964 1002 +hsync +vsync
# 1280x960 @ 100Hz
# Modeline "1280x960@100" 178.992 1280 1376 1520 1760 960 961 964 1017  +hsync +vsync
# SXGA @ 100Hz
# Modeline "1280x1024@100" 190.960 1280 1376 1520 1760 1024 1025 1028 1085 +hsync +vsync
# SPEA GDM-1950 (60Hz,64kHz,110MHz,-,-): 1280x1024 @ V-freq: 60.00 Hz, H-freq: 63.73 KHz
# Modeline "GDM-1950"  109.62  1280 1336 1472 1720  1024 1024 1026 1062 -hsync -vsync
# 1600x1000 @ 60Hz
# Modeline "1600x1000" 133.142 1600 1704 1872 2144 1000 1001 1004 1035 +hsync +vsync
# 1600x1000 @ 75Hz
# Modeline "1600x1000" 169.128 1600 1704 1880 2160 1000 1001 1004 1044 +hsync +vsync
# 1600x1000 @ 85Hz
# Modeline "1600x1000" 194.202 1600 1712 1888 2176 1000 1001 1004 1050 +hsync +vsync
# 1600x1000 @ 100Hz
# Modeline "1600x1000" 232.133 1600 1720 1896 2192 1000 1001 1004 1059 +hsync +vsync
# 1600x1024 @ 60Hz
# Modeline "1600x1024" 136.385 1600 1704 1872 2144 1024 1027 1030 1060 +hsync +vsync
# 1600x1024 @ 75Hz
# Modeline "1600x1024" 174.416 1600 1712 1888 2176 1024 1025 1028 1069 +hsync +vsync
# 1600x1024 @ 76Hz
# Modeline "1600x1024" 170.450 1600 1632 1792 2096 1024 1027 1030 1070 +hsync +vsync
# 1600x1024 @ 85Hz
# Modeline "1600x1024" 198.832 1600 1712 1888 2176 1024 1027 1030 1075 +hsync +vsync
# 1920x1080 @ 60Hz
# Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
# 1920x1080 @ 75Hz
# Modeline "1920x1080" 211.436 1920 2056 2264 2608 1080 1081 1084 1126 +hsync +vsync
# 1920x1200 @ 60Hz
# Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
# 1920x1200 @ 75Hz
# Modeline "1920x1200" 246.590 1920 2064 2272 2624 1200 1201 1203 1253 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 2048x1536 @ 60
# Modeline "2048x1536" 266.952 2048 2200 2424 2800 1536 1537 1540 1589 +hsync +vsync
# 1400x1050 @ 60Hz M9 Laptop mode 
# ModeLine "1400x1050" 122.000 1400 1488 1640 1880 1050 1052 1064 1082 +hsync +vsync
# 1920x2400 @ 25Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@25" 124.620 1920 1928 1980 2048 2400 2401 2403 2434 +hsync +vsync
# 1920x2400 @ 30Hz for IBM T221, VS VP2290 and compatible display devices
# Modeline "1920x2400@30" 149.250 1920 1928 1982 2044 2400 2402 2404 2434 +hsync +vsync

EndSection


# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

# Standard VGA Device:

Section "Device"
    Identifier  "Standard VGA"
    VendorName  "Unknown"
    BoardName   "Unknown"

# The chipset line is optional in most cases.  It can be used to override
# the driver's chipset detection, and should not normally be specified.

#    Chipset     "generic"

# The Driver line must be present.  When using run-time loadable driver
# modules, this line instructs the server to load the specified driver
# module.  Even when not using loadable driver modules, this line
# indicates which driver should interpret the information in this section.

    Driver      "vga"
# The BusID line is used to specify which of possibly multiple devices
# this section is intended for.  When this line isn't present, a device
# section can only match up with the primary video device.  For PCI
# devices a line like the following could be used.  This line should not
# normally be included unless there is more than one video device
# installed.

#    BusID       "PCI:0:10:0"

#    VideoRam    256

#    Clocks      25.2 28.3

EndSection

# === ATI device section ===

Section "Device"
    Identifier                          "ATI Graphics Adapter"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x00000000"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                 "0"
    Option "BlockSignalsOnLock"         "on"
    Option "UseInternalAGPGART"         "no"
    Option "ForceGenericCPU"            "no"
    BusID "PCI:3:0:0"    # vendor=1002, device=4e48
    Screen 0
EndSection

# **********************************************************************
# Screen sections
# **********************************************************************

# Any number of screen sections may be present.  Each describes
# the configuration of a single screen.  A single specific screen section
# may be specified from the X server command line with the "-screen"
# option.
Section "Screen"
    Identifier  "Screen0"
    Device      "ATI Graphics Adapter"
    Monitor     "Monitor0"
    DefaultDepth 24
    #Option "backingstore"

    Subsection "Display"
        Depth       24
        Modes       "1600x1200"
        ViewPort    0 0  # initial origin if mode is smaller than desktop
#        Virtual     1280 1024
    EndSubsection
EndSection

# **********************************************************************
# ServerLayout sections.
# **********************************************************************

# Any number of ServerLayout sections may be present.  Each describes
# the way multiple screens are organised.  A specific ServerLayout
# section may be specified from the X server command line with the
# "-layout" option.  In the absence of this, the first section is used.
# When now ServerLayout section is present, the first Screen section
# is used alone.

Section "ServerLayout"

# The Identifier line must be present
    Identifier  "Server Layout"

# Each Screen line specifies a Screen section name, and optionally
# the relative position of other screens.  The four names after
# primary screen name are the screens to the top, bottom, left and right
# of the primary screen.

    Screen "Screen0"

# Each InputDevice line specifies an InputDevice section name and
# optionally some options to specify the way the device is to be
# used.  Those options include "CorePointer", "CoreKeyboard" and
# "SendCoreEvents".

    InputDevice "Mouse1" "CorePointer"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

### EOF ###

```

And finally, instead of starting up X, I decided to reboot instead - sudo shutdown -r -t sec now

X started successfully after reboot.

glxinfo |grep OpenGL give me this:

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)
OpenGL extensions:

And glxgears give me about 80-100fps in a small window....thus I'm worse off

Looking at Xorg.0.log...

```

(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xf8bc5000 at 0xb7db6000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *

```

I have the latest kernal that IS supported by Ubuntu - 2.6.10-5-k7 - any later version are 2.6.11 and NOT supported by Ubuntu.

Xorg version is 6.8.2-10 (latest from ubuntu)

I've downloaded the driver from ATI website that is for xorg 6.8.

I'm doing everything right and yet I'm not getting 3D. I have one idea which I'll try out later on unless anyone have any suggestions here?

Do I *have* to get the linux-386 packages? Since it appears that it doesn't work and I only have the k7 packages (I have an AMD Athlon XP 2800) and I don't want to go back to a slower 386 packages!![/QUOTE]
 Hey man

No u don't need to switch to the 386 ones. I have the same AMD Athlon XP as you and use the same kernel k7 and I have the fglrx working with over a 1000 FPS and no Mesa Gl support.

The only thing I can think of is that the missing file is a problem, as it has to go smooth. 

I strongly reccomend that u go to irc.freenode.org #ati and ask someone there. That is how I finally got it all working.

If you're getting an error in make, did you do apt-cache search linux-headers? and choose the linux-headers-2.6.10-5-k7 ?

Keep me posted.

---

### Post by JGJones on 2005-04-07
Already got that header. I guess it's the missing file, I'll run the make.sh again to find out what it is....and here's the result:

```

jgjones@gollum:/lib/modules/fglrx/build_mod $ sudo sh make.sh
ATI module generator V 2.0
==========================
initializing...
cleaning...
patching 'highmem.h'...
assuming new VMA API since we do have kernel 2.6.x...
doing Makefile based build for kernel 2.6.x and higher
make -C /lib/modules/2.6.10-5-k7/build SUBDIRS=/lib/modules/fglrx/build_mod/2.6.x modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-k7'
  Building modules, stage 2.
  MODPOST
Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-k7'
build succeeded with return value 0
duplicating results into driver repository...
done.
==============================
You must change your working directory to /lib/modules/fglrx
and then call ./make_install.sh in order to install the built module.
==============================

```

I guess this is the problem for me:

Warning: could not find /lib/modules/fglrx/build_mod/2.6.x/.libfglrx_ip.a.GCC3.cmd for /lib/modules/fglrx/build_mod/2.6.x/libfglrx_ip.a.GCC3

---

### Post by teumima on 2005-04-07
yeah i think so.

go to #ati irc.freenode.org

---

### Post by maqi on 2005-04-07
If you try and mix the ubuntu restricted modules with the latest ATI stuff your just doubling up and making a huge farking mess. So choose one or the other - you can't have both. 

If you're using an official ubuntu kernel -and you are by the looks- you're much better off going with the official drivers. 

```
$ sudo dpkg -P fglrx-6-8-0
$ sudo apt-get install linux-restricted-modules-<your kernel> xorg-driver-fglrx
```

Then deal with xorg.conf. Should work beautifully.

maqi

[EDIT] BTW - One thing is for sure - whichever way you go **don't use fglrxconfig to generate your xorg.conf**. Although some of the xorg.conf ideas on these forums are OK, better is to go [here](http://xoomer.virgilio.it/flavio.stanchina/debian/fglrx-installer.html#install) and look at section **5 - Configure X**. Copy and paste the settings there into the relevant bits of your xorg.conf file - after first backing it up of course.

I used to use these packages for debian (with xfree86) with no problems whatsoever, but these packages don't seem to work with ubuntu even though they are supposed to deal with xorg -  I wish I knew how to modify the provided scripts to work with ubuntu (I've tried, but I know nothing). 

Even though this configuration is for Xfree86 it worked better for me than anything suggested on these forums, ie, perfectly, and **much** better than fglrxconfig - which basically didn't work at all.[/EDIT]

---

### Post by JGJones on 2005-04-07
[QUOTE=teumima]yeah i think so.

go to #ati irc.freenode.org[/QUOTE]
 Finally....after a few hours it's all sorted. The missing files in make.sh is normal so that's ok, but the problem is my old drivers was still clogging up my system despite havnig uninstalled it so I had to purge it from my system and disable composite and few other stuff and finally I now get 4715fps in glxgears and 280fps fullscreen glxgears

That channel you pointed at sure was very helpful!

---

### Post by StacyWebb on 2005-04-07
maqi, just wanted to let you know, that worked perfect for me, Thanks also in the other posts there are items about the cpu pegging when running 3d apps, this fixed that too. Thanks again.

---

### Post by maqi on 2005-04-07
[QUOTE=StacyWebb]maqi, just wanted to let you know, that worked perfect for me, Thanks also in the other posts there are items about the cpu pegging when running 3d apps, this fixed that too. Thanks again.[/QUOTE]

Glad it worked for ya Stacey :)

maqi

---

### Post by ZeusBR on 2005-04-08
Hi.

I'm new on linux and have the same problem...

I have an Althon XP 2500+ and ATi Radeon 9600
Dont know what version of kernel. Its the one that comes with the CD.
But I don't know what to do to install the package from ATi's site.
I seems that some of you did, but I have no idea how.
Can you help me?

PS: sorry, I'm brazilian, my english sux.

---

### Post by edgarallan on 2005-07-13
hi i've barton 2500 on nforce2 mobo and radeon 2600 pro (agpgart and nvidia_agp loaded into kernel)

i've done all the possible... followed all the stiky messages. (2 days of frustration maybe i will return winzozz)

fglrxinfo say i'm in MESA
Xorg.0.log say loaded kernel module for "fglrx" driver
Kernel Module version matches driver.
(II) fglrx(0): [drm] DRM interface version 1.0
(II) fglrx(0): [drm] created "fglrx" driver at busid "PCI:2:0:0"
DRI initialization successfull!
glrxinfo say direct rendering: No
client glx vendor string: ATI
OpenGL vendor string: Mesa

don't know what i can do
please helpme
tanks and bye,
francesco. this is my xorg.conf:

ection "Files"
FontPath "unix/:7100" # local font server
# if the local font server has problems, we can fall back on these
FontPath "/usr/lib/X11/fonts/misc"
FontPath "/usr/lib/X11/fonts/cyrillic"
FontPath "/usr/lib/X11/fonts/100dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/75dpi/:unscaled"
FontPath "/usr/lib/X11/fonts/Type1"
FontPath "/usr/lib/X11/fonts/CID"
FontPath "/usr/lib/X11/fonts/100dpi"
FontPath "/usr/lib/X11/fonts/75dpi"
# paths to defoma fonts
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
Load "dri"
Load "bitmap"
Load "dbe"
Load "ddc"
Load "glx"
# Load "extmod" but omit DGA extension - this must be included as is if you want to change resolution on the fly
SubSection "extmod"
Option "omit xfree86-dga"
EndSubSection
Load "freetype"
Load "int10"
Load "record"
Load "type1"
Load "vbe"
Load "GLcore"
EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "keyboard"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "it"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Driver "fglrx"
Option "UseInternalAGPGART" "no"
BusID "PCI:2:0:0"
Option "backingstore" "true"
# === Video Overlay for the Xv extension ===
Option "VideoOverlay" "yes"

# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
# will be disabled automatically
Option "OpenGLOverlay" "off"
# === Use internal AGP GART support? ===
# If OpenGL acceleration doesn't work, try using "yes" here
# and disable the kernel agpgart driver.

EndSection

Section "Monitor"
Identifier "CM715"
Option "DPMS"
EndSection



Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Radeon 9600 (R300 AP)"
Monitor "CM715"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

---

