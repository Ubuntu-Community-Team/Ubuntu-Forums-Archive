---
title: "building quake2 from source"
date: 2005-10-28
forum: Installation &amp; Upgrades
---

### Post by darth_vector on 2005-10-28
hi all, im trying to build quake2 from source but i'm getting a lot of errors. apparently it relies on SVGALib (not available anymore, but installed svgalib-bin), 3DFX fxmesa and some OpenGL libraries. Any help would be greatly appreciated!


mkdir: cannot create directory `debugi386-glibc': File exists
mkdir: cannot create directory `debugi386-glibc/client': File exists
mkdir: cannot create directory `debugi386-glibc/ded': File exists
mkdir: cannot create directory `debugi386-glibc/ref_soft': File exists
mkdir: cannot create directory `debugi386-glibc/ref_gl': File exists
mkdir: cannot create directory `debugi386-glibc/game': File exists
mkdir: cannot create directory `debugi386-glibc/ctf': File exists
make: [build_debug] Error 1 (ignored)
make targets BUILDDIR=debugi386-glibc CFLAGS="-Dstricmp=strcasecmp -g"
make[1]: Entering directory `/home/mlando/temp/quake2-3.21/linux'
gcc -Dstricmp=strcasecmp -g -fPIC -o debugi386-glibc/ref_soft/rw_svgalib.o -c ../linux/rw_svgalib.c
../linux/rw_svgalib.c:46:17: vga.h: No such file or directory
../linux/rw_svgalib.c:47:25: vgakeyboard.h: No such file or directory
../linux/rw_svgalib.c:48:22: vgamouse.h: No such file or directory
../linux/rw_svgalib.c:63: error: syntax error before '*' token
../linux/rw_svgalib.c:63: warning: data definition has no type or storage class
../linux/rw_svgalib.c: In function `VID_InitModes':
../linux/rw_svgalib.c:78: error: `vga_modeinfo' undeclared (first use in this function)
../linux/rw_svgalib.c:78: error: (Each undeclared identifier is reported only once
../linux/rw_svgalib.c:78: error: for each function it appears in.)
../linux/rw_svgalib.c:82: warning: passing arg 2 of `memcpy' makes pointer from integer without a cast
../linux/rw_svgalib.c:84: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:91: error: request for member `bytesperpixel' in something not a structure or union
../linux/rw_svgalib.c:91: error: request for member `colors' in something not a structure or union
../linux/rw_svgalib.c:92: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:96: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:97: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:97: error: request for member `height' in something not a structure or union
../linux/rw_svgalib.c: In function `get_mode':
../linux/rw_svgalib.c:123: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:124: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:124: error: request for member `height' in something not a structure or union
../linux/rw_svgalib.c: In function `SWimp_InitGraphics':
../linux/rw_svgalib.c:162: error: request for member `width' in something not a structure or union
../linux/rw_svgalib.c:163: error: request for member `height' in something not a structure or union
../linux/rw_svgalib.c:164: error: request for member `bytesperpixel' in something not a structure or union
../linux/rw_svgalib.c:165: error: request for member `linewidth' in something not a structure or union
../linux/rw_svgalib.c:167: error: request for member `linewidth' in something not a structure or union
../linux/rw_svgalib.c:170: error: request for member `linewidth' in something not a structure or union
../linux/rw_svgalib.c:171: error: request for member `linewidth' in something not a structure or union
../linux/rw_svgalib.c: In function `SWimp_Shutdown':
../linux/rw_svgalib.c:296: error: `TEXT' undeclared (first use in this function)
make[1]: *** [debugi386-glibc/ref_soft/rw_svgalib.o] Error 1
make[1]: Leaving directory `/home/mlando/temp/quake2-3.21/linux'
make: *** [build_debug] Error 2

---

