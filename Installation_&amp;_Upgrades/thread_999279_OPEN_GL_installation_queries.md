---
title: "OPEN GL installation queries"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by sundararajan on 2008-12-01
Hi guys
I have a problem getting OpenGl to work on my laptop. My laptop has a nvidia card. The output of glxinfo command is

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4


I tried glx gears and it works perfectly fine. 

I have been trying to develop a few things using Open gl and when I try compiling my scons script for the program I get the following error

scons: Reading SConscript files ...
Building for OS  posix
Setting Linux specific flags
scons: done reading SConscript files.
scons: Building targets ...
g++ -o SDLOpenGL -Wl,-Bsymbolic-functions SDLOpenGL.o -L/usr/lib -L/usr/lib/X11 -L/usr/lib -L/usr/X11R6/lib -lSDL -lpthread -lfreetype -lz -lMagick++ -lWand -lMagick -lSDL_mixer
SDLOpenGL.o: In function `FunctionPlot(int, int)':
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:45: undefined reference to `glClear'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:47: undefined reference to `glBegin'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:51: undefined reference to `glVertex2d'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:51: undefined reference to `glVertex2d'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:53: undefined reference to `glEnd'
SDLOpenGL.o: In function `MyGLInit(int, int)':
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:27: undefined reference to `glClearColor'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:28: undefined reference to `glColor3f'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:29: undefined reference to `glPointSize'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:31: undefined reference to `glMatrixMode'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:32: undefined reference to `glLoadIdentity'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:33: undefined reference to `gluOrtho2D'
/home/sundar/Desktop/SDLLecture/DotPlot/SDLOpenGL.cpp:34: undefined reference to `glMatrixMode'
collect2: ld returned 1 exit status
scons: *** [SDLOpenGL] Error 1
scons: building terminated because of errors.

Can anyone help me with this problem

---

