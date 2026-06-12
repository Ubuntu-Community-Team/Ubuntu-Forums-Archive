---
title: "Anyone having problem staring Enemy Territory on Jaunty 64bit?"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by n3had on 2009-02-15
```
et
```

```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/tru3m0sl3m/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: cannot open shared object file: No such file or directory
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```


After some suggestion in other forums

```
et
```

gives this after it was asking for libGL.so.1 so i had to extract it from 32 bit nvidia drivers and place it in my installed folder

```
/home/tru3m0sl3m/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
**...loading libGL.so.1: Segmentation fault (core dumped)**

```

I've already installed 

```
sudo apt-get install ia32-libs*
```

I tried posting this in GAME LEISURE section.. No one is facing this problem.. So i posted over here. Hope this is not a double thread.

btw i used this tutorial to install [http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy](http://gaming.gwos.org/doku.php/guides:64bit:et_wolfenstein?s=enemy)

---

### Post by eyelessfade on 2009-02-15
Starts fine for me. 64bit Jaunty

---

### Post by n3had on 2009-02-15
> **eyelessfade said:**
> Starts fine for me. 64bit Jaunty

How did you install the game? Any link to the tutorial that you  used?

---

### Post by eyelessfade on 2009-02-15
nope. I just installed the 32bit libraries and then ran the installer. But I did it before I upgraded to Jaunty though. The 32bit libraries I have is:
```
ia32-libs
lib32asound2
lib32gcc1
lib32gomp1
lib32ncurses5
lib32nss-mdns
lib32stdc++6
lib32z1
libc6-i386
libc6-i386
libx86-1
```
I can remember I had some problems installing et, but I can't remember what :|

---

### Post by n3had on 2009-02-15
[QUOTE=eyelessfade;6737806]
```
ia32-libs
[i]lib32asound2
lib32gcc1
lib32gomp1
lib32ncurses5
lib32nss-mdns
lib32stdc++6
lib32z1
libc6-i386
libc6-i386
libx86-1[/i]
```

and install these via getlibs?

EDIT: Yes I've installed all now via apt-get

---

### Post by n3had on 2009-02-15
after installing libc6-i386 i get a different output

```
ET 2.60b linux-i386 May  8 2006
----- FS_Startup -----
Current search path:
/home/tru3m0sl3m/.etwolf/etmain
/usr/local/games/enemy-territory/etmain/pak2.pk3 (22 files)
/usr/local/games/enemy-territory/etmain/pak1.pk3 (10 files)
/usr/local/games/enemy-territory/etmain/pak0.pk3 (3725 files)
/usr/local/games/enemy-territory/etmain/mp_bin.pk3 (6 files)
/usr/local/games/enemy-territory/etmain

----------------------
3763 files in pk3 files
execing default.cfg
couldn't exec language.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
[color=red]**...loading libGL.so.1: QGL_Init: dlopen libGL.so.1 failed: libGL.so.1: wrong ELF class: ELFCLASS64**[/color]
failed
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem
```

---

### Post by rajeev1204 on 2009-02-15
Try deleting the hidden .et folder in home directory.Should work.

Also try sudo chown -R <username>:.et( or whatever the game folder is called)

---

### Post by n3had on 2009-02-15
> **rajeev1204 said:**
> Try deleting the hidden .et folder in home directory.Should work.

Also try sudo chown -R <username>:.et( or whatever the game folder is called)

thankyou bro but i've already done that..

---

### Post by taavikko on 2009-02-15
nvidia drivers aren't working for the moment.
there's a glitch with them.

---

### Post by n3had on 2009-02-15
tremeleus nuxuiz flight gear working fine... thank you for the input. Lets hope it gets fixed soon

---

### Post by Holmen on 2009-02-15
I algo get this error - Januty 32-bit.

---

### Post by int on 2009-02-16
Lots of games have the deb/tar to run on native 64bits..

---

### Post by eyelessfade on 2009-02-16
A simple google with your latest error gave me this:

try to start et with:  $LD_PRELOAD=/usr/lib/libGL.so.1 et

---

### Post by minisori on 2009-02-16
I was about to post the same bug. Here on 64 bits too and up to date, all games i've tried: WoP, tremullous and smooking guns give similar errors as the first pst mentioned, they used to work before latest nvidia drivers. I also noticed almost all metamodes are borked and you are not able to change screen resolution on external monitors, to a higher one.

> SDL_Init( SDL_INIT_VIDEO )... OK
Initializing OpenGL display
...setting mode 6: 1024 768
Couldn't get a visual
...WARNING: could not set the given mode (6)
Setting r_mode 6 failed, falling back on r_mode 3
Initializing OpenGL display
...setting mode 3: 640 480
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem


---

### Post by eyelessfade on 2009-02-16
I also have 64 bit. Here is from a successful start
```
----- Client Initialization Complete -----
----- R_Init -----                        
...loading libGL.so.1: Initializing OpenGL display
...setting mode -1: 1920 1200                     
Using XFree86-VidModeExtension Version 2.2        
XF86DGA Mouse (Version 2.0) initialized           
XFree86-VidModeExtension Activated at 1920x1200   
Using 4/4/4 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: GeForce 8800 GTS/PCI/SSE2              
Initializing OpenGL extensions                      
...using GL_S3_s3tc                                 
...ignoring GL_EXT_texture_env_add                  
...using GL_ARB_multitexture                        
...using GL_EXT_compiled_vertex_array               
...ignoring GL_NV_fog_distance                      
...ignoring GL_EXT_texture_filter_anisotropic       
Initializing GLX extensions                         
...using GLX_SGI_swap_control                       
...using GLX_SGI_video_sync                         
XF86 Gamma extension initialized                    

GL_VENDOR: NVIDIA Corporation
GL_RENDERER: GeForce 8800 GTS/PCI/SSE2
GL_VERSION: 3.0.0 NVIDIA 180.29       

```

Think I did a hack to get so high resolution, can't remember how though.

---

### Post by n3had on 2009-02-18
> **eyelessfade said:**
> A simple google with your latest error gave me this:

try to start et with:  $LD_PRELOAD=/usr/lib/libGL.so.1 et

i had done that before. I've updates my system after a week now. I'll reinstall the drivers now as the driver is somehow disabled.. will try to post later.

peace 

nehad


UPDATE: ET IS RUNNING FINE!!!!!! HURRAY ......
        It was a newbie error by me.. It had to with the incorrect installation of drivers.


THANKYOU EVERYONE MUAHHHHHH

---

