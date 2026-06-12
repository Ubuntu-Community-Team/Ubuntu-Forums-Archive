---
title: "openarena broken?"
date: 2009-02-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubulette on 2009-02-15
two days without openarena, i need my shot to stay productive ;)

It used to work fine, even for a day or two after the 0.7.7-1 -> 0.8.1-1 upgrade.
But it is now broken. I keep getting "Couldn't get a visual".

Anyone else seeing this?

I'm running:
nvidia-180-kernel-source       180.29-0ubuntu2
nvidia-180-libvdpau            180.29-0ubuntu2
nvidia-180-modaliases          180.29-0ubuntu2
nvidia-glx-180                 180.29-0ubuntu2
nvidia-settings                180.25-0ubuntu1
openarena                      0.8.1-1
openarena-data                 0.8.1-1

before you ask, yes, direct rendering is fine, i'm using nvidia and not nv, GLX is loaded.

Attached my X logs
Here are the errors from openarena:
```

----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 4: 800 600
Available modes: '1440x900 720x450 840x525 960x600 800x512 680x384 1360x768 960x540 320x240 400x300 416x312 512x384 576x432 640x480 800x600 832x624 1024x768 1152x864 640x512'
Couldn't get a visual
...WARNING: could not set the given mode (4)
Setting r_mode 4 failed, falling back on r_mode 3
Initializing OpenGL display
...setting mode 3: 640 480
Available modes: '1440x900 720x450 840x525 960x600 800x512 680x384 1360x768 960x540 320x240 400x300 416x312 512x384 576x432 640x480 800x600 832x624 1024x768 1152x864 640x512'
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

```

---

### Post by ubulette on 2009-02-15
answering to myself, it seems to be caused by the new libsdl1.2.

EDIT: yeah, confirmed in [Bug 328932]("https://bugs.launchpad.net/ubuntu/+source/libsdl1.2/+bug/328932")
EDIT 2: downgrading to [1.2.13-4ubuntu1]("https://launchpad.net/ubuntu/jaunty/+source/libsdl1.2/1.2.13-4ubuntu1") fixes it

---

### Post by autocrosser on 2009-02-16
Yes--I had the same issue with my old UT 2004---Grabbed the libsdl from the PPA in the bug report & I was back online fragging the young ones:P

---

### Post by techdude3177 on 2009-02-16
i downgraded and still get this error....

---

### Post by autocrosser on 2009-02-16
Goto the bug report & read about Michael Marley's PPA--He has a updated version of the libsdl that works--then---Link:  [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/%7Ethefirstm/+archive/ppa")

I'm using it with my old copy of UT2004 & it was what it took to get it fraggin' again!!!!!

---

### Post by techdude3177 on 2009-02-16
yea the PPA didnt work for me either

---

### Post by autocrosser on 2009-02-16
What are you having problems with?

---

### Post by techdude3177 on 2009-02-16
running openarena

$ openarena
ioq3+oa 1.35 linux-i386 Feb 12 2009
----- FS_Startup -----
Current search path:
/home/mine/.openarena/baseoa
/usr/share/games/openarena/baseoa/pak6-misc.pk3 (229 files)
/usr/share/games/openarena/baseoa/pak5-TA.pk3 (139 files)
/usr/share/games/openarena/baseoa/pak4-textures.pk3 (1753 files)
/usr/share/games/openarena/baseoa/pak2-players.pk3 (669 files)
/usr/share/games/openarena/baseoa/pak2-players-mature.pk3 (231 files)
/usr/share/games/openarena/baseoa/pak1-maps.pk3 (100 files)
/usr/share/games/openarena/baseoa/pak0.pk3 (1042 files)
/usr/share/games/openarena/baseoa

----------------------
4163 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
Couldn't read q3history.
Your network rate is too slow for VoIP.
Set 'Data Rate' to 'LAN/Cable/xDSL' in 'Setup/System/Network' and restart.
Until then, VoIP is disabled.
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL_Init( SDL_INIT_VIDEO ) FAILED (No available video device)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

edit: thats where i just notived that there is no video device.... how do i fix that?!
before i was getting the same error as ubulette

---

### Post by autocrosser on 2009-02-16
HMMMMMM--I'm not sure about that one--you might search Launchpad & do a Google search---what hardware are you using??  Desktop or Laptop?

---

### Post by techdude3177 on 2009-02-17
thats all i can do!
laptop with an intel graphics card

---

### Post by autocrosser on 2009-02-17
Well--there have been several problems with Intel graphics---I'm running nvidia--so I've done about what I can do....Dude--I'm only trying to help--don't get hot.

---

### Post by eyelessfade on 2009-02-17
what does the first few lines of glxinfo give you?

---

### Post by techdude3177 on 2009-02-17
i am not hot, guess my use of the "!" wasnt a good spot, just trying to figure this out. would be nice to play ya know, lol

glxinfo output

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

---

### Post by techdude3177 on 2009-02-27
So recently there was a intel driver update, so i ran "aptitude install gnome-devel" then reconfinguring and then compiling sdl fixed the error for me.
I am able to frag again! :guitar:

---

