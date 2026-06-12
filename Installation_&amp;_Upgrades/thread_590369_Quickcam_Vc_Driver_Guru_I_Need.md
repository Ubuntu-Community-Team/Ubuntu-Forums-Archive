---
title: "Quickcam Vc Driver Guru I Need"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by crafted on 2007-10-24
pg@pg-desktop:~/Scrivania/qcamvc/linux_2.6$ make modules 
mkdir -p .tmp_versions 
cp /lib/modules/2.6.22-14-generic/build/.tmp_versions/*.mod /home/pg/Scrivania/qcamvc/linux_2.6/.tmp_versions 
cp: impossibile fare stat di `/lib/modules/2.6.22-14-generic/build/.tmp_versions/*.mod': Nessun file o directory 
make: [modules] Error 1 (ignored) 
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/pg/Scrivania/qcamvc/linux_2.6 MODVERDIR=/home/pg/Scrivania/qcamvc/linux_2.6/.tmp_versions modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic' 
CC [M] /home/pg/Scrivania/qcamvc/linux_2.6/qcamvc.o 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc.c: In function ‘qcamvc_vread’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc.c:1563: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘size_t’ 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc.c:1590: warning: format ‘%ld’ expects type ‘long int’, but argument 2 has type ‘size_t’ 
CC [M] /home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.o 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘__check_parport’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:87: warning: return from incompatible pointer type 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_ecp_read_block_dma’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:274: error: ‘const struct parport_pc_private’ has no member named ‘dev’ 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:380: error: ‘const struct parport_pc_private’ has no member named ‘dev’ 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_stream_start’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:456: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_stream_read’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:473: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:519: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_read’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:548: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_write’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:570: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_set_reg’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:592: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_get_reg’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:625: warning: ISO C90 forbids mixed declarations and code 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c: In function ‘qcamvc_pp_exit_module’: 
/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.c:875: warning: ISO C90 forbids mixed declarations and code 
make[2]: *** [/home/pg/Scrivania/qcamvc/linux_2.6/qcamvc_pp.o] Error 1 
make[1]: *** [_module_/home/pg/Scrivania/qcamvc/linux_2.6] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic' 
make: *** [modules] Error 2 
 
Hope hanyone can help me... thanx

---

### Post by crafted on 2007-10-25
:-(

---

