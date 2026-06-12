---
title: "Creating binary driver disk for uvcvideo"
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by prshah on 2010-04-24
Hello,

I need (for a friend) to create a "driver" disc for a webcam that is uvcvideo compatible. 

The webcam when plugged into my machine works out-of-the-box using the uvcvideo module.

However, for some reasons, we want to include a binary and/or sources file with it.

I have downloaded the source files from [http://linuxtv.org/hg/~pinchartl/uvcvideo/](http://linuxtv.org/hg/~pinchartl/uvcvideo/) , but compiling fails. (build-essential is installed). I did not compile it using sudo since I do not want to mess up what is already installed on my system. Compilation according to the enclosed INSTALL file is as simple as "make" (no ./configure).

However, make give me errors```

/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/et61x251_core.c: In function 'et61x251_ioctl_v4l2':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/et61x251_core.c:2500: warning: the frame size of 1256 bytes is larger than 1024 bytes
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/et61x251_tas5130d1b.o
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-avc.o
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-ci.o
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-dvb.o
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-fe.o
  CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.o
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:22:21: error: csr1212.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:23:23: error: highlevel.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:24:19: error: hosts.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:25:22: error: ieee1394.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:26:17: error: iso.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:27:21: error: nodemgr.h: No such file or directory
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:40: warning: 'struct hpsb_iso' declared inside parameter list
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:40: warning: its scope is only this definition or declaration, which is probably not what you want
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:56: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:57: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:64: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:65: error: implicit declaration of function 'dma_region_i'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:65: error: expected expression before 'unsigned'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:66: warning: assignment makes pointer from integer without a cast
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:67: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:71: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:85: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_of':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:90: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:90: warning: type defaults to 'int' in declaration of '__mptr'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:90: warning: initialization from incompatible pointer type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:90: error: invalid use of undefined type 'struct unit_directory'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_lock':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:95: error: 'quadlet_t' undeclared (first use in this function)
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:95: error: (Each undeclared identifier is reported only once
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:95: error: for each function it appears in.)
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:95: error: 'd' undeclared (first use in this function)
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:96: warning: ISO C90 forbids mixed declarations and code
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:98: error: implicit declaration of function 'hpsb_node_lock'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:99: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_read':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:107: error: implicit declaration of function 'hpsb_node_read'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_write':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:112: error: implicit declaration of function 'hpsb_node_write'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'start_iso':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:123: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:123: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:125: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:127: warning: assignment makes pointer from integer without a cast
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:134: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:137: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'stop_iso':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:148: error: implicit declaration of function 'hpsb_iso_stop'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: At top level:
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:163: warning: 'struct hpsb_host' declared inside parameter list
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'fcp_request':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:176: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_probe':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:191: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:191: warning: type defaults to 'int' in declaration of '__mptr'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:191: warning: initialization from incompatible pointer type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:191: error: invalid use of undefined type 'struct unit_directory'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:196: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:198: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:198: warning: assignment makes pointer from integer without a cast
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: At top level:
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:257: warning: 'struct unit_directory' declared inside parameter list
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'node_update':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:259: error: dereferencing pointer to incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: At top level:
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:267: error: variable 'fdtv_driver' has initializer but incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:268: error: unknown field 'name' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:268: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:268: warning: (near initialization for 'fdtv_driver')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:269: error: unknown field 'id_table' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:270: error: unknown field 'update' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:271: error: unknown field 'driver' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:271: error: extra brace group at end of initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:271: error: (near initialization for 'fdtv_driver')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:274: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:274: warning: (near initialization for 'fdtv_driver')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:277: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:278: error: unknown field 'name' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:278: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:278: warning: (near initialization for 'fdtv_highlevel')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:279: error: unknown field 'fcp_request' specified in initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:286: error: implicit declaration of function 'hpsb_register_highlevel'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_protocol'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:290: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:297: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.31-20-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l'
make: *** [all] Error 2
```


I was hoping that it will dump a .ko file that I can handover to my friend. I understand that this file will be tied to my current kernel architecture and headers.

I have also looked into apt-src -b but cannot find the source for uvcvideo.

I have also looked at dkms, but I get the error```
sudo dkms mkdriverdisk -m uvcvideo -k `uname -r` -d redhat -v `uname -r`

Error! DKMS tree does not contain: uvcvideo-2.6.31-20-generic
Build cannot continue without the proper tree.
```

My main issue is that the webcam is currently supported by uvcvideo, but there are many reports where uvcvideo has to be downloaded and compiled to get the webcam to work. If such an issue occurs, I do not know how to compile it successfully.

Can anyone advise me on how to successfully compile and produce a uvcvideo.ko kernel module? Failing that, I will just copy over the existing uvcvideo.ko modules and hand it over. ```
locate uvcvideo
/lib/modules/2.6.22-14-generic/ubuntu/media/usbvideo/uvcvideo.ko
/lib/modules/2.6.31-14-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
/lib/modules/2.6.31-15-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
/lib/modules/2.6.31-16-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
/lib/modules/2.6.31-17-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
/lib/modules/2.6.31-19-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/uvc/uvcvideo.ko
```

Any help/advice welcome and appreciated.

---

### Post by prshah on 2010-04-24
> **prshah said:**
>   CC [M]  /home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.o
/home/user/downloads/uvcvideo/uvcvideo-553dfd853cba/v4l/firedtv-1394.c:21:17: error: dma.h: No such file or directory

In typical Murphy's fashion, I [found the solution]("http://ubuntuforums.org/showthread.php?t=1337146") within 3 minutes of posting, notwithstanding 3 hours of Google-ing before posting.

However, I would still like pointers on how to use apt-src and/or dkms mkdriverdisk, if anyone would like to share their knowledge.

---

