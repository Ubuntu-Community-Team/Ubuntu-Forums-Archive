---
title: "Can't install VMWare Workstation 7 on 10.04"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by CRCarl on 2010-04-02
Attempting to install Workstation 7 on Lucid (2.6.32-19-generic) fully patched as of today (4/2/2010). 

Output from installer - 

```
auser@alaptop:~/Downloads$ sudo ./VMware-Workstation-Full-7.0.1-227600.i386.bundle 
Extracting VMware Installer...done.
*** glibc detected *** /tmp/vmis.E6cNz1/install/vmware-installer/vmis-launcher: double free or corruption (out): 0xb6148008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b581)[0x9ab581]
/lib/tls/i686/cmov/libc.so.6(+0x6cdd8)[0x9acdd8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0x9afebd]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Free+0x5c)[0x7eb41c]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x6353c)[0x7f253c]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x55049)[0x7e4049]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyDict_SetItem+0x7e)[0x7e605e]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x2b290)[0x7ba290]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_SetAttr+0xaf)[0x7e949f]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x1edb)[0x8314ab]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x44eb0)[0x7d3eb0]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x2ac32)[0x7b9c32]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_CallObjectWithKeywords+0x7b)[0x82e8cb]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x2c8b3)[0x7bb8b3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0xa1e)[0x82ffee]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x3b9ff)[0x7ca9ff]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0xa1e)[0x82ffee]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x44eb0)[0x7d3eb0]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x2ac32)[0x7b9c32]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/lib/lib-dynload/_functools.so(+0xe1d)[0xed3e1d]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x1383)[0x830953]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0x8346b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x44f87)[0x7d3f87]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x3ea0)[0x833470]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x62f8)[0x8358c8]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0x8366e3]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x44eb0)[0x7d3eb0]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0x2ac32)[0x7b9c32]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0x7b24b7]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(PyEval_CallObjectWithKeywords+0x7b)[0x82e8cb]
/tmp/vmis.E6cNz1/install/vmware-installer/python/libpython.so(+0xd54f4)[0x8644f4]
/lib/tls/i686/cmov/libpthread.so.0(+0x596e)[0xb5796e]
/lib/tls/i686/cmov/libc.so.6(clone+0x5e)[0xa0d9de]
======= Memory map: ========
00110000-00111000 r-xp 00000000 00:00 0          [vdso]
00111000-00124000 r-xp 00000000 08:01 9175149    /lib/tls/i686/cmov/libnsl-2.11.1.so
00124000-00125000 r--p 00012000 08:01 9175149    /lib/tls/i686/cmov/libnsl-2.11.1.so
00125000-00126000 rw-p 00013000 08:01 9175149    /lib/tls/i686/cmov/libnsl-2.11.1.so
00126000-00128000 rw-p 00000000 00:00 0 
00128000-0014c000 r-xp 00000000 08:01 9175138    /lib/tls/i686/cmov/libm-2.11.1.so
0014c000-0014d000 r--p 00023000 08:01 9175138    /lib/tls/i686/cmov/libm-2.11.1.so
0014d000-0014e000 rw-p 00024000 08:01 9175138    /lib/tls/i686/cmov/libm-2.11.1.so
0014e000-00153000 r-xp 00000000 08:01 4591575    /tmp/vmis.E6cNz1/install/vmware-installer/python/lib/lib-dynload/operator.so
00153000-00154000 rw-p 00005000 08:01 4591575    /tmp/vmis.E6cNz1/install/vmware-installer/python/lib/lib-dynload/operator.so
00154000-00157000 r-xp 00000000 08:01 4591566    /tmp/vmis.E6cNz1/install/vmware-installer/python/lib/lib-dynload/cStringIO.so
00157000-00158000 rw-p 00003000 08:01 4591566    /tmp/vmis.E6cNz1/install/vmware-installer/python/lib/lib-dynload/cStringIO.so
00159000-00174000 r-xp 00000000 08:01 9175054    /lib/ld-2.11.1.so
00174000-00175000 r--p 0001a000 08:01 9175054    /lib/ld-2.11.1.so
00175000-00176000 rw-p 0001b000 08:01 9175054    /lib/ld-2.11.1.so
00176000-00255000 r-xp 00000000 08:01 4597948    /tmp/vmis.E6cNz1/install/vmware-installer/sopython/libpy25.so
00255000-0026b000 rw-p 000df000 08:01 4597948    /tmp/vmis.E6cNz1/install/vmware-installer/sopython/libpy25.so
0026b000-00273000 rw-p 00000000 00:00 0 /tmp/vmis.E6cNz1/install/vmware-installer/vmware-installer: line 22: 27633 Aborted                 (core dumped) VMWARE_INSTALLER="$VMWARE_INSTALLER" VMISPYVERSION="$VMISPYVERSION" "$VMWARE_INSTALLER"/vmis-launcher "$VMWARE_INSTALLER"/vmware-installer.py "$@"

```

