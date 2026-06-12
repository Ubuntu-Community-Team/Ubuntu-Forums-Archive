---
title: "GLX Dragon"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by TrueTom on 2009-03-29
A lot of people use [FONT="Courier New"]glxgears[/FONT] as cheap benchmark. Unfortunately it does a pretty bad job as such since the displayed scene has an extremely low poly count. Therefore I've put some code together that creates a bit more of a challenge for your graphics card (foremost for integrated chips) by rendering the [Stanford dragon]("http://www-graphics.stanford.edu/data/3Dscanrep/").

This still isn't a comprehensive benchmark but at least the results don't just represent SwapBuffer performance. I've also included a version compiled for Windows, so if you happen to have a dual boot system you can check how much Linux is slower... ;)

```

# Required packages for building
sudo apt-get install build-essential libsdl1.2-dev libgl1-mesa-dev libglu1-mesa-dev

# Actually build the program
make

# Run it
./glxdragon
```


**Linux version**
Since putting the code on some random file hoster proved to be somewhat unreliable, I've uploaded the code on Launchpad. You can get a copy with: ```
bzr branch lp:glxdragon
```

**Windows version**
TBD

---

### Post by TrueTom on 2009-03-29
In case you are wondering about the state of the Intel OpenGl stack in Linux:

**Windows**
```
GL_VENDOR   : Intel
GL_RENDERER : Intel 945GM
GL_VERSION  : 1.4.0 - Build 7.14.10.4926

12.1 seconds for 180 frames = 14.9 FPS
```

**Linux**
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090114 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.3

37.8 seconds for 180 frames = 4.8 FPS
```

---

### Post by jerrylamos on 2009-03-29
Well, ran the directions for making glxdragon and got:

make: *** No targets specified and no makefile found.  Stop.

?

Thanks, Jerry

---

### Post by TrueTom on 2009-03-29
I looked at your attachment but couldn't figure out what you were doing (especially where 'glxdragonmake' is comming from).

Here is what you have to to:

1) Download the linux version to your desktop
2) Right-click on it and select 'Extract here'
3) You should get a folder called 'glxdragon'
4) Open a terminal and type 'cd ~/Desktop/glxdragon'
5) Type 'make'
6) Type './glxdragon'

---

### Post by knarf on 2009-03-29
In the race to the bottom I guess the blistering speed of my T23's SuperSavage will do quite well:

GL_VENDOR   : S3 Graphics Inc.
GL_RENDERER : Mesa DRI SuperSavage 20061110 AGP 4x x86/MMX/SSE
GL_VERSION  : 1.2 Mesa 7.3

75.4 seconds for 180 frames = 2.4 FPS

For comparison here's the results with 3D accelleration turned off (using driconf):

GL_VENDOR   : S3 Graphics Inc.
GL_RENDERER : Mesa DRI SuperSavage 20061110 AGP 4x x86/MMX/SSE
GL_VERSION  : 1.2 Mesa 7.3

107.7 seconds for 180 frames = 1.7 FPS

These results were achieved with a 1.2 GHz PIII-m (my main machine :-)

---

### Post by autocrosser on 2009-03-29
Interesting---My system: i7-920 Gigabyte GA-EX58-UD4P running @ 3.3 - SLI (auto setting) with matched pair 9500GT-512mb DDR2 cards.

Glxgears:

dean@linux:~/Desktop$ glxgears
37681 frames in 5.0 seconds = 7528.610 FPS
38150 frames in 5.0 seconds = 7626.550 FPS
37839 frames in 5.0 seconds = 7567.715 FPS
38078 frames in 5.0 seconds = 7615.512 FPS
38094 frames in 5.0 seconds = 7618.706 FPS
38163 frames in 5.0 seconds = 7632.507 FPS
38057 frames in 5.0 seconds = 7611.340 FPS
37959 frames in 5.0 seconds = 7591.686 FPS
36956 frames in 5.0 seconds = 7388.477 FPS
38098 frames in 5.0 seconds = 7619.540 FPS
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 71 requests (71 known processed) with 0 events remaining.

Glxdragon:

dean@linux:~/Desktop$ cd '/home/dean/Desktop/glxdragon' 
dean@linux:~/Desktop/glxdragon$ ./glxdragon
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 9500 GT/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.37

0.8 seconds for 180 frames = 236.8 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 250.0 FPS
0.7 seconds for 180 frames = 268.7 FPS
0.7 seconds for 180 frames = 257.1 FPS
0.7 seconds for 180 frames = 253.5 FPS
0.7 seconds for 180 frames = 260.9 FPS
0.7 seconds for 180 frames = 264.7 FPS


