---
title: "[SOLVED] Compiling vloopback in Intrepid Ibex (8.10), is it possible?"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickballeux on 2008-10-17
Hi,

I am currently trying to compile the module vloopback (from the Flashcam project) under Ubuntu 8.10.

I am unable to compile the source since the kernel seems to have changed a bit.  Here is the output of vloopback error when compiling...

```

patrick@patrick-laptop:~/Download/flashcam-1.1/vloopback-1.1.2$ make
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/home/patrick/Download/flashcam-1.1/vloopback-1.1.2 modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.27-7-generic »
  CC [M]  /home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.o
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c: In function ‘fake_ioctl’:
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:317: error: implicit declaration of function ‘kill_proc’
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c: At top level:
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:967: error: ‘v4l_compat_ioctl32’ undeclared here (not in a function)
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:974: error: unknown field ‘owner’ specified in initializer
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:974: warning: initialization from incompatible pointer type
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:976: error: unknown field ‘type’ specified in initializer
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c: In function ‘create_pipe’:
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:1052: error: ‘struct video_device’ has no member named ‘type’
/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.c:1054: error: ‘struct video_device’ has no member named ‘type’
make[2]: *** [/home/patrick/Download/flashcam-1.1/vloopback-1.1.2/vloopback.o] Erreur 1
make[1]: *** [_module_/home/patrick/Download/flashcam-1.1/vloopback-1.1.2] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.27-7-generic »
make: *** [all] Erreur 2

```

I always was able to compile that source code with 8.04 and 7.10. The project is not maintaned anymore (I think)...


Any hint would be appreciated.

---

### Post by patrickballeux on 2008-10-19
Hi,

I will again answer my own query:  No!

The vloopback module cannot be compiled as it is (v1.1.2) with the kernel 2.6.27 since there seem to be a lot of changes in modules loading for v4l devices.

I modified the source code after doing a lot of research and a new version is available in the WebcamStudio for GNU/Linux project (v1.1.3).

Source code is in the svn repository and available as an archive in the "Libraries" package in the Download section of the project.

If you feel as checking/improving/testing the module, it would be appreciated.  I don't know much about module coding, so I modified the bare minimum in the source code to be able to compile it and use it.

WebcamStudio for GNU/Linux project: [http://webcamstudio.wiki.sourceforge.net]("http://webcamstudio.wiki.sourceforge.net")

---