Ideas?

---

### Post by jou770d on 2010-04-02
That's weird! I've just finished successfully installing the Workstation 7.0.1 (release 227600) x86 full bundle.
I've also chosen the eclipse debug options (which failed as I stupidly forgotten to preconfigure eclipse).

I'm running as well a fully updated/upgraded lucid.

---

### Post by aLiEnTxC on 2010-04-12
Im got the same problem, also on the extraction:

```
user@nb:/pool/Downloads/vmware/VMware 7 Workstation$ ./VMware-Workstation-Full-7.0.1-227600.i386.bundle --extract=vmware
Extracting VMware Installer...done.
*** glibc detected *** /tmp/vmis.rjoUec/install/vmware-installer/vmis-launcher: double free or corruption (out): 0xb5f05008 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(+0x6b581)[0xb77c5581]
/lib/tls/i686/cmov/libc.so.6(+0x6cdd8)[0xb77c6dd8]
/lib/tls/i686/cmov/libc.so.6(cfree+0x6d)[0xb77c9ebd]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyObject_Free+0x5c)[0xb764241c]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x6353c)[0xb764953c]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x55049)[0xb763b049]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyDict_SetItem+0x7e)[0xb763d05e]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x2b290)[0xb7611290]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyObject_SetAttr+0xaf)[0xb764049f]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x1edb)[0xb76884ab]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x44eb0)[0xb762aeb0]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xb76094b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x2ac32)[0xb7610c32]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyObject_Call+0x37)[0xb76094b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_CallObjectWithKeywords+0x7b)[0xb76858cb]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(+0x2c8b3)[0xb76128b3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0xa1e)[0xb7686fee]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x50e7)[0xb768b6b7]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalFrameEx+0x62f8)[0xb768c8c8]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCodeEx+0x793)[0xb768d6e3]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyEval_EvalCode+0x55)[0xb768d755]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyRun_FileExFlags+0xb4)[0xb76af7e4]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyRun_SimpleFileExFlags+0x1a6)[0xb76afad6]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(PyRun_AnyFileExFlags+0x7a)[0xb76afdba]
/tmp/vmis.rjoUec/install/vmware-installer/python/libpython.so(Py_Main+0xa24)[0xb76b9204]
/tmp/vmis.rjoUec/install/vmware-installer/sopython/libpy25.so(RunInstaller+0xed)[0xb74d062d]
/tmp/vmis.rjoUec/install/vmware-installer/vmis-launcher[0x804fb56]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0xb7770bd6]
/tmp/vmis.rjoUec/install/vmware-installer/vmis-launcher[0x804f631]
======= Memory map: ========
08048000-080f1000 r-xp 00000000 08:03 918431     /tmp/vmis.rjoUec/install/vmware-installer/vmis-launcher
080f1000-08104000 rw-p 000a8000 08:03 918431     /tmp/vmis.rjoUec/install/vmware-installer/vmis-launcher
08104000-0810c000 rw-p 00000000 00:00 0 
09e69000-0a7fb000 rw-p 00000000 00:00 0          [heap]
b5d00000-b5d21000 rw-p 00000000 00:00 0 
b5d21000-b5e00000 ---p 00000000 00:00 0 
b5e2d000-b5e4a000 r-xp 00000000 08:03 2228307    /lib/libgcc_s.so.1
b5e4a000-b5e4b000 r--p 0001c000 08:03 2228307    /lib/libgcc_s.so.1
b5e4b000-b5e4c000 rw-p 0001d000 08:03 2228307    /lib/libgcc_s.so.1
b5e5e000-b5ff0000 rw-p 00000000 00:00 0 
b5ff0000-b6016000 r-xp 00000000 08:03 1186787    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6016000-b6017000 r--p 00025000 08:03 1186787    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6017000-b6018000 rw-p 00026000 08:03 1186787    /usr/lib/gtk-2.0/2.10.0/engines/libmurrine.so
b6018000-b601f000 r-xp 00000000 08:03 1183149    /usr/lib/libltdl.so.7.2.1
b601f000-b6020000 r--p 00006000 08:03 1183149    /usr/lib/libltdl.so.7.2.1
b6020000-b6021000 rw-p 00007000 08:03 1183149    /usr/lib/libltdl.so.7.2.1
b6021000-b602e000 r-xp 00000000 08:03 1183417    /usr/lib/libtdb.so.1.2.0
b602e000-b602f000 r--p 0000c000 08:03 1183417    /usr/lib/libtdb.so.1.2.0
b602f000-b6030000 rw-p 0000d000 08:03 1183417    /usr/lib/libtdb.so.1.2.0
b6030000-b6035000 r-xp 00000000 08:03 1183232    /usr/lib/libogg.so.0.6.0
b6035000-b6036000 r--p 00004000 08:03 1183232    /usr/lib/libogg.so.0.6.0
b6036000-b6037000 rw-p 00005000 08:03 1183232    /usr/lib/libogg.so.0.6.0
b6037000-b605e000 r-xp 00000000 08:03 1183468    /usr/lib/libvorbis.so.0.4.3
b605e000-b605f000 r--p 00026000 08:03 1183468    /usr/lib/libvorbis.so.0.4.3
b605f000-b6060000 rw-p 00027000 08:03 1183468    /usr/lib/libvorbis.so.0.4.3
b6060000-b6067000 r-xp 00000000 08:03 1183472    /usr/lib/libvorbisfile.so.3.3.2
b6067000-b6068000 r--p 00006000 08:03 1183472    /usr/lib/libvorbisfile.so.3.3.2
b6068000-b6069000 rw-p 00007000 08:03 1183472    /usr/lib/libvorbisfile.so.3.3.2
b6069000-b6077000 r-xp 00000000 08:03 1182651    /usr/lib/libcanberra.so.0.2.1
b6077000-b6078000 r--p 0000d000 08:03 1182651    /usr/lib/libcanberra.so.0.2.1
b6078000-b6079000 rw-p 0000e000 08:03 1182651    /usr/lib/libcanberra.so.0.2.1
b6079000-b607c000 r-xp 00000000 08:03 1182649    /usr/lib/libcanberra-gtk.so.0.1.5
b607c000-b607d000 r--p 00003000 08:03 1182649    /usr/lib/libcanberra-gtk.so.0.1.5
b607d000-b607e000 rw-p 00004000 08:03 1182649    /usr/lib/libcanberra-gtk.so.0.1.5
b608a000-b608c000 r-xp 00000000 08:03 917827     /tmp/vmis.rjoUec/install/vmware-installer/python/lib/lib-dynload/_random.so
b608c000-b608d000 rw-p 00002000 08:03 917827     /tmp/vmis.rjoUec/install/vmware-installer/python/lib/lib-dynload/_random.so
b608d000-b608f000 r-xp 00000000 08:03 917826     /tmp/vmis.rjoUec/install/vmware-installer/python/lib/lib-dynload/math.so
b608f000-b6090000 rw-p 00002000 08:03 917826     /tmp/vmis.rjoUec/install/vmware-installer/python/lib/lib-dynload/math.so
b6090000-b6094000 r-xp 00000000 08:03 1186833    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6094000-b6095000 ---p 00004000 08:03 1186833    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6095000-b6096000 r--p 00004000 08:03 1186833    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6096000-b6097000 rw-p 00005000 08:03 1186833    /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
b6097000-b60c0000 r--p 00000000 08:03 1453875    /usr/share/locale-langpack/de/LC_MESSAGES/gtk20-properties.mo
b60c0000-b60d4000 r--p 00000000 08:03 1453929    /usr/share/locale-langpack/de/LC_MESSAGES/gtk20.mo
b60d4000-b61f2000 r--p 00000000 08:03 1190146    /usr/lib/locale/de_DE.utf8/LC_COLLATE
b61f2000-b61f5000 r-xp 00000000 08:03 917708     /tmp/vmis.rjoUec/install/vmware-installer/python/pygtk/pangocairo.so
b61f5000-b61f6000 rw-p 00002000 08:03 917708     /tmp/vmis.rjoUec/install/vmware-installer/python/pygtk/pangocairo.so
b61f6000-b63a1000 r-xp 00000000 08:03 917700     /tmp/vmis.rjoUec/install/vmware-installer/python/pygtk/gtk/_gtk.so
b63a1000-b63c6000 rw-p 001ab000 08:03 917700     /tmp/vmis.rjoUec/install/vmware-installer/python/pygtk/gtk/_gtk.so
b63c6000-b63e3000 r-xp 00000000 08:03 918236     /tmp/vmis.rjoUec/install/vmware-installer/lib/lib/libexpat.so.0/libexpat.so.0
b63e3000-b63e5000 rw-p 0001d000 08:03 918236     /tmp/vmis.rjoUec/install/vmware-installer/lib/lib/libexpat.so.0/libexpat.so.0
b63e5000-b67b2000 r-xp 00000000 08:03 1187318    /usr/lib/libgtk-x11-2.0.so.0.2000.0
b67b2000-b67b6000 r--p 003cd000 08:03 1187318    /usr/lib/libgtk-x11-2.0.so.0.2000.0
b67b6000-b67b8000 rw-p 003d1000 08:03 1187318    /usr/lib/libgtk-x11-2.0.so.0.2000.0
b67b8000-b67ba000 rw-p 00000000 00:00 0 
b67ba000-b67d3000 r-xp 00000000 08:03 1182594    /usr/lib/libatk-1.0.so.0.3009.1
b67d3000-b67d4000 ---p 00019000 08:03 1182594    /usr/lib/libatk-1.0.so.0.3009.1
b67d4000-b67d5000 r--p 00019000 08:03 1182594    /usr/lib/libatk-1.0.so.0.3009.1
b67d5000-b67d6000 rw-p 0001a000 08:03 1182594    /usr/lib/libatk-1.0.so.0.3009.1
b67d6000-b67d8000 r-xp 00000000 08:03 1182517    /usr/lib/libXdamage.so.1.1.0
b67d8000-b67d9000 r--p 00001000 08:03 1182517    /usr/lib/libXdamage.so.1.1.0/tmp/vmis.rjoUec/install/vmware-installer/vmware-installer: Zeile 22: 19907 Aborted                 (Speicherabzug geschrieben) VMWARE_INSTALLER="$VMWARE_INSTALLER" VMISPYVERSION="$VMISPYVERSION" "$VMWARE_INSTALLER"/vmis-launcher "$VMWARE_INSTALLER"/vmware-installer.py "$@"
user@nb:/pool/Downloads/vmware/VMware 7 Workstation$
```

