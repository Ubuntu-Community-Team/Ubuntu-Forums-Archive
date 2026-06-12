---
title: "Error while installing OpenCV in Ubuntu 9.10"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by appusajeev on 2010-02-01
I am trying to install OpenCV on my kamic koala...
I downloaded OpenCV package from sourceforge

I did ./configure and it showed no errors

my when i try 'make install' , i get the following error


/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzeof'
/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzopen'
/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzclose'
/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzrewind'
/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzgets'
/home/appu/Downloads/OPencv/OpenCV-2.0.0/src/.libs/libcxcore.so: undefined reference to `gzputs'
collect2: ld returned 1 exit status
make[1]: *** [opencv-haartraining] Error 1
make[1]: Leaving directory `/home/appu/Downloads/OPencv/OpenCV-2.0.0/apps'
make: *** [install-recursive] Error 1


whats the cause of the error? Please help

---

### Post by zainmsud on 2010-03-10
This thread might be useful:

[http://n2.nabble.com/Compiling-error-with-OpenCV-2-0-0-td3968857.html](http://n2.nabble.com/Compiling-error-with-OpenCV-2-0-0-td3968857.html)

---

