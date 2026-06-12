---
title: "Errors when installing ARToolKit"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by Ephemeral on 2008-09-09
Hello hello =)

I'm trying to install ARToolKit, to be able to use my Eyetoy camera.
The ./Configure goes fine, but the make gives me an error :

```
eternal@eternal-desktop:~/ARToolKit$ make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/eternal/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/eternal/ARToolKit/lib/SRC/AR'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eternal/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/eternal/ARToolKit/lib/SRC/ARMulti'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eternal/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/eternal/ARToolKit/lib/SRC/Gl'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eternal/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/eternal/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -DUSE_EYETOY -g -I../../../include ccvt_i386.S
ccvt_i386.S:32:27: error: linux/linkage.h: No such file or directory
make[2]: *** [../../libARvideo.a(ccvt_i386.o)] Error 1
make[2]: Leaving directory `/home/eternal/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/eternal/ARToolKit/lib/SRC'
make: *** [all] Error 2

```

Any ideas?

Cheers,
Mark

---

### Post by Ephemeral on 2008-09-10
Bump**

---

### Post by Ephemeral on 2008-09-11
BUMP**

Does nobody know?

---

### Post by smallcamel on 2008-09-17
maybe you haven't install the openGL and GLUT in a right way.
try the following command:

sudo apt-get install mesa-common-dev mesademos libgl1-mesa-dev libglu1-mesa-dev freeglut3-dev

---

### Post by junglejuice on 2008-09-18
yes would be really interesting to know if any one has any suggestions to this problem as i seem to have the same issue as Ephemeral. have you found a solution to this compiling of ArtToolKit Ephemeral?
i am using ubuntu 8.04, with both Kdm and Gdm.
worth noting, however, that instead of using the eye toy camera option i have chosen video for linux. everything works fine when i run ./Configure this is the output,
```
lyndon@lyndon-desktop:~/Documents/theLoveShow/art/ARToolKit$ ./Configure
Select a video capture driver.
  1: Video4Linux
  2: Video4Linux+JPEG Decompression (EyeToy)
  3: Digital Video Camcoder through IEEE 1394 (DV Format)
  4: Digital Video Camera through IEEE 1394 (VGA NONCOMPRESSED Image Format)
  5: GStreamer Media Framework
Enter : 1

Color conversion should use x86 assembly (choose 'n' for 64bit systems)?
Enter : y
Do you want to create debug symbols? (y or n)
Enter : y
Build gsub libraries with texture rectangle support? (y or n)
GL_NV_texture_rectangle is supported on most NVidia graphics cards
and on ATi Radeon and better graphics cards
Enter : y
  create ./Makefile
  create lib/SRC/Makefile
  create lib/SRC/AR/Makefile
  create lib/SRC/ARMulti/Makefile
  create lib/SRC/Gl/Makefile
  create lib/SRC/VideoLinux1394Cam/Makefile
  create lib/SRC/VideoLinuxDV/Makefile
  create lib/SRC/VideoLinuxV4L/Makefile
  create lib/SRC/VideoSGI/Makefile
  create lib/SRC/VideoMacOSX/Makefile
  create lib/SRC/VideoGStreamer/Makefile
  create lib/SRC/ARvrml/Makefile
  create util/Makefile
  create util/calib_camera2/Makefile
  create util/calib_cparam/Makefile
  create util/calib_distortion/Makefile
  create util/mk_patt/Makefile
  create util/graphicsTest/Makefile
  create util/videoTest/Makefile
  create examples/Makefile
  create examples/collide/Makefile
  create examples/exview/Makefile
  create examples/loadMultiple/Makefile
  create examples/modeTest/Makefile
  create examples/multi/Makefile
  create examples/optical/Makefile
  create examples/paddle/Makefile
  create examples/paddleDemo/Makefile
  create examples/paddleInteraction/Makefile
  create examples/range/Makefile
  create examples/relation/Makefile
  create examples/simple/Makefile
  create examples/simple2/Makefile
  create examples/simpleLite/Makefile
  create examples/twoView/Makefile
  create examples/simpleVRML/Makefile
  create include/AR/config.h
Done.

