---
title: "Eclipse C++ and Opencv"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by rafael14 on 2014-12-10
Hi all , 
       Im having trouble to compile OpenCv  example code using Eclipse C++ .
I added the include , the libs in compile linker and so on , but isnt recognizing the OpencvLibs   .
(reference link used to install it : [https://www.youtube.com/watch?v=m2pPlGkmjy8](https://www.youtube.com/watch?v=m2pPlGkmjy8) ) 

Follow the flags :

rafael@rafael-Dell-System-XPS-L502X:~/opencv-2.4.9/samples/c$ pkg-config opencv --libs
/usr/lib/x86_64-linux-gnu/libopencv_calib3d.so /usr/lib/x86_64-linux-gnu/libopencv_contrib.so /usr/lib/x86_64-linux-gnu/libopencv_core.so /usr/lib/x86_64-linux-gnu/libopencv_features2d.so /usr/lib/x86_64-linux-gnu/libopencv_flann.so /usr/lib/x86_64-linux-gnu/libopencv_gpu.so /usr/lib/x86_64-linux-gnu/libopencv_highgui.so /usr/lib/x86_64-linux-gnu/libopencv_imgproc.so /usr/lib/x86_64-linux-gnu/libopencv_legacy.so /usr/lib/x86_64-linux-gnu/libopencv_ml.so /usr/lib/x86_64-linux-gnu/libopencv_objdetect.so /usr/lib/x86_64-linux-gnu/libopencv_ocl.so /usr/lib/x86_64-linux-gnu/libopencv_photo.so /usr/lib/x86_64-linux-gnu/libopencv_stitching.so /usr/lib/x86_64-linux-gnu/libopencv_superres.so /usr/lib/x86_64-linux-gnu/libopencv_ts.so /usr/lib/x86_64-linux-gnu/libopencv_video.so /usr/lib/x86_64-linux-gnu/libopencv_videostab.so -lopencv_calib3d -lopencv_contrib -lopencv_core -lopencv_features2d -lopencv_flann -lopencv_gpu -lopencv_highgui -lopencv_imgproc -lopencv_legacy -lopencv_ml -lopencv_objdetect -lopencv_ocl -lopencv_photo -lopencv_stitching -lopencv_superres -lopencv_ts -lopencv_video -lopencv_videostab


       When I enter in samples of Opencv and compile with build_all.sh and run the program , its going ok ! The problem appears to be the configuration of Eclipse C++ .

       This is the build file in samples : 

#!/bin/sh

if [ $# -gt 0 ] ; then
    base=`basename $1 .c`
    echo "compiling $base"
    gcc -ggdb `pkg-config opencv --cflags --libs` $base.c -o $base
else
    for i in *.c; do
        echo "compiling $i"
        gcc -ggdb `pkg-config --cflags opencv` -o `basename $i .c` $i `pkg-config --libs opencv`;
    done
    for i in *.cpp; do
        echo "compiling $i"
        g++ -ggdb `pkg-config --cflags opencv` -o `basename $i .cpp` $i `pkg-config --libs opencv`;
    done
fi



      Someone can help me to fix this problem please ?

Thanks !

---

### Post by MAFoElffen on 2014-12-10
Does this help?
[http://docs.opencv.org/doc/tutorials/introduction/linux_eclipse/linux_eclipse.html](http://docs.opencv.org/doc/tutorials/introduction/linux_eclipse/linux_eclipse.html)

---

