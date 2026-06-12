---
title: "Compiling TuxRacer 0.61 on Feisty"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Steven_B on 2007-07-07
I'm trying to install Tuxracer 0.61 (the last GPL'd version) from source.  I don't want to install PlanetPenguin Racer - I want to work with the original Tuxracer source code.  I've downloaded the source tarball from tuxracer.sourceforge.net.   When I try ./configure, I get:
```

checking for GL library... yes
checking for glXGetProcAddressARB... yes
checking for GLU library... yes
checking for GL/gl.h... yes
checking for GL/glx.h... yes
checking whether glx.h defines glXGetProcAddressARB... no
configure: error: Your copy of glx.h is out of date.  You can get a more recent copy from the latest Mesa distribution (http://mesa3d.sourceforge.net).

```
I doubt that my glx.h is out of date, since the tuxracer code is 5+ years older than my version of mesa. ;)
Any ideas on how to fix this?

---

### Post by zach12 on 2007-07-07
i've tryed to install tuxracer too and have had that (i think)error message too

---

### Post by m10 on 2007-09-29
same here :(

---

### Post by noamh on 2007-10-06
I actually managed to get passed this error (and another one after it by running:

```
./configure --with-tcl-inc=/usr/include/tcl8.4 --with-tcl-lib-name=tcl8.4 --with-gl-inc=/usr/share/doc/nvidia-glx-new-dev/include
```


However, the next error is:

```
checking for sdl-config... no
checking for SDL - version >= 1.0.1... no
*** The sdl-config script installed by SDL could not be found
*** If SDL was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the SDL_CONFIG environment variable to the
*** full path to sdl-config.
*** SDL not found.  Configuring without audio or joystick support.
checking for GL library... yes
checking for glXGetProcAddressARB... yes
checking for GLU library... yes
checking for GL/gl.h... yes
checking for GL/glx.h... yes
checking whether glx.h defines glXGetProcAddressARB... yes
checking for GL/glext.h... yes
checking whether glext.h is recent enough... yes
checking for glut library... no
checking for glut32 library... no
configure: error: GLUT library not found or too old version. 3.7 (beta) or later required (or install SDL instead).

```


Any ideas ?

---

### Post by runemaste644 on 2007-10-07
I need to install Mesa to run it onLinux. It runs fine on Windaz though

---

### Post by Steven_B on 2007-10-15
@noamh
What version of GLUT do you have installed?  For me, it configured correctly with only freeglut3 and libglut3 installed.

When I type make, it spews out a zillion errors about game_config.c:
```
game_config.c:798:1: error: pasting "." and "write_diagnostic_log" does not give a valid preprocessing token
game_config.c:798:1: error: pasting "write_diagnostic_log" and "." does not give a valid preprocessing token
game_config.c:798:1: error: pasting "." and "write_diagnostic_log" does not give a valid preprocessing token
game_config.c:798:1: error: pasting "." and "write_diagnostic_log" does not give a valid preprocessing token
game_config.c:798:1: error: pasting "write_diagnostic_log" and "." does not give a valid preprocessing token
game_config.c:798:1: error: pasting "." and "bool" does not give a valid preprocessing token
game_config.c:798:1: error: pasting "." and "write_diagnostic_log" does not give a valid preprocessing token

```
This is just the errors for line 798.  There are an equivalent set of errors for each line 735-798.

---

### Post by Steven_B on 2007-10-15
I was able to fix the compile errors by modifying game_config.c  The modified file is attached.  Just extract the .c file and put it into the src folder.

---

