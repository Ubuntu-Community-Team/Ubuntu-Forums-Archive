---
title: "Gnome 2.27.3 snappy and fast"
date: 2009-06-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Regenweald on 2009-06-16
Feeling speed improvements in moving around the desktop and graphics feel sharper. Anyone experiencing regressions yet ? For some reason this development cycle does not give me the feeling that there will be show stopping breakage.

---

### Post by zekopeko on 2009-06-16
> **Regenweald said:**
> Feeling speed improvements in moving around the desktop and graphics feel sharper. Anyone experiencing regressions yet ? For some reason this development cycle does not give me the feeling that there will be show stopping breakage.

i got that from jaunty. before i was rather reluctant with testing dev builds.

---

### Post by Regenweald on 2009-06-16
Actually for me, Jaunty dev was faster than Jaunty final. I guess with the final a few holes were plugged or processes added/changed and i saw slight regression in speed. Example: If I'd go places>>any drive, the screen would take 2-4 seconds to load and pop up. In karmic dev it's a fraction of a second. Think it's due to the -30 Kernel. I don't think i can do the six month thing anymore.

Ignore the cycle, make Ubuntu your own personal rolling release kids!
(said the suspicious looking man....)

---

### Post by super.rad on 2009-06-16
I've got fedora and ubuntu installed, at the moment fedora is on 11 but in a month or so once ubuntu starts becoming a bit boring i'll switch to using this as my stable(ish) system and upgrade to fedora 12 testing, keeps me from getting bored as I always have at least 1 testing version to try and break

---

### Post by Regenweald on 2009-06-16
> **super.rad said:**
> I've got fedora and ubuntu installed, at the moment fedora is on 11 but in a month or so once ubuntu starts becoming a bit boring i'll switch to using this as my stable(ish) system and upgrade to fedora 12 testing, keeps me from getting bored as I always have at least 1 testing version to try and break

Yeah, Fed12 testing should be exciting :) How is Palimpsest in Fed11 ? I see it in the karmic repos but haven't installed it yet. Should be a nice addition to 9.10

---

### Post by Nullack on 2009-06-17
Performance of gnome seems subjectively about the same for my test system with the NVIDIA 185.18.14 driver.

---

### Post by plun on 2009-06-17
For me its a little faster with the new GTK version

glxdragon has for a long time been around 115 fps and now its
around 120 fps on my system.;)

```
plun@plun:~/glxdragon$ ./glxdragon
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600 GT/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 185.18.14

1.5 seconds for 180 frames = 120.0 FPS
1.5 seconds for 180 frames = 120.0 FPS
1.5 seconds for 180 frames = 120.0 FPS
1.5 seconds for 180 frames = 120.8 FPS
1.5 seconds for 180 frames = 118.4 FPS
1.5 seconds for 180 frames = 120.0 FPS
1.5 seconds for 180 frames = 120.8 FPS
1.5 seconds for 180 frames = 119.2 FPS

```

---

### Post by davideotape on 2009-06-17
> **plun said:**
> For me its a little faster with the new GTK version

glxdragon has for a long time been around 115 fps and now its
around 120 fps on my system.;)
[/CODE]

May I ask whereabouts I can get glxdragon? It doesn't seem to be in the repos.

---

### Post by plun on 2009-06-17
> **davideotape said:**
> May I ask whereabouts I can get glxdragon? It doesn't seem to be in the repos.

No, you can get it from Launchpad