So the sample time is different--if I multiply by 7.14 (diff between 5 & .7), I get 1835.694 FPS per 5 sec.

Very interesting.........How hard would it be to instead of defining the number of frames for the sample, do the same as glxgears & define the time of the sample?

---

### Post by TrueTom on 2009-03-30
knarf: I tried the Mesa SW rasterizer and it isn't really slower. The Intel Linux driver is basically just waiting for Larabee.

autocrosser: It's not really a technical issue but necessary to make the results comparable. The obvious downside is that for fast video cards the accuracy of the results suffers. Please note that FPS always means FPS, though.

I rebuild the mesa package and optimised it for my laptop, gives 6% improvement for free, but still... ;) 

**Jaunty Default Package**
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090114 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.3

37.8 seconds for 180 frames = 4.8 FPS
```

**Optimized Mesa Package:**
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090114 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.3

35.6 seconds for 180 frames = 5.1 FPS
```

---

### Post by knarf on 2009-03-30
TrueTom: I'm not using Intel graphics, this is a veritable S3 SuperSavage IX/C SDR (rev 05) with a whopping 16 MB of (dedicated) RAM. I does not do fancy stuff like compiz or, generally, anything fancy at all...

---

### Post by TrueTom on 2009-03-31
> **knarf said:**
> TrueTom: I'm not using Intel graphics, this is a veritable S3 SuperSavage IX/C SDR (rev 05) with a whopping 16 MB of (dedicated) RAM. I does not do fancy stuff like compiz or, generally, anything fancy at all...

That is just adding insult to the Intel driver. I've done some profiling to see if there is some obvious performance hog, but the results are somewhat inconclusive. Though, there is a lot of copying going on in the kernel, that doesn't seem necessary. I'm still trying to get some callgraph data to make more sense out of it.

```
samples  %        image name                 symbol name
180897   41.6826  vmlinux-2.6.28-11-generic  __copy_from_user_ll_nocache_nozero
64749    14.9196  libc-2.9.so                memcpy
50006    11.5225  i915_dri.so                vbo_split_copy
23327     5.3750  i915_dri.so                light_fast_rgba_single
21305     4.9091  i915_dri.so                intel_render_triangles_elts
14474     3.3351  i915_dri.so                mesa_x86_cliptest_points4
12413     2.8602  glxdragon                  (no symbols)
9483      2.1851  i915_dri.so                _mesa_sse_transform_points3_general
7496      1.7272  vmlinux-2.6.28-11-generic  __copy_to_user_ll
5895      1.3583  i915_dri.so                intel_get_prim_space
4770      1.0991  i915_dri.so                vbo_exec_DrawElements
4711      1.0855  i915_dri.so                vbo_rebase_prims
```

---

### Post by TrueTom on 2009-04-05
In case someone cares for the code, I've uploaded it on Launchpad: [http://launchpad.net/glxdragon]("http://launchpad.net/glxdragon")

---

### Post by smbm on 2009-04-05
I get:

```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2
GL_VERSION  : 2.0 Mesa 7.4

52.1 seconds for 180 frames = 3.5 FPS

```

---

### Post by skullmunky on 2009-04-05
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : Quadro FX 1400/PCI/SSE2/3DNOW!
GL_VERSION  : 2.1.2 NVIDIA 169.12
0.6 seconds for 180 frames = 281.2 FPS

---

### Post by klange on 2009-04-05
```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GM GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.4

38.5 seconds for 180 frames = 4.7 FPS
```
DRI2/UXA.

---

### Post by ronacc on 2009-04-05
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 7600 GS/PCI/SSE2
GL_VERSION  : 2.1.2 NVIDIA 180.44

2.5 seconds for 180 frames = 71.4 FPS

---

### Post by smbm on 2009-04-06
With UXA enabled I get:

```
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 965GM GEM 20090326 2009Q1 RC2
GL_VERSION  : 2.0 Mesa 7.4

48.8 seconds for 180 frames = 3.7 FPS

```

---

### Post by Darkshade on 2009-04-06
```
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 6800 XT/AGP/SSE2/3DNOW!
GL_VERSION  : 2.1.2 NVIDIA 180.44
```

With compiz on:
```
3.3 seconds for 180 frames = 55.2 FPS
```

With compiz off:
```
2.9 seconds for 180 frames = 62.5 FPS
```

---

