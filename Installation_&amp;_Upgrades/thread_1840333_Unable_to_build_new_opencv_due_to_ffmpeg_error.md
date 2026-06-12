---
title: "Unable to build new opencv due to ffmpeg error"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by frondeur on 2011-09-07
Hi,

I am trying to compile OpenCV2.3.1 but highgui doesn't compile. The error is as following:
```
Linking CXX shared library ../../lib/libopencv_highgui.so
/usr/bin/ld: /usr/local/lib/libavcodec.a(kbdwin.o): relocation R_X86_64_32 against `.rodata' can not be used when making a shared object; recompile with -fPIC
/usr/local/lib/libavcodec.a: could not read symbols: Bad value
collect2: ld returned 1 exit status
make[2]: *** [lib/libopencv_highgui.so.2.3.1] Error 1
make[1]: *** [modules/highgui/CMakeFiles/opencv_highgui.dir/all] Error 2
make: *** [all] Error 2

```

 I think it is due to ffmpeg. I have tried to compile x264 and ffmpeg multiple times with --enable-static and --enable-pic but all in vain. Would anyone kindly help in this regard?

Thanks in Advance.

---

### Post by dino99 on 2011-09-07
ready to use into ppa: 

[https://launchpad.net/~gijzelaar/+archive/opencv2.3](https://launchpad.net/~gijzelaar/+archive/opencv2.3)

---

### Post by frondeur on 2011-09-09
Thanks dino,

i tried the ppa, but it returns the error while doing the sudo update.


W: Failed to fetch [http://ppa.launchpad.net/gijzelaar/opencv2.3/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/gijzelaar/opencv2.3/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/gijzelaar/opencv2.3/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gijzelaar/opencv2.3/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