---

### Post by jrider on 2010-04-12
I installed VMware-Workstation-7.0.0-203739_x86_64 on Ubuntu 10.4 beta 2. I cant run it as it says several modules must be compiled and loaded into the running kernel. It fails to load from there. The logs from  /tmp/vmare-root/setup-2461.log says 

```
Apr 12 16:20:15.075: app-140172318439168| Log for VMware Workstation pid=3461 version=7.0.0 build=build-203739 option=Release
Apr 12 16:20:15.075: app-140172318439168| The process is 64-bit.
Apr 12 16:20:15.075: app-140172318439168| Host codepage=UTF-8 encoding=UTF-8
Apr 12 16:20:15.075: app-140172318439168| Logging to /tmp/vmware-root/setup-3461.log
Apr 12 16:20:15.304: app-140172318439168| modconf query interface initialized
Apr 12 16:20:15.304: app-140172318439168| modconf library initialized
Apr 12 16:20:15.338: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.346: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.358: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.375: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.389: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.425: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.428: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.431: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.433: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.436: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.456: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.458: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.461: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.464: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.466: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.473: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.485: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.527: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.530: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.532: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.535: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.538: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.544: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.557: app-140172318439168| Your GCC version: 4.4
Apr 12 16:20:15.621: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.625: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.627: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.630: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:15.633: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:16.201: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:16.201: app-140172318439168| Building module vmmon.
Apr 12 16:20:16.208: app-140172318439168| Extracting the sources of the vmmon module.
Apr 12 16:20:16.294: app-140172318439168| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-19-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Apr 12 16:20:27.297: app-140172318439168| Installing module vmmon from /tmp/vmware-root/modules/vmmon.o.
Apr 12 16:20:27.336: app-140172318439168| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-19-generic/misc/vmmon.o
Apr 12 16:20:29.579: app-140172318439168| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-19-generic/misc/vmmon.ko
Apr 12 16:20:42.604: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:42.605: app-140172318439168| Building module vmnet.
Apr 12 16:20:42.605: app-140172318439168| Extracting the sources of the vmnet module.
Apr 12 16:20:42.670: app-140172318439168| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmnet-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-19-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Apr 12 16:20:50.550: app-140172318439168| Failed to compile module vmnet!
Apr 12 16:20:50.556: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:50.557: app-140172318439168| Building module vmblock.
Apr 12 16:20:50.557: app-140172318439168| Extracting the sources of the vmblock module.
Apr 12 16:20:50.657: app-140172318439168| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmblock-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-19-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Apr 12 16:20:56.048: app-140172318439168| Installing module vmblock from /tmp/vmware-root/modules/vmblock.o.
Apr 12 16:20:56.049: app-140172318439168| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-19-generic/misc/vmblock.o
Apr 12 16:20:56.811: app-140172318439168| Registering file: /usr/lib/vmware-installer/1.1/vmware-installer --register-file vmware-player-app regular /lib/modules/2.6.32-19-generic/misc/vmblock.ko
Apr 12 16:20:57.986: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:57.986: app-140172318439168| Building module vmci.
Apr 12 16:20:57.986: app-140172318439168| Extracting the sources of the vmci module.
Apr 12 16:20:58.033: app-140172318439168| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-19-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Apr 12 16:20:59.755: app-140172318439168| Failed to compile module vmci!
Apr 12 16:20:59.761: app-140172318439168| Trying to find a suitable PBM set for kernel 2.6.32-19-generic.
Apr 12 16:20:59.761: app-140172318439168| Building module vmci.
Apr 12 16:20:59.761: app-140172318439168| Extracting the sources of the vmci module.
Apr 12 16:20:59.777: app-140172318439168| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmci-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.32-19-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.3
Apr 12 16:21:01.100: app-140172318439168| Failed to compile module vmci!
```

---

### Post by mindcircus on 2010-04-13
Yes, I had the same problem with VMware-Workstation-7.0.0-203739_x86_64. Version 7.0.1 works fine.

---

### Post by jrider on 2010-04-15
Yeah I tried it too, 7.0.1 does work. Thanks.

---

