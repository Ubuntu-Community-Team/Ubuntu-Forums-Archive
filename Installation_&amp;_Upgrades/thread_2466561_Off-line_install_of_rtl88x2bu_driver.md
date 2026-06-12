---
title: "Off-line install of rtl88x2bu driver"
date: 2021-08-30
forum: Installation &amp; Upgrades
---

### Post by terraclast on 2021-08-30
I just upgraded to the 5.11.0.27 kernal and am having a first go at an offline install of a driver install for a bros trend AC3 WIFI adapter.  
I have the driver, I think. I have it mounted on a USB.  I have these instructions:
```

cd rtl88x2bu
VER=$(sed -n 's/\PACKAGE_VERSION="\(.*\)"/\1/p' dkms.conf)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu

```

And when I run it I get the following errors:
```

/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c: In function ‘isFileReadable’:
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2231:11: error: implicit declaration of function ‘get_fs’; did you mean ‘get_sa’? [-Werror=implicit-function-declaration]
 2231 |   oldfs = get_fs();
      |           ^~~~~~
      |           get_sa
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2231:11: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’
  CC [M]  /var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/linux/usb_intf.o
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2233:3: error: implicit declaration of function ‘set_fs’; did you mean ‘sget_fc’? [-Werror=implicit-function-declaration]
 2233 |   set_fs(KERNEL_DS);
      |   ^~~~~~
      |   sget_fc
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2233:10: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2233 |   set_fs(KERNEL_DS);
      |          ^~~~~~~~~
      |          KERNFS_NS
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2233:10: note: each undeclared identifier is reported only once for each function it appears in
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c: In function ‘retriveFromFile’:
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2273:12: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’
 2273 |    oldfs = get_fs();
      |            ^~~~~~
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2275:11: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2275 |    set_fs(KERNEL_DS);
      |           ^~~~~~~~~
      |           KERNFS_NS
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c: In function ‘storeToFile’:
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2312:12: error: incompatible types when assigning to type ‘mm_segment_t’ {aka ‘struct <anonymous>’} from type ‘int’
 2312 |    oldfs = get_fs();
      |            ^~~~~~
/var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.c:2314:11: error: ‘KERNEL_DS’ undeclared (first use in this function); did you mean ‘KERNFS_NS’?
 2314 |    set_fs(KERNEL_DS);
      |           ^~~~~~~~~
      |           KERNFS_NS
cc1: some warnings being treated as errors
make[2]: *** [scripts/Makefile.build:287: /var/lib/dkms/rtl88x2bu/5.8.7.4/build/os_dep/osdep_service.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:1848: /var/lib/dkms/rtl88x2bu/5.8.7.4/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.11.0-27-generic'
make: *** [Makefile:2425: modules] Error 2

```

I don't understand why the build is failing aside from the wrong variable is being used.  I also don't know how to solve the problem after searching the interwebs a fair amount, hence my post.  
Any help would be immensely appreciated.  

Thanks

---

