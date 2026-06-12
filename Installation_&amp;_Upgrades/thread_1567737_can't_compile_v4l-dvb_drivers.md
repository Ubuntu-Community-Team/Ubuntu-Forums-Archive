---
title: "can't compile v4l-dvb drivers"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by KutViZ on 2010-09-04
I've purchased a new hp laptop with a usb tv tuner. To use it i have to install v4l-dvb stuff, but installing doesn't want to work.

> 
root@gepzsir-laptop:/home/gepzsir/v4l-dvb# make
make -C /home/gepzsir/v4l-dvb/v4l 
make[1]: Entering directory `/home/gepzsir/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/gepzsir/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-24-generic/build
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/gepzsir/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/gepzsir/v4l-dvb/v4l/firedtv-1394.o
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:58: error: implicit declaration of function root@gepzsir-laptop:/home/gepzsir/v4l-dvb# make
make -C /home/gepzsir/v4l-dvb/v4l 
make[1]: Entering directory `/home/gepzsir/v4l-dvb/v4l'
creating symbolic links...
make -C firmware prep
make[2]: Entering directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make[2]: Leaving directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make -C firmware
make[2]: Entering directory `/home/gepzsir/v4l-dvb/v4l/firmware'
make[2]: Nothing to be done for `default'.
make[2]: Leaving directory `/home/gepzsir/v4l-dvb/v4l/firmware'
Kernel build directory is /lib/modules/2.6.32-24-generic/build
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/gepzsir/v4l-dvb/v4l  modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/gepzsir/v4l-dvb/v4l/firedtv-1394.o
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:22:17: error: dma.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:23:21: error: csr1212.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:24:23: error: highlevel.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:25:19: error: hosts.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:26:22: error: ieee1394.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:27:17: error: iso.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:28:21: error: nodemgr.h: No such file or directory
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:41: warning: 'struct hpsb_iso' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:41: warning: its scope is only this definition or declaration, which is probably not what you want
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'rawiso_activity_cb':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:57: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:58: error: implicit declaration of function 'hpsb_iso_n_ready'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/gepzsir/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/gepzsir/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gepzsir/v4l-dvb/v4l'
make: *** [all] Error 2
root@gepzsir-laptop:/home/gepzsir/v4l-dvb# 
'hpsb_iso_n_ready'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:65: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: implicit declaration of function 'dma_region_i'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:66: error: expected expression before 'unsigned'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:68: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:72: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:86: error: implicit declaration of function 'hpsb_iso_recv_release_packets'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_of':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: warning: type defaults to 'int' in declaration of '__mptr'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: warning: initialization from incompatible pointer type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:91: error: invalid use of undefined type 'struct unit_directory'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_lock':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: 'quadlet_t' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: (Each undeclared identifier is reported only once
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: for each function it appears in.)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:96: error: 'd' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:97: warning: ISO C90 forbids mixed declarations and code
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:99: error: implicit declaration of function 'hpsb_node_lock'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:100: error: 'EXTCODE_COMPARE_SWAP' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_read':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:108: error: implicit declaration of function 'hpsb_node_read'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_write':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:113: error: implicit declaration of function 'hpsb_node_write'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'start_iso':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:124: error: implicit declaration of function 'hpsb_iso_recv_init'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:124: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:126: error: 'HPSB_ISO_DMA_DEFAULT' undeclared (first use in this function)
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:135: error: implicit declaration of function 'hpsb_iso_recv_start'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:138: error: implicit declaration of function 'hpsb_iso_shutdown'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'stop_iso':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:149: error: implicit declaration of function 'hpsb_iso_stop'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:164: warning: 'struct hpsb_host' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fcp_request':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:177: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:178: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_probe':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: warning: type defaults to 'int' in declaration of '__mptr'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: warning: initialization from incompatible pointer type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:192: error: invalid use of undefined type 'struct unit_directory'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:197: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:198: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:199: error: implicit declaration of function 'CSR1212_TEXTUAL_DESCRIPTOR_LEAF_DATA'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:199: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:258: warning: 'struct unit_directory' declared inside parameter list
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'node_update':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:260: error: dereferencing pointer to incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: At top level:
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:268: error: variable 'fdtv_driver' has initializer but incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: error: unknown field 'name' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:269: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: error: unknown field 'id_table' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:270: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: error: unknown field 'update' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:271: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: unknown field 'driver' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: extra brace group at end of initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:272: error: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:275: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:275: warning: (near initialization for 'fdtv_driver')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:278: error: variable 'fdtv_highlevel' has initializer but incomplete type
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: error: unknown field 'name' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:279: warning: (near initialization for 'fdtv_highlevel')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: error: unknown field 'fcp_request' specified in initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: warning: excess elements in struct initializer
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:280: warning: (near initialization for 'fdtv_highlevel')
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_init':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:287: error: implicit declaration of function 'hpsb_register_highlevel'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:288: error: implicit declaration of function 'hpsb_register_protocol'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:291: error: implicit declaration of function 'hpsb_unregister_highlevel'
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c: In function 'fdtv_1394_exit':
/home/gepzsir/v4l-dvb/v4l/firedtv-1394.c:298: error: implicit declaration of function 'hpsb_unregister_protocol'
make[3]: *** [/home/gepzsir/v4l-dvb/v4l/firedtv-1394.o] Error 1
make[2]: *** [_module_/home/gepzsir/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/gepzsir/v4l-dvb/v4l'
make: *** [all] Error 2
root@gepzsir-laptop:/home/gepzsir/v4l-dvb# 


---

### Post by KutViZ on 2010-09-04
i've tried to do make in the v4l-dvb*/v4l directory. It does some but then the same error (make[2]: Error 2) comes up.

---

### Post by alroger on 2010-10-05
Ubuntu packaging bug.
Gotta disable firedtv compilation. Just edit v4l/.config and find CONFIG_DVB_FIREDTV=m and change to =n. Then run make again.

Why was this thread marked SOLVED without the answer?

---

### Post by n888 on 2010-10-15
thanks for that solution alroger - as to why it was marked SOLVED before your post is beyond me :guitar:

---