```
then when i try ```
make
``` or ```
sudo make
``` 
this is what i get 
```
lyndon@lyndon-desktop:~/Documents/theLoveShow/art/ARToolKit$ sudo make
(cd lib/SRC;    make -f Makefile)
make[1]: Entering directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC'
(cd AR;         make -f Makefile)
make[2]: Entering directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/AR'
cc -c -O -I/usr/X11R6/include -g -I../../../include mAlloc.c
ar rs ../../libAR.a mAlloc.o
rm -f mAlloc.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mFree.c
ar rs ../../libAR.a mFree.o
rm -f mFree.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mAllocDup.c
ar rs ../../libAR.a mAllocDup.o
rm -f mAllocDup.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mDup.c
ar rs ../../libAR.a mDup.o
rm -f mDup.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mAllocTrans.c
ar rs ../../libAR.a mAllocTrans.o
rm -f mAllocTrans.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mTrans.c
ar rs ../../libAR.a mTrans.o
rm -f mTrans.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mAllocMul.c
ar rs ../../libAR.a mAllocMul.o
rm -f mAllocMul.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mMul.c
ar rs ../../libAR.a mMul.o
rm -f mMul.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mAllocInv.c
ar rs ../../libAR.a mAllocInv.o
rm -f mAllocInv.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mInv.c
ar rs ../../libAR.a mInv.o
rm -f mInv.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mSelfInv.c
ar rs ../../libAR.a mSelfInv.o
rm -f mSelfInv.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mAllocUnit.c
ar rs ../../libAR.a mAllocUnit.o
rm -f mAllocUnit.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mUnit.c
ar rs ../../libAR.a mUnit.o
rm -f mUnit.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mDisp.c
ar rs ../../libAR.a mDisp.o
rm -f mDisp.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mDet.c
ar rs ../../libAR.a mDet.o
rm -f mDet.o
cc -c -O -I/usr/X11R6/include -g -I../../../include mPCA.c
ar rs ../../libAR.a mPCA.o
rm -f mPCA.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vAlloc.c
ar rs ../../libAR.a vAlloc.o
rm -f vAlloc.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vDisp.c
ar rs ../../libAR.a vDisp.o
rm -f vDisp.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vFree.c
ar rs ../../libAR.a vFree.o
rm -f vFree.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vHouse.c
ar rs ../../libAR.a vHouse.o
rm -f vHouse.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vInnerP.c
ar rs ../../libAR.a vInnerP.o
rm -f vInnerP.o
cc -c -O -I/usr/X11R6/include -g -I../../../include vTridiag.c
ar rs ../../libAR.a vTridiag.o
rm -f vTridiag.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramGet.c
ar rs ../../libAR.a paramGet.o
rm -f paramGet.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramDecomp.c
ar rs ../../libAR.a paramDecomp.o
rm -f paramDecomp.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramDistortion.c
ar rs ../../libAR.a paramDistortion.o
rm -f paramDistortion.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramChangeSize.c
ar rs ../../libAR.a paramChangeSize.o
rm -f paramChangeSize.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramFile.c
ar rs ../../libAR.a paramFile.o
rm -f paramFile.o
cc -c -O -I/usr/X11R6/include -g -I../../../include paramDisp.c
ar rs ../../libAR.a paramDisp.o
rm -f paramDisp.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arDetectMarker.c
ar rs ../../libAR.a arDetectMarker.o
rm -f arDetectMarker.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetTransMat.c
ar rs ../../libAR.a arGetTransMat.o
rm -f arGetTransMat.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetTransMat2.c
ar rs ../../libAR.a arGetTransMat2.o
rm -f arGetTransMat2.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetTransMat3.c
ar rs ../../libAR.a arGetTransMat3.o
rm -f arGetTransMat3.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetTransMatCont.c
ar rs ../../libAR.a arGetTransMatCont.o
rm -f arGetTransMatCont.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arLabeling.c
ar rs ../../libAR.a arLabeling.o
rm -f arLabeling.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arDetectMarker2.c
ar rs ../../libAR.a arDetectMarker2.o
rm -f arDetectMarker2.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetMarkerInfo.c
ar rs ../../libAR.a arGetMarkerInfo.o
rm -f arGetMarkerInfo.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arGetCode.c
ar rs ../../libAR.a arGetCode.o
rm -f arGetCode.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arUtil.c
arUtil.c: In function ‘arGetVersion’:
arUtil.c:46: warning: incompatible implicit declaration of built-in function ‘exit’
ar rs ../../libAR.a arUtil.o
rm -f arUtil.o
make[2]: Leaving directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/AR'
(cd ARMulti;    make -f Makefile)
make[2]: Entering directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/ARMulti'
cc -c -O -I/usr/X11R6/include -g -I../../../include arMultiReadConfigFile.c
ar rs ../../libARMulti.a arMultiReadConfigFile.o
rm -f arMultiReadConfigFile.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arMultiGetTransMat.c
ar rs ../../libARMulti.a arMultiGetTransMat.o
rm -f arMultiGetTransMat.o
cc -c -O -I/usr/X11R6/include -g -I../../../include arMultiActivate.c
ar rs ../../libARMulti.a arMultiActivate.o
rm -f arMultiActivate.o
make[2]: Leaving directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/ARMulti'
(cd Gl;         make -f Makefile)
make[2]: Entering directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/Gl'
cc -c -O -I/usr/X11R6/include -g -I../../../include gsub.c
ar rs ../../libARgsub.a gsub.o
rm -f gsub.o
cc -c -O -I/usr/X11R6/include -g -I../../../include gsubUtil.c
ar rs ../../libARgsubUtil.a gsubUtil.o
rm -f gsubUtil.o
cc -c -O -I/usr/X11R6/include -g -I../../../include gsub_lite.c
gsub_lite.c: In function ‘arglCameraFrustum’:
gsub_lite.c:659: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
gsub_lite.c: In function ‘arglCameraFrustumRH’:
gsub_lite.c:718: warning: passing argument 1 of ‘arParamDecompMat’ from incompatible pointer type
ar rs ../../libARgsub_lite.a gsub_lite.o
rm -f gsub_lite.o
make[2]: Leaving directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/Gl'
(cd VideoLinuxV4L; make -f Makefile)
make[2]: Entering directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/VideoLinuxV4L'
cc -c -O -I/usr/X11R6/include -g -I../../../include ccvt_i386.S
ccvt_i386.S:32:27: error: linux/linkage.h: No such file or directory
make[2]: *** [../../libARvideo.a(ccvt_i386.o)] Error 1
make[2]: Leaving directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC/VideoLinuxV4L'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/lyndon/Documents/theLoveShow/art/ARToolKit/lib/SRC'
make: *** [all] Error 2

```
please could some one advise as i am uncertain of what to do next. i am also quite new to ubuntu so please be a clear as possible in your explanation :-)

---

### Post by tuga3d on 2009-01-04
choose no in the second question in the cofig phase, works for me.

but when i run the simpleTest my camera only displays noise :(

(maybe is my camera drivers)

---

### Post by LeBateleur on 2009-07-02
I have the same problem, I really need a solution, I don't wanna return to XP!

---

### Post by Okar on 2010-01-31
if you are on a 64bit system you should not user x86 assembly -> answer the question with no

---

