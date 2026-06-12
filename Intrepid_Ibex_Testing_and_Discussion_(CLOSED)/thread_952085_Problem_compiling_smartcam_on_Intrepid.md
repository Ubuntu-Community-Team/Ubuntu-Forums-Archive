---
title: "Problem compiling smartcam on Intrepid"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2008-10-18
Given that smartcam ( an application, which turns your mobile phone into a webcam - [https://sourceforge.net/projects/smartcam](https://sourceforge.net/projects/smartcam)) now works with Skype I tried to compile the required driver on Intrepid (it works fine on my Hardy installation) but I have the error below. I wonder if there is a problem with the app or I do not have some dev libraries installed?

```
test@neclaptop:~/Desktop/smartcam/src/driver$ make -C /lib/modules/2.6.27-7-generic/build M=`pwd` modules
make: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /home/test/Desktop/smartcam/src/driver/smartcam.o
/home/test/Desktop/smartcam/src/driver/smartcam.c: In function ‘smartcam_mmap’:
/home/test/Desktop/smartcam/src/driver/smartcam.c:194: error: implicit declaration of function ‘vmalloc_to_pfn’
/home/test/Desktop/smartcam/src/driver/smartcam.c:195: error: implicit declaration of function ‘remap_pfn_range’
/home/test/Desktop/smartcam/src/driver/smartcam.c:195: error: ‘PAGE_SHARED’ undeclared (first use in this function)
/home/test/Desktop/smartcam/src/driver/smartcam.c:195: error: (Each undeclared identifier is reported only once
/home/test/Desktop/smartcam/src/driver/smartcam.c:195: error: for each function it appears in.)
/home/test/Desktop/smartcam/src/driver/smartcam.c: At top level:
/home/test/Desktop/smartcam/src/driver/smartcam.c:559: error: ‘video_ioctl2’ undeclared here (not in a function)
/home/test/Desktop/smartcam/src/driver/smartcam.c:566: error: unknown field ‘type’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:572: error: unknown field ‘vidioc_querycap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:572: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:573: error: unknown field ‘vidioc_enum_fmt_cap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:573: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:574: error: unknown field ‘vidioc_g_fmt_cap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:574: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:574: error: initializer element is not computable at load time
/home/test/Desktop/smartcam/src/driver/smartcam.c:574: error: (near initialization for ‘smartcam_vid.tvnorms’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:575: error: unknown field ‘vidioc_try_fmt_cap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:575: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:575: error: initializer element is not computable at load time
/home/test/Desktop/smartcam/src/driver/smartcam.c:575: error: (near initialization for ‘smartcam_vid.current_norm’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:576: error: unknown field ‘vidioc_s_fmt_cap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:576: warning: initialization from incompatible pointer type
/home/test/Desktop/smartcam/src/driver/smartcam.c:577: error: unknown field ‘vidioc_reqbufs’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:577: warning: initialization from incompatible pointer type
/home/test/Desktop/smartcam/src/driver/smartcam.c:578: error: unknown field ‘vidioc_querybuf’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:579: error: unknown field ‘vidioc_qbuf’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:579: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:580: error: unknown field ‘vidioc_dqbuf’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:580: warning: missing braces around initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:580: warning: (near initialization for ‘smartcam_vid.lock’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:580: warning: initialization makes integer from pointer without a cast
/home/test/Desktop/smartcam/src/driver/smartcam.c:581: error: unknown field ‘vidioc_s_std’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:581: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:581: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:582: error: unknown field ‘vidioc_enum_input’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:582: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:582: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:583: error: unknown field ‘vidioc_g_input’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:583: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:583: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:584: error: unknown field ‘vidioc_s_input’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:584: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:584: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:585: error: unknown field ‘vidioc_queryctrl’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:585: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:585: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:586: error: unknown field ‘vidioc_g_ctrl’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:586: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:586: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:587: error: unknown field ‘vidioc_s_ctrl’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:587: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:587: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:588: error: unknown field ‘vidioc_cropcap’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:588: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:588: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:589: error: unknown field ‘vidioc_g_crop’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:589: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:589: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:590: error: unknown field ‘vidioc_s_crop’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:590: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:590: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:591: error: unknown field ‘vidioc_g_parm’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:591: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:591: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:592: error: unknown field ‘vidioc_s_parm’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:592: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:592: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:593: error: unknown field ‘vidioc_streamon’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:593: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:593: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:594: error: unknown field ‘vidioc_streamoff’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:594: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:594: warning: (near initialization for ‘smartcam_vid’)
/home/test/Desktop/smartcam/src/driver/smartcam.c:596: error: unknown field ‘vidiocgmbuf’ specified in initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:596: warning: excess elements in struct initializer
/home/test/Desktop/smartcam/src/driver/smartcam.c:596: warning: (near initialization for ‘smartcam_vid’)
make[1]: *** [/home/test/Desktop/smartcam/src/driver/smartcam.o] Error 1
make: *** [_module_/home/test/Desktop/smartcam/src/driver] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'

```

---