### Post by plun on 2009-04-06
Intel 5200 and a 8600GT nVidia card

> plun@plun:~/glxdragon$ ./glxdragon
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8600 GT/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.44

1.8 seconds for 180 frames = 102.9 FPS
1.7 seconds for 180 frames = 107.8 FPS
1.9 seconds for 180 frames = 94.7 FPS
1.7 seconds for 180 frames = 107.8 FPS


---

### Post by GenPFault on 2009-04-07
Core i7 920, with the 640MB 8800GTS variant.

```

GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 8800 GTS/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 180.44

```

Compiz off:
```

1.1 seconds for 180 frames = 160.7 FPS
1.1 seconds for 180 frames = 160.7 FPS

```

Compiz on:
```

1.3 seconds for 180 frames = 138.5 FPS
1.3 seconds for 180 frames = 139.5 FPS

```

---

### Post by jbernardo on 2009-04-08
Aspire One (intel 945 GME), EXA, KDE 4.2 with composite on:

```
./glxdragon
get fences failed: -1
param: 6, val: 0
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GME GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.4

73.9 seconds for 180 frames = 2.4 FPS
70.6 seconds for 180 frames = 2.5 FPS
73.6 seconds for 180 frames = 2.4 FPS

```

With composite disabled:
```
./glxdragon
get fences failed: -1
param: 6, val: 0
GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GME GEM 20090326 2009Q1 RC2 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.4

60.2 seconds for 180 frames = 3.0 FPS
58.7 seconds for 180 frames = 3.1 FPS
58.7 seconds for 180 frames = 3.1 FPS
```

---

### Post by Polygon on 2009-04-08
i like this better then glxgears =)

mark@Humboldti:~/svn/glxdragon$ ./glxdragon 
GL_VENDOR   : NVIDIA Corporation
GL_RENDERER : GeForce 9800 GTX/9800 GTX+/PCI/SSE2
GL_VERSION  : 3.0.0 NVIDIA 185.13

0.8 seconds for 180 frames = 211.8 FPS
0.8 seconds for 180 frames = 227.8 FPS
0.9 seconds for 180 frames = 200.0 FPS
0.9 seconds for 180 frames = 209.3 FPS
0.9 seconds for 180 frames = 209.3 FPS
0.8 seconds for 180 frames = 211.8 FPS

suggestion: make the spin a bit slower, its kinda annoying watching it go by really fast =P

---

### Post by GenPFault on 2009-04-10
ASUS EeePC 1000, 2GB RAM, Ubuntu 8.10 with the Array.org kernel.

```

GL_VENDOR   : Tungsten Graphics, Inc
GL_RENDERER : Mesa DRI Intel(R) 945GME 20061102 x86/MMX/SSE2
GL_VERSION  : 1.4 Mesa 7.2

```

No Compiz:
```

43.9 seconds for 180 frames = 4.1 FPS

```

Compiz:
```

46.6 seconds for 180 frames = 3.9 FPS

```

---

### Post by taavikko on 2009-04-10
Tested on KDE with kwin effects on,

Rest of hardware is 
"I7@920, ASUS P6T dlx V2, 6GB DDR3-1066"

```
GL_VENDOR   : NVIDIA Corporation                                                                                 
GL_RENDERER : GeForce 9800 GTX/9800 GTX+/PCI/SSE2                                                                
GL_VERSION  : 3.0.0 NVIDIA 180.44                                                                                

0.7 seconds for 180 frames = 250.0 FPS
0.6 seconds for 180 frames = 290.3 FPS
0.6 seconds for 180 frames = 285.7 FPS
0.6 seconds for 180 frames = 295.1 FPS
0.6 seconds for 180 frames = 295.1 FPS
0.6 seconds for 180 frames = 290.3 FPS
0.6 seconds for 180 frames = 290.3 FPS
0.6 seconds for 180 frames = 290.3 FPS
0.6 seconds for 180 frames = 295.1 FPS
0.6 seconds for 180 frames = 295.1 FPS
```

As for "glxgears" got
```
glxgears     
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/113353 the monitor refresh rate.                      
43581 frames in 5.0 seconds = 8715.230 FPS                            
41796 frames in 5.0 seconds = 8359.180 FPS                            
44319 frames in 5.0 seconds = 8863.684 FPS                            
43674 frames in 5.0 seconds = 8734.700 FPS                            
43708 frames in 5.0 seconds = 8741.440 FPS                            
44632 frames in 5.0 seconds = 8926.335 FPS
```

---

