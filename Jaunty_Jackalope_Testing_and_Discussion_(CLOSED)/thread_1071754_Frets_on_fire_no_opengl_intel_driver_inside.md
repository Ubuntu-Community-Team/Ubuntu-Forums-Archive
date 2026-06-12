---
title: "Frets on fire no opengl intel driver inside?"
date: 2009-02-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Taiebot65 on 2009-02-16
I can not play to frets on fire because of opengl ?is it a bug or only related to my config.

```
 fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 68, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 69, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: X11 driver not configured with OpenGL
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 85, in apport_excepthook
    os.O_WRONLY|os.O_CREAT|os.O_EXCL), 'w')
OSError: [Errno 17] File exists: '/var/crash/_usr_share_games_fretsonfire_game_FretsOnFire.py.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "./FretsOnFire.py", line 68, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 69, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: X11 driver not configured with OpenGL

```

---

### Post by Taiebot65 on 2009-02-16
Well i do think it s a bug with x because even extreme tux racer is not working..

```
 etracer
Extreme TuxRacer SVN Development --  http://www.extremetuxracer.com 
(c) 2007 The ETRacer team
(c) 2004-2005 The PPRacer team
(c) 1999-2001 Jasmin F. Patry<jfpatry@sunspirestudios.com>
ETRacer comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to redistribute it under certain conditions.
See http://www.gnu.org/copyleft/gpl.html for details.

*** etracer error: Couldn't initialize video: X11 driver not configured with OpenGL (Resource temporarily unavailable)

```

---

### Post by Taiebot65 on 2009-02-16
Well all my games with opengl are not working...

```
taiebot@home:~$ openarena
ioq3+oa 1.35 linux-i386 Feb 12 2009
----- FS_Startup -----
Current search path:
/home/taiebot/.openarena/baseoa
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
execing q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
QKEY found.
----- Client Initialization Complete -----
----- R_Init -----
SDL using driver "x11"
Initializing OpenGL display
Estimated display aspect: 1.600
...setting mode 6: 1024 768
Available modes: '1280x800 640x400 720x400 640x350 640x480 800x600 832x624 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (6)
Setting r_mode 6 failed, falling back on r_mode 3
Initializing OpenGL display
...setting mode 3: 640 480
Available modes: '1280x800 640x400 720x400 640x350 640x480 800x600 832x624 1024x768'
Couldn't get a visual
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
GLimp_Init() - could not load OpenGL subsystem

```

---

### Post by autocrosser on 2009-02-16
Look at the OpenArena thread--the problem is the last release of libsdl--it has no GL support built-in.....

---

### Post by Taiebot65 on 2009-02-17
Yep thanks i ve added the ppa and it s working [https://launchpad.net/~thefirstm/+archive/ppa]("https://launchpad.net/~thefirstm/+archive/ppa")

---

### Post by techdude3177 on 2009-02-17
what intel driver are you using? i added the PPA and it doesnt work for me.

---

### Post by Taiebot65 on 2009-02-18
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

I ve enabled UXA in my xorg as well i had big problems with performance.

---

