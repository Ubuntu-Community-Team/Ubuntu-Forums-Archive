---
title: "Quake 3 Install"
date: 2006-02-24
forum: Installation &amp; Upgrades
---

### Post by R3linquish3r on 2006-02-24
Aight I've looked through alot of threads on here and other sites about this nd none of them answered it. I got the pak0.pk3 file transfered from my disk and im currently trying to install the point release for quake 3.

When I do
```
cd /home/ed/Desktop

sh linuxq3apoint-1.32b.x86.run
```

It opens a window asking for my root password. I put it in and click ok and the window just closes. I tried a secon time and instead of putting my password I clicked cancel. The point release install window opened but I couldn't click the install button. So I tried SU ROOT and to run the realease in that fashion and I got the following error:

```
root@ubuntu:/home/ed/Desktop# sh linuxq3apoint-1.32b.x86.run
Verifying archive integrity... All good.
Uncompressing Quake III Arena Point Release 1.32b ...................................................................................................................................................
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

No UI drivers available
./setup.sh: line 96: 10993 Segmentation fault      "$setup" "$@" 2>/dev/null
The setup program seems to have failed on x86/glibc-2.1

Please contact Id software technical support at bugs@idsoftware.com, or ttimo@idsoftware.com
The program returned an error code (1)
```

Any suggestions would be awesome.

---

### Post by R3linquish3r on 2006-02-24
bumps..... no one has any ideas?

---

### Post by gord on 2006-02-24
have you tried
```

sudo ./linuxq3apoint-1.32b.x86.run

```

---

### Post by R3linquish3r on 2006-02-24
```
ed@ubuntu:~/Desktop$ sudo ./linuxq3apoint-1.32b.x86.run
sudo: ./linuxq3apoint-1.32b.x86.run: command not found
ed@ubuntu:~/Desktop$
```

Any other ideas?

---

### Post by gord on 2006-02-24
make sure the file is in the directory you are in, and make sure that its permitions are set to executionable
```

chmod +x linuxq3apoint-1.32b.x86.run

```

then try sudo

---

### Post by R3linquish3r on 2006-02-24
That didd it man. THanks alot for the help on that :)

---

### Post by R3linquish3r on 2006-02-24
Ok new problem :P

I go to run the game and I get this error:

```
ed@ubuntu:~$ quake3
Q3 1.32b linux-i386 Nov 14 2002
----- FS_Startup -----
Current search path:
/home/ed/.q3a/baseq3
/usr/local/games/quake3/baseq3/pak8.pk3 (9 files)
/usr/local/games/quake3/baseq3/pak7.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak6.pk3 (64 files)
/usr/local/games/quake3/baseq3/pak5.pk3 (7 files)
/usr/local/games/quake3/baseq3/pak4.pk3 (272 files)
/usr/local/games/quake3/baseq3/pak3.pk3 (4 files)
/usr/local/games/quake3/baseq3/pak2.pk3 (148 files)
/usr/local/games/quake3/baseq3/pak1.pk3 (26 files)
/usr/local/games/quake3/baseq3/pak0.pk3 (3539 files)
/usr/local/games/quake3/baseq3
./quake3.x86/baseq3

----------------------
4073 files in pk3 files
execing default.cfg
couldn't exec q3config.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 3: 640 480
Using XFree86-VidModeExtension Version 2.2
XF86DGA Mouse (Version 2.0) initialized
XFree86-VidModeExtension Activated at 640x480
Using 8/8/8 Color bits, 16 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (3)
----- CL_Shutdown -----
RE_Shutdown( 1 )
-----------------------
----- CL_Shutdown -----
-----------------------
Sys_Error: GLimp_Init() - could not load OpenGL subsystem

```

---

### Post by R3linquish3r on 2006-02-25
bump

---

### Post by R3linquish3r on 2006-02-25
ight i found the problem. just had to update my drivers :)

---

