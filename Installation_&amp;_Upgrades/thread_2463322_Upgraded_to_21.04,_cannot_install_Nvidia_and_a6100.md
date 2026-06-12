---
title: "Upgraded to 21.04, cannot install Nvidia and a6100 adapter"
date: 2021-06-08
forum: Installation &amp; Upgrades
---

### Post by notgoingbackto_ms on 2021-06-08
Hi, both were installed and working in 20.04, but all my attempts (with terminal commands) to install these now fail with errors on the install. I need some guidance on where to begin, I would like to get the a6100 working first. 

I just tried instructions from github, and the make errors are:

```
  CC [M]  /home/leary/src/rtl8812AU_8821AU_linux/core/rtw_odm.o 
  CC [M]  /home/leary/src/rtl8812AU_8821AU_linux/core/efuse/rtw_efuse.o 
  CC [M]  /home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.o 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c: In function &#8216;isFileReadable&#8217;: 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1951:11: error: implicit declaration of function &#8216;get_fs&#8217;; did you mean &#8216;get_ds&#8217;? [-Werror=implicit-function-declaration] 
 1951 |   oldfs = get_fs(); 
      |           ^~~~~~ 
      |           get_ds 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1951:11: error: incompatible types when assigning to type &#8216;mm_segment_t&#8217; from type &#8216;int&#8217; 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1952:3: error: implicit declaration of function &#8216;set_fs&#8217;; did you mean &#8216;sget_fc&#8217;? [-Werror=implicit-function-declaration] 
 1952 |   set_fs(get_ds()); 
      |   ^~~~~~ 
      |   sget_fc 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:37:19: error: &#8216;KERNEL_DS&#8217; undeclared (first use in this function); did you mean &#8216;KERNFS_NS&#8217;? 
   37 |  #define get_ds() KERNEL_DS 
      |                   ^~~~~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1952:10: note: in expansion of macro &#8216;get_ds&#8217; 
 1952 |   set_fs(get_ds()); 
      |          ^~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:37:19: note: each undeclared identifier is reported only once for each function it appears in 
   37 |  #define get_ds() KERNEL_DS 
      |                   ^~~~~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1952:10: note: in expansion of macro &#8216;get_ds&#8217; 
 1952 |   set_fs(get_ds()); 
      |          ^~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c: In function &#8216;retriveFromFile&#8217;: 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1980:12: error: incompatible types when assigning to type &#8216;mm_segment_t&#8217; from type &#8216;int&#8217; 
 1980 |    oldfs = get_fs(); 
      |            ^~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:37:19: error: &#8216;KERNEL_DS&#8217; undeclared (first use in this function); did you mean &#8216;KERNFS_NS&#8217;? 
   37 |  #define get_ds() KERNEL_DS 
      |                   ^~~~~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:1981:11: note: in expansion of macro &#8216;get_ds&#8217; 
 1981 |    set_fs(get_ds()); 
      |           ^~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c: In function &#8216;storeToFile&#8217;: 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:2015:12: error: incompatible types when assigning to type &#8216;mm_segment_t&#8217; from type &#8216;int&#8217; 
 2015 |    oldfs = get_fs(); 
      |            ^~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:37:19: error: &#8216;KERNEL_DS&#8217; undeclared (first use in this function); did you mean &#8216;KERNFS_NS&#8217;? 
   37 |  #define get_ds() KERNEL_DS 
      |                   ^~~~~~~~~ 
/home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.c:2016:11: note: in expansion of macro &#8216;get_ds&#8217; 
 2016 |    set_fs(get_ds()); 
      |           ^~~~~~ 
cc1: all warnings being treated as errors 
make[2]: *** [scripts/Makefile.build:287: /home/leary/src/rtl8812AU_8821AU_linux/os_dep/osdep_service.o] Error 1 
make[1]: *** [Makefile:1848: /home/leary/src/rtl8812AU_8821AU_linux] Error 2 
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-18-generic' 
make: *** [Makefile:1622: modules] Error 2 
leary@ubuntu-upstairs:~/src/rtl8812AU_8821AU_linux$  
```
 

Most all other instructions give the same errors above on the make.

Thanks

---

### Post by monkeybrain20122 on 2021-06-09
Probably because 21.04 use wayland as default. Try disable it and restart in X

See post #4 by the Fu [here]("https://ubuntuforums.org/showthread.php?t=2463154").

---

### Post by notgoingbackto_ms on 2021-06-10
Changed the setting to force xorg, but that had no effect, still cannot get the Netgear a6100 to work, must be something simple. Nvidia says it is being used, but no longer see the NVIDIA boot screens like in 20.04, so don't think that is installed properly.

---

### Post by monkeybrain20122 on 2021-06-12
What is the output for
```

nvidia-smi
```

I am on 20.04 and don't have the nvidia-splash screen either, but everything works.

---

### Post by monkeybrain20122 on 2021-06-13
sorry wrong thread. post deleted.

---