[https://launchpad.net/glxdragon](https://launchpad.net/glxdragon)

---

### Post by super.rad on 2009-06-17
Still missing quite a lot from gnome 2.27.3, the important bits for me are empathy and epiphany-webkit both of which are still on 2.27.2

---

### Post by Gourgi on 2009-06-17
> **plun said:**
> No, you can get it from Launchpad

[https://launchpad.net/glxdragon](https://launchpad.net/glxdragon)
**Edit** : _forget it_! 
installing **libsdl** fixed my problem


i get build errors with glxdragon

```

$ make
gcc -O2 -Wall -I/usr/include/SDL -o glxdragon glxdragon.cpp -lSDL -lGL -lGLU
glxdragon.cpp:28:17: error: SDL.h: No such file or directory
glxdragon.cpp:29:24: error: SDL_opengl.h: No such file or directory
glxdragon.cpp: In function &#8216;void init(int, int, const std::string&)&#8217;:
glxdragon.cpp:55: error: &#8216;SDL_INIT_VIDEO&#8217; was not declared in this scope
glxdragon.cpp:55: error: &#8216;SDL_Init&#8217; was not declared in this scope
glxdragon.cpp:57: error: &#8216;SDL_GetError&#8217; was not declared in this scope
glxdragon.cpp:63: error: &#8216;SDL_GL_RED_SIZE&#8217; was not declared in this scope
glxdragon.cpp:63: error: &#8216;SDL_GL_SetAttribute&#8217; was not declared in this scope
glxdragon.cpp:64: error: &#8216;SDL_GL_GREEN_SIZE&#8217; was not declared in this scope
glxdragon.cpp:65: error: &#8216;SDL_GL_BLUE_SIZE&#8217; was not declared in this scope
glxdragon.cpp:66: error: &#8216;SDL_GL_DEPTH_SIZE&#8217; was not declared in this scope
glxdragon.cpp:67: error: &#8216;SDL_GL_DOUBLEBUFFER&#8217; was not declared in this scope
glxdragon.cpp:70: error: &#8216;SDL_WM_SetCaption&#8217; was not declared in this scope
glxdragon.cpp:73: error: &#8216;SDL_OPENGL&#8217; was not declared in this scope
glxdragon.cpp:73: error: &#8216;SDL_SetVideoMode&#8217; was not declared in this scope
glxdragon.cpp:75: error: &#8216;SDL_GetError&#8217; was not declared in this scope
glxdragon.cpp:81: error: &#8216;GL_VENDOR&#8217; was not declared in this scope
glxdragon.cpp:81: error: &#8216;glGetString&#8217; was not declared in this scope
glxdragon.cpp:82: error: &#8216;GL_RENDERER&#8217; was not declared in this scope
glxdragon.cpp:83: error: &#8216;GL_VERSION&#8217; was not declared in this scope
glxdragon.cpp:89: error: &#8216;glViewport&#8217; was not declared in this scope
glxdragon.cpp:91: error: &#8216;GL_PROJECTION&#8217; was not declared in this scope
glxdragon.cpp:91: error: &#8216;glMatrixMode&#8217; was not declared in this scope
glxdragon.cpp:92: error: &#8216;glLoadIdentity&#8217; was not declared in this scope
glxdragon.cpp:94: error: &#8216;GLfloat&#8217; was not declared in this scope
glxdragon.cpp:94: error: &#8216;gluPerspective&#8217; was not declared in this scope
glxdragon.cpp:96: error: &#8216;GL_MODELVIEW&#8217; was not declared in this scope
glxdragon.cpp:101: error: &#8216;GL_CULL_FACE&#8217; was not declared in this scope
glxdragon.cpp:101: error: &#8216;glEnable&#8217; was not declared in this scope
glxdragon.cpp:104: error: &#8216;GL_SMOOTH&#8217; was not declared in this scope
glxdragon.cpp:104: error: &#8216;glShadeModel&#8217; was not declared in this scope
glxdragon.cpp:107: error: &#8216;GL_DEPTH_TEST&#8217; was not declared in this scope
glxdragon.cpp:110: error: &#8216;glClearDepth&#8217; was not declared in this scope
glxdragon.cpp:113: error: &#8216;GL_LEQUAL&#8217; was not declared in this scope
glxdragon.cpp:113: error: &#8216;glDepthFunc&#8217; was not declared in this scope
glxdragon.cpp:116: error: &#8216;GL_VERTEX_ARRAY&#8217; was not declared in this scope
glxdragon.cpp:116: error: &#8216;glEnableClientState&#8217; was not declared in this scope
glxdragon.cpp:117: error: &#8216;GL_NORMAL_ARRAY&#8217; was not declared in this scope
glxdragon.cpp:120: error: &#8216;GL_PERSPECTIVE_CORRECTION_HINT&#8217; was not declared in this scope
glxdragon.cpp:120: error: &#8216;GL_NICEST&#8217; was not declared in this scope
glxdragon.cpp:120: error: &#8216;glHint&#8217; was not declared in this scope
glxdragon.cpp: In function &#8216;void initScene()&#8217;:
glxdragon.cpp:126: error: &#8216;GL_COLOR_MATERIAL&#8217; was not declared in this scope
glxdragon.cpp:126: error: &#8216;glEnable&#8217; was not declared in this scope
glxdragon.cpp:128: error: &#8216;GL_FRONT&#8217; was not declared in this scope
glxdragon.cpp:128: error: &#8216;GL_AMBIENT_AND_DIFFUSE&#8217; was not declared in this scope
glxdragon.cpp:128: error: &#8216;glColorMaterial&#8217; was not declared in this scope
glxdragon.cpp:129: error: &#8216;GL_SHININESS&#8217; was not declared in this scope
glxdragon.cpp:129: error: &#8216;glMateriali&#8217; was not declared in this scope
glxdragon.cpp:132: error: &#8216;GL_SPECULAR&#8217; was not declared in this scope
glxdragon.cpp:132: error: &#8216;glMaterialfv&#8217; was not declared in this scope
glxdragon.cpp:135: error: &#8216;GL_LIGHT0&#8217; was not declared in this scope
glxdragon.cpp:138: error: &#8216;GLfloat&#8217; was not declared in this scope
glxdragon.cpp:138: error: expected `;' before &#8216;ambient&#8217;
glxdragon.cpp:139: error: expected `;' before &#8216;diffuse&#8217;
glxdragon.cpp:140: error: expected `;' before &#8216;specular&#8217;
glxdragon.cpp:141: error: expected `;' before &#8216;position&#8217;
glxdragon.cpp:144: error: &#8216;GL_AMBIENT&#8217; was not declared in this scope
glxdragon.cpp:144: error: &#8216;ambient&#8217; was not declared in this scope
glxdragon.cpp:144: error: &#8216;glLightfv&#8217; was not declared in this scope
glxdragon.cpp:145: error: &#8216;GL_DIFFUSE&#8217; was not declared in this scope
glxdragon.cpp:145: error: &#8216;diffuse&#8217; was not declared in this scope
glxdragon.cpp:146: error: &#8216;specular&#8217; was not declared in this scope
glxdragon.cpp:147: error: &#8216;GL_POSITION&#8217; was not declared in this scope
glxdragon.cpp:147: error: &#8216;position&#8217; was not declared in this scope
glxdragon.cpp:150: error: &#8216;gluLookAt&#8217; was not declared in this scope
glxdragon.cpp: In function &#8216;void done()&#8217;:
glxdragon.cpp:156: error: &#8216;SDL_Quit&#8217; was not declared in this scope
glxdragon.cpp: In function &#8216;void drawModelVA(const Mesh&)&#8217;:
glxdragon.cpp:164: error: &#8216;GL_MAX_ELEMENTS_INDICES&#8217; was not declared in this scope
glxdragon.cpp:164: error: &#8216;glGetIntegerv&#8217; was not declared in this scope
glxdragon.cpp:167: error: &#8216;GL_FLOAT&#8217; was not declared in this scope
glxdragon.cpp:167: error: &#8216;glVertexPointer&#8217; was not declared in this scope
glxdragon.cpp:168: error: &#8216;glNormalPointer&#8217; was not declared in this scope
glxdragon.cpp:175: error: &#8216;GL_TRIANGLES&#8217; was not declared in this scope
glxdragon.cpp:175: error: &#8216;GL_UNSIGNED_INT&#8217; was not declared in this scope
glxdragon.cpp:175: error: &#8216;glDrawElements&#8217; was not declared in this scope
glxdragon.cpp: In function &#8216;bool paintGL()&#8217;:
glxdragon.cpp:182: error: &#8216;GL_DEPTH_BUFFER_BIT&#8217; was not declared in this scope
glxdragon.cpp:182: error: &#8216;glClear&#8217; was not declared in this scope
glxdragon.cpp:185: error: &#8216;GL_PROJECTION&#8217; was not declared in this scope
glxdragon.cpp:185: error: &#8216;glMatrixMode&#8217; was not declared in this scope
glxdragon.cpp:186: error: &#8216;glPushMatrix&#8217; was not declared in this scope
glxdragon.cpp:187: error: &#8216;glLoadIdentity&#8217; was not declared in this scope
glxdragon.cpp:189: error: &#8216;glOrtho&#8217; was not declared in this scope
glxdragon.cpp:191: error: &#8216;GL_MODELVIEW&#8217; was not declared in this scope
glxdragon.cpp:196: error: &#8216;GL_DEPTH_TEST&#8217; was not declared in this scope
glxdragon.cpp:196: error: &#8216;glDisable&#8217; was not declared in this scope
glxdragon.cpp:197: error: &#8216;GL_LIGHTING&#8217; was not declared in this scope
glxdragon.cpp:200: error: &#8216;GL_QUADS&#8217; was not declared in this scope
glxdragon.cpp:200: error: &#8216;glBegin&#8217; was not declared in this scope
glxdragon.cpp:202: error: &#8216;glColor3ub&#8217; was not declared in this scope
glxdragon.cpp:203: error: &#8216;glVertex2f&#8217; was not declared in this scope
glxdragon.cpp:210: error: &#8216;glEnd&#8217; was not declared in this scope
glxdragon.cpp:215: error: &#8216;glPopMatrix&#8217; was not declared in this scope
glxdragon.cpp:221: error: &#8216;glEnable&#8217; was not declared in this scope
glxdragon.cpp:226: error: &#8216;glColor3ub&#8217; was not declared in this scope
glxdragon.cpp:232: error: &#8216;SDL_GL_SwapBuffers&#8217; was not declared in this scope
glxdragon.cpp:239: error: &#8216;glRotatef&#8217; was not declared in this scope
glxdragon.cpp: In function &#8216;void runEventLoop()&#8217;:
glxdragon.cpp:252: error: &#8216;SDL_Event&#8217; was not declared in this scope
glxdragon.cpp:252: error: expected `;' before &#8216;event&#8217;
glxdragon.cpp:254: error: &#8216;event&#8217; was not declared in this scope
glxdragon.cpp:254: error: &#8216;SDL_PollEvent&#8217; was not declared in this scope
glxdragon.cpp:256: error: &#8216;SDL_QUIT&#8217; was not declared in this scope
make: *** [glxdragon] Error 1


```
PS sorry being off-topic

---

### Post by Joe_Bishop on 2009-06-17
It's written in c++, try g++ instead

---

### Post by Joe_Bishop on 2009-06-17
sudo aptitude install libsdl-dev

---

